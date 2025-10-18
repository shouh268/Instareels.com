# FastReels - Instagram Reels Downloader with AI

## Overview

FastReels is a web application that enables users to download Instagram Reels, IGTV videos, and other Instagram content with AI-powered features. The application provides video quality options, AI-generated captions and hashtags, and title summarization using Google's Gemini AI. Built as a full-stack TypeScript application with a modern React frontend and Express backend, it emphasizes a clean, dark-mode-first user interface inspired by modern media platforms.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework & Build System**
- React 18 with TypeScript for type-safe component development
- Vite as the build tool and development server for fast hot module replacement
- Wouter for lightweight client-side routing
- TanStack React Query for server state management and API caching

**UI Component Strategy**
- Radix UI primitives for accessible, unstyled component foundations
- shadcn/ui design system with the "new-york" style variant
- Tailwind CSS for utility-first styling with custom design tokens
- Dark mode as the primary theme with optional light mode support via ThemeProvider context

**Design System**
- Custom color palette defined in CSS variables (HSL format) for both light and dark modes
- Material Design principles adapted for dark mode
- Inter font family from Google Fonts for consistent typography
- Comprehensive component library including forms, dialogs, toasts, accordions, and cards

**State Management Pattern**
- Local component state with React hooks (useState, useEffect)
- Server state managed through React Query with custom query client
- Theme preference persisted in localStorage
- Toast notifications for user feedback via custom toast hook

### Backend Architecture

**Server Framework**
- Express.js for HTTP server and API routing
- TypeScript with ES modules for type safety and modern JavaScript features
- Custom Vite integration for development mode with HMR support
- Middleware-based request/response logging

**API Design**
- RESTful endpoints with POST methods for data mutations
- Zod schema validation for request/response type safety
- JSON request/response format
- Error handling middleware with standardized error responses

**Key API Endpoints**
1. `/api/video/fetch` - Fetches Instagram video metadata (currently returns mock data)
2. `/api/ai/generate-content` - Generates captions and hashtags using Gemini AI
3. `/api/ai/summarize-title` - Summarizes video titles using Gemini AI

**Data Storage Approach**
- In-memory storage implementation (MemStorage class) as the current data layer
- Interface-based storage design (IStorage) for future database integration
- Drizzle ORM configured for PostgreSQL with Neon serverless adapter
- Database schema defined but not actively used in current implementation

**Rationale**: The in-memory storage serves as a placeholder while the application focuses on core video downloading functionality. The interface abstraction allows easy migration to persistent storage (PostgreSQL) without changing business logic.

### AI Integration

**Google Gemini AI**
- Using `@google/genai` SDK with API key authentication
- Model: gemini-2.5-flash for fast, cost-effective generation
- Structured JSON output via response schemas
- Two AI features:
  1. Caption and hashtag generation based on video title and creator
  2. Title summarization for quick content understanding

**Implementation Pattern**
- Separate gemini.ts module for AI operations
- Type-safe responses validated against Zod schemas
- Error handling for AI service failures
- Prompt engineering for social media content optimization

### Form Handling & Validation

**React Hook Form Integration**
- @hookform/resolvers for Zod schema integration
- Client-side validation before API calls
- Error state management and display
- Accessible form components with proper ARIA attributes

### Development Tooling

**TypeScript Configuration**
- Strict mode enabled for maximum type safety
- Path aliases configured (@/, @shared/, @assets/)
- ESNext module system with bundler resolution
- Incremental compilation for faster builds

**Development Experience**
- Replit-specific plugins for runtime error overlay, cartographer, and dev banner
- Hot module replacement in development mode
- Source maps for debugging
- PostCSS with Tailwind and Autoprefixer

## External Dependencies

### Third-Party Services

**Google Gemini AI API**
- Purpose: Generate captions, hashtags, and summarize video titles
- Authentication: API key stored in environment variable (GEMINI_API_KEY)
- Model: gemini-2.5-flash for production use
- Response format: Structured JSON with schema validation

**Instagram Content Fetching**
- Current implementation: Mock data generator
- Future integration point: Instagram scraping library or official API
- Note: Application currently simulates Instagram metadata for demonstration purposes

### Database

**Neon PostgreSQL**
- Serverless PostgreSQL adapter (@neondatabase/serverless)
- Drizzle ORM for type-safe database operations
- Connection: DATABASE_URL environment variable
- Schema: Defined in shared/schema.ts with User model
- Migration directory: ./migrations
- Current status: Configured but not actively used; in-memory storage is the active implementation

**Rationale for PostgreSQL readiness**: The application is architected to support user accounts and video history tracking in the future. The database infrastructure is prepared but not required for the core video downloading functionality.

### UI Component Libraries

**Radix UI Ecosystem**
- Comprehensive set of accessible, unstyled components
- Components used: Accordion, Alert Dialog, Avatar, Checkbox, Dialog, Dropdown Menu, Hover Card, Label, Navigation Menu, Popover, Progress, Radio Group, Scroll Area, Select, Separator, Slider, Switch, Tabs, Toast, Toggle, Tooltip
- Enables WCAG-compliant UI without custom accessibility implementation

**shadcn/ui**
- Pre-styled components built on Radix UI primitives
- "new-york" style variant for consistent design
- Tailwind CSS integration for customization
- Components live in codebase (not npm dependencies) for full control

### Styling & Design

**Tailwind CSS**
- Utility-first CSS framework
- Custom configuration with extended color palette
- CSS variables for theme-aware colors
- Dark mode class strategy
- PostCSS pipeline for processing

**Fonts**
- Google Fonts: Inter (weights 100-900)
- Preconnect optimization for faster font loading

### Build & Development Tools

**Vite Ecosystem**
- @vitejs/plugin-react for React Fast Refresh
- Runtime error modal for better debugging
- Custom middleware mode for Express integration
- Production builds to dist/public directory

**Replit Integration**
- @replit/vite-plugin-runtime-error-modal
- @replit/vite-plugin-cartographer
- @replit/vite-plugin-dev-banner
- Development-only plugins for enhanced Replit experience

### Type Safety & Validation

**Zod**
- Runtime type validation
- Request/response schema definitions
- drizzle-zod for ORM schema integration
- Shared schemas between client and server

### Utility Libraries

**Class Variance Authority (CVA)**
- Type-safe component variants
- Used for button, badge, and other component styling variations

**clsx & tailwind-merge**
- Conditional class name composition
- Tailwind class conflict resolution via cn() utility

**date-fns**
- Date manipulation and formatting
- Lightweight alternative to moment.js

**nanoid**
- Unique ID generation for client-side operations