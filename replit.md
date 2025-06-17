# FileFlow - File Conversion Application

## Overview

FileFlow is a full-stack web application that provides professional file conversion services. Users can upload files and convert them between various formats including PDF, images, videos, and audio files. The application features a modern React frontend with shadcn/ui components and an Express.js backend with PostgreSQL database integration.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter for client-side routing
- **UI Components**: shadcn/ui component library built on Radix UI primitives
- **Styling**: Tailwind CSS with CSS variables for theming
- **State Management**: TanStack Query (React Query) for server state management
- **Build Tool**: Vite for development and production builds
- **File Uploads**: React Dropzone for drag-and-drop file uploads

### Backend Architecture
- **Runtime**: Node.js with Express.js framework
- **Language**: TypeScript with ES modules
- **Authentication**: Replit Auth with OpenID Connect
- **Session Management**: Express sessions with PostgreSQL storage
- **File Handling**: Multer for multipart form data and file uploads
- **API Design**: RESTful API with JSON responses

### Database Architecture
- **Primary Database**: PostgreSQL via Neon serverless
- **ORM**: Drizzle ORM with TypeScript schema definitions
- **Connection Pool**: @neondatabase/serverless with WebSocket support
- **Migrations**: Drizzle Kit for schema migrations

## Key Components

### Authentication System
- **Provider**: Replit Auth with OIDC integration
- **Session Storage**: PostgreSQL-backed sessions using connect-pg-simple
- **User Management**: Automatic user creation and profile synchronization
- **Security**: Secure cookies with HTTP-only and secure flags

### File Conversion System
- **Upload Handler**: Multer middleware with 100MB file size limit
- **Supported Formats**: 
  - Documents: PDF, DOCX, TXT
  - Images: JPG, PNG, GIF, WebP
  - Videos: MP4, AVI, MOV, WMV
  - Audio: MP3, WAV, FLAC, AAC
- **Conversion Tracking**: Database records for conversion history and status
- **File Storage**: Local filesystem with uploads directory

### Database Schema
- **Users Table**: Profile information synced from Replit Auth
- **Sessions Table**: Express session storage for authentication
- **Conversions Table**: File conversion records with status tracking

## Data Flow

### User Authentication Flow
1. User clicks login/signup → Redirected to Replit Auth
2. Successful authentication → User profile synced to database
3. Session established → User redirected to dashboard

### File Conversion Flow
1. User uploads file via drag-and-drop or file picker
2. Frontend validates file type and size
3. File sent to backend with target format
4. Conversion record created in database with "processing" status
5. File processed (conversion logic to be implemented)
6. Database updated with completion status and download URL
7. User can download converted file or view in history

### Data Synchronization
- React Query manages all server state with automatic caching
- Real-time updates for conversion status (polling-based)
- Optimistic updates for immediate UI feedback

## External Dependencies

### Core Dependencies
- **@neondatabase/serverless**: PostgreSQL database connection
- **drizzle-orm**: Type-safe database queries and migrations
- **@tanstack/react-query**: Server state management
- **@hookform/resolvers**: Form validation with Zod schemas
- **multer**: File upload handling
- **passport**: Authentication middleware

### UI Dependencies
- **@radix-ui/***: Headless UI components for accessibility
- **tailwindcss**: Utility-first CSS framework
- **class-variance-authority**: Component variant management
- **lucide-react**: Icon library

### Development Dependencies
- **vite**: Build tool and development server
- **typescript**: Type checking and compilation
- **tsx**: TypeScript execution for development

## Deployment Strategy

### Development Environment
- **Command**: `npm run dev`
- **Server**: Express with Vite middleware for HMR
- **Database**: Neon PostgreSQL with connection pooling
- **Port**: 5000 (configurable via environment)

### Production Environment
- **Build Process**: 
  1. Frontend: Vite builds React app to `dist/public`
  2. Backend: esbuild bundles server code to `dist/index.js`
- **Start Command**: `npm start` runs production server
- **Deployment**: Replit Autoscale with port 80 external mapping

### Environment Configuration
- **DATABASE_URL**: PostgreSQL connection string (required)
- **SESSION_SECRET**: Session encryption key (required)
- **REPL_ID**: Replit environment identifier
- **NODE_ENV**: Environment mode (development/production)

## Changelog

```
Changelog:
- June 17, 2025. Initial setup
```

## User Preferences

```
Preferred communication style: Simple, everyday language.
```