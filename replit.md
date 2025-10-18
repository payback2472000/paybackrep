# Payback247 - P2P Network Marketing MLM Dashboard

## Overview
Payback247 is a comprehensive full-stack P2P network marketing dashboard designed to implement a complete MLM (Multi-Level Marketing) system. It features payment verification, a binary tree structure, and a 5-level forced matrix. The project is production-ready and aims to provide a fair and transparent income distribution system through its unique Global FIFO Binary Queue and USDT unique amount verification system.

## User Preferences
I prefer iterative development with clear communication on progress. Ask before making major architectural changes or introducing new external dependencies. I appreciate detailed explanations for complex features. Ensure the codebase is clean and well-documented.

## System Architecture

### UI/UX Decisions
The system features a responsive design with a dark/light theme toggle, utilizing Shadcn/UI (Material Design 3 inspired) for components. The color palette includes a vibrant blue primary, with white and dark gray backgrounds. Typography uses Poppins and Inter fonts. Real-time WebSocket notifications provide immediate feedback on payment events and income updates.

### Technical Implementations
Payback247 is built with a React + TypeScript + Vite frontend, using Wouter for routing, TanStack Query v5 for state management, and Tailwind CSS for styling. The backend runs on Node.js with Express, using PostgreSQL (Neon) for the database, Drizzle as the ORM, and Replit Auth (OIDC) for user authentication. Session storage is managed with `connect-pg-simple`, and Replit Object Storage is used for payment proofs.

### Feature Specifications
- **Activation Fee Structure (₹5000 Total)**: Comprises Referral Payment (₹1000), Binary Payment (₹1000), 5 levels of Matrix Payments (₹500 each), and a System Fee (₹500). Each payment has a unique USDT amount with 5 decimal precision for verification.
- **Income Sources**: Sponsor/Referral Income, Binary Income (via FIFO queue), and Matrix Income.
- **Binary FIFO Queue System**: Ensures fair distribution of binary payments, where users are added to a global queue and payments go to the first person in line. When the queue is empty, binary payments are routed to admin accounts for manual confirmation.
- **Payment Workflow**: Users sign up with a referral link (https://payback247.com/?ref=USER_ID&pos=left/right), triggering the creation of 8 activation payment records. Users submit payment proofs (QR, Bank, UPI, USDT), which are then confirmed by receivers. USDT payments are auto-verified via BscScan API.
- **Admin Payment Confirmations**: When binary FIFO queue is empty, payments are assigned to admin accounts with `needsAdminConfirmation` flag set to true. Admins review and confirm these payments via the /admin/confirmations page, which updates payment status and creates admin income transactions.
- **System Fee Confirmations**: All system fee payments (₹500) are now assigned to admin accounts and require admin confirmation. Admins review and confirm these through the /admin/system-fees page, ensuring proper tracking and verification of all system fees collected.
- **Affiliate Links**: Referral links use the custom domain https://payback247.com as the base URL for professional branding. Format: https://payback247.com/?ref={userId}&pos={left|right}
- **Dual Authentication System**: Regular users authenticate via Replit Auth, while administrators use a separate email/password system.
- **Admin Panel**: Features user management, dispute resolution, system configuration (including payment timers), and analytics. Supports multiple admin accounts for system fee collection with random rotation.
- **Network Structure**: Implements a binary tree with left/right placement and a 5-level forced matrix.
- **Notifications**: Real-time WebSocket notifications for payment events and income updates.

### System Design Choices
- **Database Schema**: Extensive schema with over 12 tables including `users`, `payments`, `binary_tree`, `binary_queue`, `matrix_placements`, `transactions`, and `admin_accounts`. Payments table includes `adminAccountId` column to track payments assigned to admin accounts separately from user-to-user payments.
- **API Routes**: Comprehensive set of RESTful API endpoints for authentication, user operations, payment processing, network structure, transactions, and protected admin functionalities.
- **Security**: Session-based authentication with PostgreSQL storage, CSRF protection, input validation with Zod, SQL injection prevention via Drizzle ORM, and admin role-based access control.
- **Performance**: Utilizes React Query for data caching, optimistic UI updates, lazy loading, and database indexing.

## External Dependencies
- **Database**: PostgreSQL (via Neon)
- **Authentication**: Replit Auth (OIDC)
- **Blockchain Verification**: BscScan API (for USDT BEP-20)
- **Object Storage**: Replit Object Storage (for payment proofs)
- **Frontend Libraries**: React, TypeScript, Vite, Wouter, Shadcn/UI, TanStack Query, React Hook Form, Zod, Tailwind CSS
- **Backend Libraries**: Node.js, Express, Drizzle, `connect-pg-simple`, `bcryptjs`