---
title: Architecture
---

# NutriCue AI Technical Architecture

**Last Updated: September 19, 2025**  
**Status: App Store Ready**

A comprehensive overview of the production-ready technical architecture behind NutriCue AI's AI-powered reminder system, featuring backend-proxy AI integration, Railway deployment, and cross-platform subscription management.

## Production System Overview

NutriCue AI is a production-ready full-stack application with a React Native mobile frontend and Railway-deployed Node.js backend, featuring secure AI integration via backend proxy, PostgreSQL database, and RevenueCat subscription management. The system is optimized for reminder management with HTTPS-only communication and App Store compliance.

## Backend Architecture

### Core Framework
- **Node.js** - JavaScript runtime environment
- **Express.js** - Web application framework
- **TypeScript** - Type safety for backend services
- **JWT Authentication** - Secure user authentication and authorization

### Security & Middleware
- **Helmet.js** - Security headers and protection
- **CORS** - Cross-origin resource sharing configuration
- **Express Rate Limiter** - API rate limiting and abuse prevention
- **Express Validator** - Input validation and sanitization
- **bcryptjs** - Password hashing and security

### API Architecture
- **RESTful Endpoints** - `/api/v1/` versioned API structure
- **Health Monitoring** - System status and uptime checks
- **Authentication Routes** - User registration, login, device auth
- **AI Processing Routes** - Reminder parsing and image analysis
- **Reminder Management** - CRUD operations for reminders

## Technology Stack

### Mobile Frontend
- **React Native** - Cross-platform mobile development
- **Expo** - Development platform and build toolchain
- **TypeScript** - Type-safe development environment
- **Expo Router** - File-based navigation system
- **React Native Paper** - Material Design 3 components

### State Management
- **Zustand** - Modern state management with TypeScript support
- **Zustand Persist Middleware** - Automatic AsyncStorage persistence
- **AsyncStorage** - Local data persistence with retry logic
- **Custom Hooks** - Encapsulated business logic

### Production Infrastructure
- **Railway Deployment** - Production hosting at `https://nutricue-backend-production.up.railway.app`
- **PostgreSQL Database** - Production database with connection pooling and automatic backups
- **HTTPS/SSL** - Automatic certificate management via Railway
- **Health Monitoring** - `/health`, `/ready`, `/live` endpoints for production reliability
- **Auto-Scaling** - Railway infrastructure handles traffic growth automatically

### AI Integration (Backend Proxy)
- **OpenAI GPT-4o** - Natural language processing via secure backend proxy
- **OpenAI GPT-4o Vision** - Image analysis for text recognition and scanning
- **Backend Proxy Security** - API keys secured in backend, never exposed to mobile app
- **Usage Tracking** - PostgreSQL-based limits and subscription validation
- **Cost Control** - Backend-managed API usage and rate limiting

### Subscription Management
- **RevenueCat SDK** - Cross-platform subscription management with real API keys
- **Freemium Model** - 5 active reminders, 3 image scans, 15 AI interactions/month free
- **Premium Tier** - Unlimited reminders & AI conversations, 20 image scans/month
- **Pricing** - $5.99/month or $39.99/year for AI Premium
- **Feature Gating** - Usage limits enforced at backend level

### Notification System
- **Expo Notifications** - Local push notifications with smart scheduling
- **Platform-specific channels** - Android notification channels for reminders
- **Smart Scheduling** - AI-powered reminder timing optimization
- **Permission Management** - Smart onboarding flow with skip handling

### User Onboarding
- **2-Screen Flow** - Welcome screen and permissions setup
- **Smart Permission Handling** - Tracks permission requests and handles skips
- **Generic Content** - Works for any reminder use case
- **Theme Responsive** - Full light/dark mode support

## Architecture Patterns

### Production Data Flow (Backend Proxy)
```
Mobile App → JWT Auth → Backend API → Usage Validation → OpenAI GPT-4o → PostgreSQL → Response
     ↓              ↓              ↓               ↓              ↓              ↓
RevenueCat → User Validation → Rate Limiting → AI Processing → Usage Tracking → Mobile App
```

### Subscription Flow
```
App Launch → RevenueCat SDK → Subscription Service → Usage Tracking → Feature Gating
     ↓              ↓                    ↓                 ↓              ↓
Local State → Platform Store → Backend Validation → PostgreSQL → UI Components
```

### Security & Compliance
- **HTTPS-Only Communication** - All production traffic encrypted
- **API Key Security** - OpenAI keys secured in Railway backend, never exposed to client
- **JWT Authentication** - Production-grade device authentication
- **PostgreSQL with RLS** - Row Level Security for data isolation
- **Privacy Compliant** - General reminder focus, no medical claims or prescription handling

### Graceful Degradation
- **Offline Queue** - Store AI requests for later processing when backend unavailable
- **Manual Fallback** - Direct users to traditional reminder creation
- **Clear Messaging** - Inform users of limited functionality
- **No Blocking** - Core reminder functionality never depends solely on AI services

## Production Architecture Benefits

### Scalability & Performance
- **Railway Auto-scaling** - Backend infrastructure scales with user growth
- **PostgreSQL Optimization** - Connection pooling and query optimization
- **Rate Limiting** - Prevents abuse and controls costs
- **Health Monitoring** - Production reliability with comprehensive endpoints

### Monetization Integration
- **RevenueCat Handles Complexity** - Cross-platform subscription management
- **Backend Validates Subscriptions** - Usage limits enforced before AI requests
- **Real-time Tracking** - PostgreSQL-based usage monitoring
- **Graceful Limit Handling** - Seamless transition when limits reached

### Scalability Considerations
- **Local-First Processing** - Reduces server load and latency
- **Efficient API Usage** - Smart caching and request optimization
- **Platform Store Integration** - Native payment processing

## Development Practices

### Testing Strategy
- **Jest** - Comprehensive testing framework for frontend and backend
- **Supertest** - HTTP endpoint testing for backend API
- **TypeScript ESLint** - Code quality and consistency
- **90%+ Coverage** - Comprehensive test suite requirements
- **Mock Services** - RevenueCat, OpenAI, and database mocking

### Build Pipeline
- **EAS Build** - Expo Application Services for production builds
- **Automated Versioning** - Semantic versioning with build number increment
- **Multi-Environment Support** - Development, preview, and production configurations

## Performance Optimizations

### Notification Efficiency
- **Batch Scheduling** - Minimize system notification overhead
- **Smart Recurrence** - Efficient handling of complex repeat patterns
- **Memory Management** - Proper cleanup of scheduled notifications

### AI Processing
- **Backend Proxy** - Secure API key management and request routing
- **Request Optimization** - Minimal data transmission to OpenAI
- **Context Management** - Efficient conversation history handling
- **Fallback Mechanisms** - Instant offline mode switching
- **Cost Control** - Usage tracking and rate limiting

---

[Home](index.md) | [Screenshots](screenshots.md) | [Architecture](architecture.md) | [Privacy](privacy.md)
