---
title: Architecture
---

# NutriCue AI Technical Architecture

**Last Updated: August 25, 2025**

A comprehensive overview of the technical design and implementation decisions behind NutriCue AI's dietary supplement reminder system.

## System Overview

NutriCue AI is built as a cross-platform mobile application leveraging AI-powered natural language processing for intelligent reminder creation, with robust offline capabilities and platform-optimized notification delivery.

## Technology Stack

### Core Framework
- **React Native 0.79.5** - Cross-platform mobile development
- **Expo 53.0.22** - Development platform and build toolchain
- **TypeScript** - Type-safe development environment

### State Management
- **Zustand** - Lightweight state management for reminders and AI conversations
- **AsyncStorage** - Persistent local storage with retry logic and memory fallback
- **JSON Storage** - Structured data persistence via Zustand middleware

### AI Integration
- **OpenAI API** - Natural language processing and image analysis
- **Custom Offline Service** - Local pattern matching for AI-free operation
- **Intelligent Fallback** - Seamless degradation when AI services unavailable

### Notification System
- **Expo Notifications** - Cross-platform notification scheduling
- **Platform-Specific Optimization** - iOS KeyboardAvoidingView, Android adjustResize
- **iOS Compliance** - 64-notification limit handling with rolling window scheduling

## Architecture Patterns

### Data Flow
```
User Input → AI Processing → Reminder Creation → Local Storage → Notification Scheduling
```

### Offline-First Design
- **Local Data Persistence** - All user data stored on-device via AsyncStorage
- **AI Service Abstraction** - Pluggable online/offline processing modes
- **Graceful Degradation** - Full functionality without external dependencies

### Security & Privacy
- **Device-Level Encryption** - Leveraging platform security features
- **Minimal Data Transmission** - Only AI features require external communication
- **User Control** - Complete offline mode available

## Subscription Architecture

### Revenue Model
- **RevenueCat Integration** - Cross-platform subscription management
- **Usage Tracking** - Local enforcement of free tier limits
- **Feature Gating** - AI capabilities tied to subscription status

### Scalability Considerations
- **Local-First Processing** - Reduces server load and latency
- **Efficient API Usage** - Smart caching and request optimization
- **Platform Store Integration** - Native payment processing

## Development Practices

### Testing Strategy
- **Jest** - Unit and integration testing
- **TypeScript** - Compile-time error prevention
- **Platform Testing** - iOS Simulator and Android Emulator validation

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
- **Request Optimization** - Minimal data transmission to OpenAI
- **Context Management** - Efficient conversation history handling
- **Fallback Mechanisms** - Instant offline mode switching

---

[Home](index.md) | [Screenshots](screenshots.md) | [Architecture](architecture.md) | [Privacy](privacy.md)
