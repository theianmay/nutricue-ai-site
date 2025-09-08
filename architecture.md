---
title: Architecture
---

# NutriCue AI Technical Architecture

**Last Updated: September 8, 2025**

A comprehensive overview of the technical design and implementation decisions behind NutriCue AI's dietary supplement reminder system.

## System Overview

NutriCue AI is built as a full-stack application with a React Native mobile frontend and Node.js backend, leveraging AI-powered natural language processing for intelligent supplement reminder creation, with robust offline capabilities and platform-optimized notification delivery.

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
- **Reminder Management** - CRUD operations for supplement reminders

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

### AI Integration
- **OpenAI GPT-4o** - Natural language processing and vision capabilities
- **OpenAI GPT-4o Vision** - Image analysis and text extraction
- **Backend AI Proxy** - Secure API key management and cost control
- **Custom AI Prompts** - Supplement-focused reminder parsing and scheduling
- **Offline Mode** - Fallback responses when AI services unavailable

### Notification System
- **Expo Notifications** - Local push notifications
- **Platform-specific channels** - Android notification channels
- **Production-grade scheduling** - UUID tracking and comprehensive error handling
- **iOS Compliance** - 64-notification limit handling with rolling window scheduling

## Architecture Patterns

### Mobile App Data Flow
```
User Input → AI Service Layer → Backend Proxy → OpenAI API → Reminder Creation → Local Storage → Notification Scheduling
```

### Backend Data Flow
```
Mobile App → JWT Auth → Rate Limiting → AI Processing → OpenAI API → Response → Mobile App
```

### Offline-First Design
- **Local Data Persistence** - All user data stored on-device via AsyncStorage
- **AI Service Abstraction** - Pluggable online/offline processing modes
- **Graceful Degradation** - Full functionality without external dependencies

### Security & Privacy
- **Backend Proxy** - API keys secured on backend server, not exposed in mobile app
- **JWT Authentication** - Secure user authentication and session management
- **Rate Limiting** - Express rate limiter with API abuse prevention
- **Device-Level Encryption** - Leveraging platform security features
- **User Control** - Complete offline mode available

## Subscription Architecture

### Revenue Model
- **RevenueCat SDK** - Cross-platform subscription management
- **Freemium Model** - 15 AI interactions/month free, unlimited premium
- **Usage Tracking** - Monthly limits and premium feature gating
- **Feature Gating** - AI capabilities tied to subscription status

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
