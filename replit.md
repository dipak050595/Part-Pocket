# Party Pocket

## Overview

Party Pocket is a hybrid mobile-first web application that combines interactive party games with productivity utilities. Built as a Progressive Web App (PWA), it functions entirely offline, targeting ages 13-35 for social gatherings and daily task management. The app features two main party games (Truth or Dare with bottle spinner, Dumb Charades with team-based gameplay) alongside productivity tools (notes, tasks, calculator, coin toss).

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework Stack:**
- React 18+ with TypeScript for type-safe component development
- Vite as the build tool and development server
- Wouter for lightweight client-side routing
- TanStack Query for state management and data caching

**UI Component System:**
- Shadcn/ui component library built on Radix UI primitives
- Tailwind CSS for utility-first styling with custom design tokens
- Mobile-first responsive design with full viewport layouts (h-screen)
- Custom CSS variables for theming (light/dark mode support)
- Typography: Inter (body) and Poppins (display) from Google Fonts

**Design Pattern:**
- Reference-based approach inspired by Houseparty (playful gaming), Instagram (mobile UI), and Notion (productivity)
- Bottom navigation bar with 5 persistent tabs (Games, Toss, Notes, Tasks, Calculator)
- Card-based layouts with hover/active elevation states
- Safe area padding for mobile notches (px-4 standard, pb-20 for bottom nav clearance)

### Data Storage Architecture

**Client-Side Storage:**
- LocalStorage as primary persistence layer via custom StorageManager class
- No backend database - 100% offline-capable application
- Zod schemas for runtime type validation of stored data structures

**Storage Domains:**
- Notes: Title, content, timestamps (created/updated)
- Tasks: Text, completion status, creation timestamp
- Truth or Dare Games: Players, rounds, game history, custom content
- Charades Games: Teams, scores, word categories, game sessions
- Settings: User preferences (future expansion)

**Data Models (shared/schema.ts):**
- Player schema: ID, name, optional custom truths/dares, score tracking
- Truth or Dare game schema: Game mode (simple/allSet), players array, round tracking, usage history
- Team schema: ID, name, icon, color, player list, score, statistics
- Charades word schema: Word, category, difficulty levels

### Game Logic Architecture

**Truth or Dare:**
- Two modes: Simple (quick play with default content) and All Set (custom player-specific content)
- Bottle spinner component using CSS transforms and rotation animations
- Round-based progression with used content tracking to avoid repetition
- Player score tracking (completed vs skipped challenges)

**Charades:**
- Team-based gameplay (2-4 teams supported)
- Category selection from predefined word banks (Bollywood Movies, etc.)
- Difficulty-based word filtering (easy/medium/hard)
- Timer-based rounds with score tracking and statistics

### Routing Structure

**Navigation Hierarchy:**
- Home dashboard → Game/utility selection
- Truth or Dare: Mode selection → Player setup → Game play
- Charades: Team setup → Category selection → Game play
- Direct access utilities: Toss, Notes, Tasks, Calculator

### Component Patterns

**Reusable Components:**
- BottleSpinner: Radial player layout with rotation animations
- BottomNav: Persistent navigation with active state indicators
- Confetti: Canvas-based celebration animations
- Custom Shadcn/ui components: Cards, Buttons, Dialogs, Inputs, etc.

**State Management:**
- Local component state with useState for UI interactions
- LocalStorage synchronization on mount/unmount
- React Query for future API integration capability

## External Dependencies

### UI Libraries
- **Radix UI**: Headless component primitives (dialogs, popovers, dropdowns, etc.)
- **Lucide React**: Icon library for consistent iconography
- **Tailwind CSS**: Utility-first styling framework with PostCSS
- **Class Variance Authority**: Type-safe component variant management
- **Embla Carousel**: Touch-friendly carousel implementation

### Development Tools
- **Vite Plugins**: 
  - @vitejs/plugin-react for React Fast Refresh
  - @replit/vite-plugin-runtime-error-modal for error overlays
  - @replit/vite-plugin-cartographer (dev mode, conditional)
  - @replit/vite-plugin-dev-banner (dev mode, conditional)
- **TypeScript**: Type safety across client and shared code
- **ESBuild**: Fast bundling for production builds

### Form & Validation
- **React Hook Form**: Form state management
- **@hookform/resolvers**: Validation resolver integration
- **Zod**: Runtime type validation and schema definition
- **Drizzle Zod**: Database schema to Zod schema conversion

### Database (Configured but not actively used)
- **@neondatabase/serverless**: PostgreSQL driver for Neon
- **Drizzle ORM**: Type-safe database queries and migrations
- **Connect-pg-simple**: PostgreSQL session store
- Note: Database configured via drizzle.config.ts but current implementation is fully client-side

### Utility Libraries
- **date-fns**: Date manipulation and formatting
- **clsx & tailwind-merge**: Conditional className management
- **nanoid**: Unique ID generation

### Backend Framework (Minimal)
- **Express.js**: HTTP server for serving static assets and future API routes
- **Node.js**: Server runtime environment
- Current backend role: Static file serving and Vite middleware in development