# Booking Micro Frontend

A React-based micro frontend for displaying Reports. 

## Tech Stack

- **Frontend Framework**: React 19.1.1 with TypeScript
- **UI Library**: Material-UI (MUI) v7.3.2 with Emotion styling
- **Build Tool**: Webpack 5 with Module Federation
- **Development Server**: Webpack Dev Server
- **Language**: TypeScript 4.9.5
- **Testing**: React Testing Library & Jest
- **Package Manager**: npm
- **State Management**: Redux


## Architecture

This micro frontend follows the **Module Federation** pattern, allowing it to be independently developed, deployed, and consumed by other applications in the micro frontend ecosystem.

### Key Architectural Components:

1. **Module Federation Setup**
   - Exposes `ReportDashboard` components
   - Runs on port 3003
   - Shared React dependencies to prevent duplication

2. **Component Structure**
   - `ReportDashboard`: To View Reports

3. **Integration Points**
   - Can be consumed by the host application (mf-host)
   - Communicates through shared state management

# Admin Access Control Implementation

## Overview
The reporting page is protected and only accessible to admin users. Here's how the system works:

## User Roles
- **User**: Regular users can access login, profile, and booking features
- **Admin**: Admin users have access to all features including the reporting dashboard

## How to Test Admin Access

### 1. Login as Admin
To login as an admin user, use an email that contains "admin" (case-insensitive):
- `admin@example.com` → Role: admin
- `admin.user@company.com` → Role: admin
- `superadmin@test.com` → Role: admin

### 2. Login as Regular User
Any other email will be assigned the "user" role:
- `john@example.com` → Role: user
- `jane.doe@company.com` → Role: user

### 3. Testing the Access Control

#### As Admin User:
1. Login with an admin email (e.g., `admin@example.com`)
2. You should see the "Reports" button in the navigation bar
3. Click on "Reports" - you should be able to access the reporting dashboard
4. Check your profile to see your role displayed as "admin"

#### As Regular User:
1. Login with a regular email (e.g., `user@example.com`)
2. You should NOT see the "Reports" button in the navigation bar
3. If you try to access `/reports` directly, you'll see an "Access Denied" message
4. Check your profile to see your role displayed as "user"