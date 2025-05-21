# CodeTech Verification Platform

## Overview

This project is a web application that allows organizations to verify the authenticity of certificates and offer letters. It features both public-facing verification functionality and an admin dashboard for managing certificates and offer letters. The system is built with a modern tech stack including React, Express, and Drizzle ORM, following a client-server architecture with shared type definitions.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend

The frontend is built with React and uses a component-based architecture. It leverages:

- **React** for UI rendering and state management
- **TanStack Query** (React Query) for data fetching and caching
- **Wouter** for client-side routing
- **Shadcn UI** components for consistent design
- **Tailwind CSS** for styling
- **TypeScript** for type safety

The client-side code is organized into pages, components, hooks, and utility functions. Components are structured using the Shadcn UI approach, which provides a clean and maintainable component library with consistent styling.

### Backend

The backend is built with Node.js and Express, using:

- **Express** for the HTTP server and API routing
- **Drizzle ORM** for database interaction
- **Zod** for runtime validation
- **Session-based authentication** for user login and protection of admin routes

The server code handles API requests, database operations, and serves the client-side application in production.

### Database

The application uses Drizzle ORM with a schema defining three main tables:
- `users`: Stores admin user accounts
- `certificates`: Stores certificate information
- `offerLetters`: Stores offer letter information

In development, a MemStorage implementation is used, which will be replaced with PostgreSQL in production.

## Key Components

### Client Components

1. **Pages**: Each route in the application has a corresponding page component
   - Public pages (Home, Verify, FAQ)
   - Admin pages (Dashboard, Certificates, Offers, Login)

2. **UI Components**: Reusable UI elements built on Radix UI primitives
   - Form inputs
   - Buttons
   - Cards
   - Modals/Dialogs
   - Tables

3. **Verification Forms**: Components for validating certificates and offer letters

4. **Layout Components**: Header, footer, and page structure components

### Server Components

1. **API Routes**: Express routes for handling data operations
   - Certificate verification
   - Offer letter verification
   - Admin authentication
   - CRUD operations for certificates and offer letters

2. **Storage Layer**: Database abstraction for data access
   - Currently implemented with in-memory storage (MemStorage)
   - Will be connected to PostgreSQL in production

3. **Authentication**: Session-based authentication for admin users

4. **Validation**: Schema validation using Zod and Drizzle-zod

## Data Flow

1. **Certificate/Offer Letter Verification**:
   - User enters a verification code in the client application
   - Client makes a GET request to the verification API
   - Server validates the input and checks the database
   - Server returns verification status and details
   - Client displays the result to the user

2. **Admin Operations**:
   - Admin logs in through the login page
   - Upon successful authentication, a session is created
   - Admin can view, create, update, and delete certificates and offer letters
   - Each operation triggers corresponding API calls to the server
   - Server validates the request, performs the database operation, and returns results
   - Client updates the UI based on the server response

## External Dependencies

### Frontend Libraries
- React and React DOM for UI rendering
- TanStack Query for data fetching
- Wouter for routing
- Radix UI components for accessible UI primitives
- Tailwind CSS for styling
- Lucide React for icons
- React Hook Form for form handling
- Zod for schema validation

### Backend Libraries
- Express for HTTP server and routing
- Drizzle ORM for database operations
- Express-session for session management
- Connect-pg-simple for PostgreSQL session storage
- Vite for development server and bundling

## Deployment Strategy

The application is configured for deployment on Replit with:

1. **Build Process**:
   - Frontend: Vite builds the React application to static assets
   - Backend: esbuild bundles the server code

2. **Production Setup**:
   - Static assets are served by the Express server
   - Environment variables control database connections and other configuration
   - Session management uses secure cookies in production

3. **Database**:
   - PostgreSQL will be used in production
   - Drizzle ORM handles database schema and queries
   - Database migrations can be managed with Drizzle Kit

## Getting Started

1. Setup environment variables:
   - `DATABASE_URL`: PostgreSQL connection string
   - `SESSION_SECRET`: Secret for session encryption

2. Run development server:
   ```bash
   npm run dev
   ```

3. Build for production:
   ```bash
   npm run build
   ```

4. Start production server:
   ```bash
   npm run start
   ```

5. Manage database schema:
   ```bash
   npm run db:push
   ```