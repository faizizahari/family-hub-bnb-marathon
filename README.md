<div align="center">
<img width="1200" height="475" alt="GHBanner" src="https://github.com/user-attachments/assets/0aa67016-6eaf-458a-adb2-6e31a0763ed6" />
</div>

# Family Hub - Complete Family Management Platform

[![React](https://img.shields.io/badge/React-19.2.0-blue.svg)](https://reactjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.8.2-blue.svg)](https://www.typescriptlang.org/)
[![Firebase](https://img.shields.io/badge/Firebase-12.3.0-orange.svg)](https://firebase.google.com/)
[![Vite](https://img.shields.io/badge/Vite-6.2.0-purple.svg)](https://vitejs.dev/)

> A centralized digital platform designed to help families manage their daily lives, stay organized, and maintain strong connections through AI-powered features and real-time collaboration.

---

## 📚 Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [Technology Stack](#-technology-stack)
- [Architecture](#-architecture)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Local Development](#local-development)
  - [Docker Deployment](#docker-deployment)
- [Application Structure](#-application-structure)
- [How It Works](#-how-it-works)
  - [Authentication Flow](#1-authentication-flow)
  - [Data Synchronization](#2-data-synchronization)
  - [AI Integration](#3-ai-integration)
  - [Notification System](#4-notification-system)
- [Core Features Explained](#-core-features-explained)
- [Configuration](#-configuration)
- [Development Guide](#-development-guide)
- [Deployment](#-deployment)
- [License](#-license)

---

## 🎯 Overview

**Family Hub** is a Progressive Web Application (PWA) that serves as a comprehensive family management system. It consolidates scheduling, meal planning, task management, routine tracking, and gamification into a single, AI-enhanced interface powered by Google Gemini AI.

### **What Problems Does It Solve?**

- 📅 **Scattered Schedules**: Centralize all family events, appointments, and activities
- 🍽️ **Meal Planning Chaos**: Plan meals, track inventory, and manage recipes efficiently
- ✅ **Task Management**: Organize to-dos, routines, and household responsibilities
- 🏆 **Engagement**: Gamify tasks with points, rewards, and achievements
- 🤖 **Manual Entry**: Leverage AI to automate content creation and reduce tedious data input
- 📱 **Device Sync**: Real-time synchronization across all family devices
- ✈️ **Offline Access**: Full functionality without internet connectivity

### **Target Users**

- Busy families managing multiple schedules
- Parents coordinating children's activities
- Households wanting to improve meal planning efficiency
- Families seeking to build better routines and habits
- Groups looking to gamify household tasks and responsibilities

---

## ✨ Key Features

### 📅 **Unified Calendar Management**
- Shared family calendar with events, appointments, and activities
- Support for recurring events, multi-day events, and all-day activities
- Member assignment and category-based organization
- **AI-powered event generation** from natural language (e.g., "Soccer practice tomorrow at 3pm")
- Multiple view modes: Month, Week, and Day views

### 🍳 **Meal Planning & Inventory**
- Recipe management with ingredient tracking
- Fridge inventory system with expiry date monitoring
- **AI-generated recipe suggestions** based on available ingredients
- Weekly meal planning with breakfast, lunch, dinner, and snack slots
- Automatic shopping list generation from recipes

### ✅ **Task & Routine Management**
- Individual and shared to-do lists with due dates
- Recurring task support with flexible recurrence patterns
- Customizable routines with task checklists
- **AI-assisted routine generation** from descriptions
- Points-based completion tracking for motivation

### 📝 **Shopping & Lists**
- Multiple customizable lists (shopping, general, etc.)
- Sub-item tracking with completion status
- Member assignment for collaborative list management
- Real-time updates across all family devices

### 🏆 **Gamification System**
- Points system (weekly and all-time leaderboards)
- Achievement badges across multiple categories
- Reward redemption system
- Family leaderboard for friendly competition
- Motivates consistent participation

### 🏠 **Intelligent Dashboard**
- Customizable widget-based homescreen
- Weather, air quality, and UV index widgets
- Quick access to upcoming events, meals, and tasks
- Photo slideshow widget for family memories
- Sticky notes for quick reminders

### 🤖 **AI-Powered Features** (Google Gemini)
- Natural language event creation
- Recipe generation from available ingredients
- Routine creation from descriptions
- Automatic image generation for events and todos
- Help article generation and editing
- Image content extraction (OCR)

### 🔔 **Smart Notifications**
- Configurable event and task reminders
- Weather-based alerts (rain, UV index)
- Air quality warnings
- Meal preparation reminders
- Overdue task notifications

### 📸 **Media & Memories**
- Family photo gallery
- Image upload and management
- Shared media storage
- Photo slideshow widgets

### 🔄 **Cross-Device Synchronization**
- Real-time updates across all family devices
- Offline support with automatic sync when back online
- Multi-tab synchronization
- Optimistic UI updates for instant feedback

---

## 🛠 Technology Stack

### **Frontend**
- **Framework**: React 19.2.0 with TypeScript 5.8.2
- **Build Tool**: Vite 6.2.0 (fast development and optimized production builds)
- **UI Styling**: Tailwind CSS (utility-first CSS framework)
- **State Management**: React Hooks (useState, useEffect, useMemo)
- **Progressive Web App**: Service Worker for offline functionality

### **Backend & Infrastructure**
- **Hosting**: Google Cloud Run
  - Serverless containerized deployment
  - Auto-scaling and global CDN
  - Automatic HTTPS and SSL certificates
- **Authentication**: Firebase Authentication
  - Google Sign-In (OAuth)
  - Email/Password authentication
- **Database**: Cloud Firestore
  - Real-time listeners for instant synchronization
  - Offline persistence with IndexedDB
  - Multi-tab synchronization support
- **File Storage**: Firebase Storage
  - Image uploads and optimized storage
  - CDN delivery for fast media access
- **Analytics**: Firebase Analytics for usage tracking

### **AI Integration**
- **AI Provider**: Google Gemini AI (@google/genai v0.14.0)
- **Models**:
  - `gemini-2.5-flash` - Text generation, function calling, recipe/routine generation
  - `gemini-2.5-flash-image` - Image generation for events and todos

### **External APIs**
- **Weather**: Open-Meteo API (weather forecasts, UV index, air quality)
- **Geolocation**: Browser Geolocation API
- **Notifications**: Browser Notification API

---

## 🏗 Architecture

Family Hub follows a **client-centric architecture** with Firebase as the backend-as-a-service platform.

### **High-Level Architecture**

```
┌─────────────────────────────────────────────────────────────┐
│              Google Cloud Run (Hosting)                      │
│                   React Application                          │
└─────────────────────┬───────────────────────────────────────┘
                      │
┌─────────────────────┴───────────────────────────────────────┐
│                    Client Application                        │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │   React UI   │  │  State Mgmt  │  │   Utils      │      │
│  │  Components  │◄─┤  (Hooks)     │◄─┤  (Business   │      │
│  │              │  │              │  │   Logic)     │      │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘      │
│         │                 │                 │               │
└─────────┼─────────────────┼─────────────────┼───────────────┘
          │                 │                 │
     ┌────┴────────┬────────┴─────┬──────────┴────┐
     ▼             ▼              ▼               ▼
┌──────────┐  ┌─────────┐  ┌──────────┐  ┌──────────┐
│ Firebase │  │ Gemini  │  │ External │  │ Browser  │
│ Services │  │   AI    │  │   APIs   │  │   APIs   │
│          │  │         │  │          │  │          │
│•Firestore│  │• Text   │  │• Weather │  │• Geoloc  │
│• Auth    │  │• Image  │  │• AQI     │  │• Notif   │
│• Storage │  │• Func   │  │          │  │          │
└──────────┘  └─────────┘  └──────────┘  └──────────┘
```

### **Data Flow Pattern**

Family Hub uses an **optimistic update pattern** for instant user feedback:

1. **User Action** → Component Handler
2. **Optimistic Update** → Local state updates immediately (instant UI feedback)
3. **Data Sanitization** → Remove invalid data for Firestore
4. **Firestore Write** → Async write to Firebase (background)
5. **Real-time Sync** → Firestore listeners update all connected devices
6. **State Synchronization** → All devices reflect the latest data

This ensures the UI feels instant while maintaining data consistency across all devices.

---

## 🚀 Getting Started

### Prerequisites

**Required:**
- Node.js (v16 or higher)
- npm or yarn package manager
- Gemini API Key ([Get one here](https://ai.google.dev/))
- Firebase Project ([Create one here](https://console.firebase.google.com/))

---

### Local Development Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd Family-Hub
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure environment variables**
   
   Create a `.env.local` file in the root directory:
   ```env
   GEMINI_API_KEY=your_gemini_api_key_here
   ```

4. **Configure Firebase** (Important!)
   
   Update `firebase.ts` with your Firebase project configuration:
   ```typescript
   const firebaseConfig = {
     apiKey: "YOUR_API_KEY",
     authDomain: "YOUR_AUTH_DOMAIN",
     projectId: "YOUR_PROJECT_ID",
     storageBucket: "YOUR_STORAGE_BUCKET",
     messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
     appId: "YOUR_APP_ID",
     measurementId: "YOUR_MEASUREMENT_ID"
   };
   ```

5. **Start the development server**
   ```bash
   npm run dev
   ```
   
   The app will be available at `http://localhost:3000`

6. **Build for production**
   ```bash
   npm run build
   ```

7. **Preview production build**
   ```bash
   npm run preview
   ```

---

## 📁 Application Structure

```
Family-Hub/
├── 📂 components/              # React components
│   ├── 📂 calendar/            # Calendar feature components
│   │   ├── CalendarView.tsx    # Main calendar view
│   │   ├── CalendarHeader.tsx  # View mode selector
│   │   ├── 📂 modals/          # Calendar modals (event editor, AI generator, etc.)
│   │   └── 📂 views/           # Month/Week/Day views
│   ├── 📂 routines/            # Routines management
│   │   ├── RoutinesView.tsx    # Main routines view
│   │   ├── 📂 modals/          # Routine creation, AI generation
│   │   └── TaskItem.tsx        # Individual task components
│   ├── 📂 meal-planner/        # Meal planning features
│   │   └── 📂 modals/          # Recipe and meal modals
│   ├── 📂 settings/            # Settings page cards
│   ├── 📂 widgets/             # Dashboard widgets
│   │   ├── WeatherWidget.tsx   # Weather display
│   │   ├── CalendarWidget.tsx  # Upcoming events
│   │   ├── MealPlanWidget.tsx  # Weekly meals
│   │   └── ...                 # Other widgets
│   ├── CalendarView.tsx        # Calendar view wrapper
│   ├── HomescreenView.tsx      # Customizable dashboard
│   ├── TodosView.tsx           # To-do list management
│   ├── ListsView.tsx           # Shopping/general lists
│   ├── InventoryView.tsx       # Fridge inventory
│   ├── LeaderboardView.tsx     # Points leaderboard
│   ├── AwardsView.tsx          # Rewards and achievements
│   ├── ProfileView.tsx         # User profile
│   ├── SettingsView.tsx        # App settings
│   ├── LoginView.tsx           # Authentication
│   ├── OnboardingView.tsx      # Family creation/joining
│   ├── MealPlannerView.tsx     # Meal planning view
│   ├── HelpCenterView.tsx      # Help and documentation
│   ├── MediaGalleryView.tsx    # Photo gallery
│   └── ...                     # Other shared components
│
├── 📂 utils/                   # Utility functions
│   ├── calendarUtils.ts        # Calendar calculations
│   ├── firestoreUtils.ts       # Firestore data sanitization
│   ├── imageUtils.ts           # Image processing and AI generation
│   ├── inviteCode.ts           # Invite code generation
│   └── notificationEngine.ts   # Smart notification system
│
├── 📂 data/                    # Static data
│   ├── recipes.ts              # Initial recipe data
│   ├── ingredients.ts          # Ingredient definitions
│   ├── inventory.ts            # Initial inventory items
│   └── help-articles.ts        # Help center content
│
├── App.tsx                     # Root component (state orchestrator)
├── types.ts                    # TypeScript type definitions
├── constants.tsx               # Application constants and defaults
├── firebase.ts                 # Firebase initialization
├── index.tsx                   # App entry point
├── index.html                  # HTML template
├── vite.config.ts              # Vite build configuration
├── package.json                # Dependencies
├── tsconfig.json               # TypeScript configuration
├── manifest.json               # PWA manifest
├── service-worker.js           # PWA offline support
├── metadata.json               # App metadata
└── firestore.rules             # Firestore security rules (template)
```

---

## ⚙️ How It Works

### 1. **Authentication Flow**

```
┌─────────────────────────────────────────────────────────────┐
│                    User Visits App                           │
└─────────────────┬───────────────────────────────────────────┘
                  │
                  ▼
┌─────────────────────────────────────────────────────────────┐
│          Check Firebase Authentication State                 │
│              (onAuthStateChanged listener)                   │
└─────────────────┬───────────────────────────────────────────┘
                  │
        ┌─────────┴─────────┐
        │                   │
        ▼                   ▼
    Not Logged         Logged In
        │                   │
        ▼                   ▼
  Show LoginView      Load User Document
        │              (users/{uid})
        │                   │
        ▼                   ▼
  User Signs In       Has familyId?
  (Google/Email)            │
        │           ┌───────┴───────┐
        │           │               │
        └──────────►│               ▼
                  Yes           No familyId
                    │               │
                    ▼               ▼
            Load Family Data   Show OnboardingView
            (families/{id})    (Create/Join Family)
                    │               │
                    └───────┬───────┘
                            │
                            ▼
                    Main Application
                  (Calendar, Todos, etc.)
```

**Steps:**

1. App loads and checks if user is authenticated via Firebase Auth
2. If not authenticated → Show `LoginView`
3. If authenticated → Load user document from Firestore (`users/{uid}`)
4. Check if user has `familyId`
   - **No familyId** → Show `OnboardingView` (create or join a family)
   - **Has familyId** → Load family data from Firestore (`families/{familyId}`)
5. Subscribe to real-time updates via Firestore listeners
6. Render main application with all features

---

### 2. **Data Synchronization**

Family Hub uses **real-time bidirectional synchronization** powered by Firebase Firestore:

```
┌──────────────────────────────────────────────────────────┐
│                  User Action (Device A)                   │
│              (e.g., Create Calendar Event)                │
└─────────────────────┬────────────────────────────────────┘
                      │
                      ▼
┌──────────────────────────────────────────────────────────┐
│          1. Optimistic Update (Local State)              │
│              → UI updates INSTANTLY                       │
└─────────────────────┬────────────────────────────────────┘
                      │
                      ▼
┌──────────────────────────────────────────────────────────┐
│          2. Data Sanitization                            │
│        (Remove undefined, circular refs, etc.)           │
└─────────────────────┬────────────────────────────────────┘
                      │
                      ▼
┌──────────────────────────────────────────────────────────┐
│        3. Firestore Write (Async Background)             │
│          updateDoc(families/{familyId}, data)            │
└─────────────────────┬────────────────────────────────────┘
                      │
                      ▼
┌──────────────────────────────────────────────────────────┐
│          Firestore Database (Cloud)                      │
│              Data persisted in cloud                      │
└─────────────────────┬────────────────────────────────────┘
                      │
        ┌─────────────┴─────────────┐
        │                           │
        ▼                           ▼
  Device A                      Device B, C, D...
  (Originator)                  (Other Devices)
        │                           │
        ▼                           ▼
┌─────────────────┐     ┌─────────────────────┐
│ Firestore       │     │ Firestore Listener  │
│ Listener        │     │ (onSnapshot)        │
│ (onSnapshot)    │     │                     │
└────────┬────────┘     └──────────┬──────────┘
         │                         │
         ▼                         ▼
   Update State              Update State
   (Confirmation)           (New Data Received)
         │                         │
         └─────────┬───────────────┘
                   │
                   ▼
         ┌─────────────────────┐
         │  All Devices in Sync │
         └─────────────────────┘
```

**Key Points:**

- **Optimistic Updates**: UI updates immediately before server confirmation (instant feedback)
- **Firestore Listeners**: All connected devices receive updates in real-time via `onSnapshot`
- **Offline Support**: Changes queued locally when offline, synced when back online
- **Multi-tab Support**: Multiple browser tabs on the same device stay synchronized
- **Conflict Resolution**: Last-write-wins (Firestore's default behavior)

**Example in Code:**

```typescript
const setTodos = (updater: React.SetStateAction<Todo[]>) => {
    setAppState(prev => {
        if (!prev) return null;
        
        // 1. Compute new state
        const newTodos = typeof updater === 'function' 
            ? updater(prev.todos) 
            : updater;
        
        // 2. Update Firestore (async, non-blocking)
        updateFamilyData({ todos: newTodos });
        
        // 3. Return new state (optimistic update - instant UI)
        return { ...prev, todos: newTodos };
    });
};
```

---

### 3. **AI Integration**

Family Hub leverages **Google Gemini AI** for intelligent features:

```
┌──────────────────────────────────────────────────────────┐
│      User AI Prompt (Natural Language)                   │
│      e.g., "Create recipe from my fridge items"          │
└─────────────────────┬────────────────────────────────────┘
                      │
                      ▼
┌──────────────────────────────────────────────────────────┐
│          Build Context & Prepare Request                 │
│  • Current date/time                                     │
│  • Family members list                                   │
│  • Available categories                                  │
│  • Relevant data (inventory, events, etc.)              │
└─────────────────────┬────────────────────────────────────┘
                      │
                      ▼
┌──────────────────────────────────────────────────────────┐
│            Gemini AI API Call                            │
│                                                           │
│  Model Selection:                                        │
│  • gemini-2.5-flash (text, functions)                   │
│  • gemini-2.5-flash-image (image generation)            │
│                                                           │
│  Request Types:                                          │
│  ├─► Function Calling (Calendar Events)                 │
│  ├─► JSON Schema (Recipes, Routines)                    │
│  ├─► Image Generation (Event Covers)                    │
│  └─► Text Generation (Help Articles)                    │
└─────────────────────┬────────────────────────────────────┘
                      │
                      ▼
┌──────────────────────────────────────────────────────────┐
│          Process AI Response                             │
│  1. Validate structure                                   │
│  2. Extract data                                         │
│  3. Transform to app format                              │
└─────────────────────┬────────────────────────────────────┘
                      │
                      ▼
┌──────────────────────────────────────────────────────────┐
│          Update Application State                        │
│        (Follow normal data flow)                         │
│     → Optimistic Update → Firestore Write                │
└──────────────────────────────────────────────────────────┘
```

**AI Use Cases:**

1. **Calendar Event Generation**: "Soccer practice tomorrow at 3pm" → Structured event
2. **Recipe Generation**: Available ingredients → Recipe suggestions with instructions
3. **Routine Creation**: "Morning routine for kids" → Task checklist
4. **Image Generation**: Event title → AI-generated cover image
5. **Help Articles**: Generate/edit documentation content
6. **Image Analysis**: Extract text/data from uploaded images (OCR)

---

### 4. **Notification System**

Family Hub includes a **smart notification engine** that runs in the background:

```
┌──────────────────────────────────────────────────────────┐
│          Application Starts                              │
└─────────────────────┬────────────────────────────────────┘
                      │
                      ▼
┌──────────────────────────────────────────────────────────┐
│          NotificationEngine.start()                      │
│         (utils/notificationEngine.ts)                    │
└─────────────────────┬────────────────────────────────────┘
                      │
        ┌─────────────┴─────────────┐
        │                           │
        ▼                           ▼
┌───────────────────┐     ┌─────────────────────┐
│  Every 60 Seconds │     │  Every 60 Minutes   │
│  checkReminders() │     │  checkSuggestions() │
└────────┬──────────┘     └──────────┬──────────┘
         │                           │
         │                           │
         ▼                           ▼
┌───────────────────┐     ┌─────────────────────┐
│• Calendar Events  │     │• Weather Alerts     │
│• Todo Reminders   │     │• Air Quality Warns  │
│• Send Browser     │     │• Meal Prep Alerts   │
│  Notifications    │     │• Overdue Todos      │
└───────────────────┘     └─────────────────────┘
```

**Notification Types:**

1. **Event Reminders**: Configurable minutes before events start
2. **Todo Reminders**: Based on due date/time
3. **Weather Alerts**: Rain warnings, high UV index
4. **Air Quality Warnings**: Poor AQI notifications
5. **Meal Prep Reminders**: Time to thaw meat, prepare ingredients
6. **Overdue Tasks**: Notifications for missed deadlines

**Configuration**: Users can customize notification settings in `SettingsView`.

---

## 🎨 Core Features Explained

### **Homescreen (Dashboard)**

- **Customizable Widget Grid**: Drag-and-drop interface for arranging widgets
- **Responsive Layouts**: Different layouts for desktop, tablet, and mobile
- **Available Widgets**:
  - Weather, UV Index, Air Quality
  - Calendar (upcoming events)
  - Meal Plan (weekly meals)
  - Routines (progress tracking)
  - Todos (task overview)
  - Lists (shopping lists)
  - Leaderboard (family points)
  - Photo Slideshow (memories)
  - Sticky Notes (quick reminders)
  - Fridge (inventory preview)

### **Calendar**

- **Multiple Views**: Month, Week, Day
- **Event Types**: 
  - Regular events with start/end times
  - All-day events
  - Multi-day events
  - Recurring events (daily, weekly, monthly, yearly, custom)
- **AI Features**:
  - Natural language event creation
  - AI-generated cover images
  - Image-to-event conversion (OCR)
- **Member Assignment**: Assign events to specific family members
- **Categories**: Work, Personal, Family, Appointments, Celebrations
- **Reminders**: Customizable notification timings

### **Routines**

- **Daily Routines**: Create repeating task lists (e.g., morning routine, bedtime routine)
- **Task Checklists**: Multiple tasks per routine with point values
- **Progress Tracking**: Visual progress bars and completion status
- **Recurrence**: Daily, weekly, or specific days
- **AI Generation**: Generate routine suggestions from descriptions
- **Points System**: Earn points for completing tasks

### **Meal Planner**

- **Weekly Planning**: Plan meals for each day (breakfast, lunch, dinner, snacks)
- **Recipe Management**: Store recipes with ingredients and instructions
- **Fridge Integration**: Track inventory and expiry dates
- **AI Recipe Generator**: Generate recipes based on available ingredients
- **Shopping Lists**: Auto-generate shopping lists from recipes
- **Meal Types**: Categorize meals (breakfast, lunch, dinner, snack, dessert)

### **Todos**

- **Task Lists**: Create individual tasks with due dates
- **Recurrence**: Support for recurring todos
- **Member Assignment**: Assign tasks to family members
- **Categories**: Organize by category (work, personal, errands, etc.)
- **AI Cover Images**: Generate cover images for important tasks
- **Points**: Earn points for completing todos

### **Lists**

- **Multiple List Types**: Shopping lists, packing lists, general lists
- **Sub-items**: Add items with checkboxes
- **Collaborative**: All family members can add/check items
- **Member Assignment**: Assign list ownership

### **Fridge (Inventory)**

- **Item Tracking**: Track food items with quantities
- **Expiry Dates**: Monitor expiration dates
- **Categories**: Organize by type (dairy, meat, vegetables, etc.)
- **Low Stock Alerts**: Get notified when items are running low
- **Shopping List Integration**: Add items to shopping lists

### **Leaderboard & Gamification**

- **Points System**:
  - Weekly points (resets every week)
  - All-time points (lifetime total)
- **Point Sources**:
  - Completing todos
  - Finishing routines
  - Contributing to family activities
- **Leaderboard**: View family rankings
- **Weekly Reset**: Automatic reset every Monday

### **Rewards & Achievements**

- **Rewards Store**: Family can create custom rewards (e.g., "Pick movie night", "Extra screen time")
- **Point Redemption**: Spend earned points on rewards
- **Achievement System**:
  - Daily Streak & Instant Wins
  - Weekly Champion Awards
  - Special Achievement Awards
  - Teamwork & Attitude Awards
  - Grand Prize (Monthly/Long-Term) Awards
- **Admin Controls**: Admins can grant achievements manually

### **Profile**

- **Personal Information**: Name, avatar, date of birth, gender
- **Points Display**: View weekly and all-time points
- **Achievements**: See earned achievement badges
- **Role Management**: Owner, Admin, or Member roles

### **Settings**

- **Family Management**: Edit family name, manage members
- **Invite Code**: Generate/view invite codes for new members
- **Notification Settings**: Configure reminder preferences
- **Menu Customization**: Enable/disable navigation items
- **Data Management**: Export/import family data
- **Danger Zone**: Leave family, delete family data

### **Help Center**

- **Categorized Articles**: Browse help articles by category
- **Search**: Find relevant help content
- **AI Editing**: Generate or edit help articles with AI
- **Rich Text Editor**: Format help content with rich text

### **Media Gallery**

- **Photo Storage**: Upload and manage family photos
- **Gallery View**: Browse photos in grid layout
- **Image Editor**: Basic editing tools
- **Widget Integration**: Use photos in slideshow widgets

---

## 🔧 Configuration

### **Environment Variables**

Create a `.env.local` file:

```env
# Required: Google Gemini AI API Key
GEMINI_API_KEY=your_gemini_api_key_here
```

### **Firebase Configuration**

Update `firebase.ts` with your Firebase project credentials:

```typescript
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT.firebasestorage.app",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID",
  measurementId: "YOUR_MEASUREMENT_ID"
};
```

### **Firestore Database Structure**

```
firestore/
├── families/{familyId}           # Main family document
│   ├── familyName: string
│   ├── familyMembers: FamilyMember[]
│   ├── calendarEvents: CalendarEvent[]
│   ├── todos: Todo[]
│   ├── lists: ListItem[]
│   ├── routines: Routine[]
│   ├── recipes: Recipe[]
│   ├── inventory: InventoryItem[]
│   ├── mealPlan: MealPlan
│   ├── rewards: Reward[]
│   ├── achievements: Achievement[]
│   ├── widgetLayouts: {...}
│   ├── notifications: NotificationItem[]
│   └── ...
│
├── users/{userId}                # User-specific data
│   ├── familyId: string
│   ├── currentViewId: string
│   ├── darkMode: boolean
│   └── notificationSettings: {...}
│
├── global_data/help_center       # Shared help articles
│   ├── articles: HelpArticle[]
│   └── categories: Category[]
│
└── counters/families             # Family ID counter
    └── count: number
```

### **Firebase Storage Structure**

```
storage/
├── covers/{imageId}.webp         # AI-generated event/todo covers
└── media/{familyId}/{mediaId}    # User-uploaded media
```

---

## 👨‍💻 Development Guide

### **Project Setup**

1. **Install dependencies**:
   ```bash
   npm install
   ```

2. **Run development server**:
   ```bash
   npm run dev
   ```
   Open `http://localhost:3000`

3. **Build for production**:
   ```bash
   npm run build
   ```

4. **Preview production build**:
   ```bash
   npm run preview
   ```

### **Code Structure Guidelines**

- **Components**: Place feature components in respective folders (`components/calendar/`, `components/routines/`, etc.)
- **Shared Components**: Place reusable components directly in `components/`
- **Utilities**: Place helper functions in `utils/`
- **Types**: Define TypeScript interfaces in `types.ts`
- **Constants**: Define default values and configurations in `constants.tsx`

### **State Management**

Family Hub uses a **centralized state pattern**:

- `App.tsx` is the **single source of truth** for application state
- State is passed down to components via props
- Components update state via callback functions
- All state changes trigger Firestore writes for synchronization

**Example:**

```typescript
// In App.tsx
const [appState, setAppState] = useState<AppState | null>(null);

// Setter functions for specific data types
const setTodos = (updater: React.SetStateAction<Todo[]>) => {
    setAppState(prev => {
        if (!prev) return null;
        const newTodos = typeof updater === 'function' 
            ? updater(prev.todos) 
            : updater;
        updateFamilyData({ todos: newTodos });
        return { ...prev, todos: newTodos };
    });
};

// Pass to components
<TodosView todos={appState.todos} setTodos={setTodos} />
```

### **Adding New Features**

1. **Define Types**: Add TypeScript interfaces to `types.ts`
2. **Create Component**: Create new component in appropriate folder
3. **Update Constants**: Add default values to `constants.tsx`
4. **Update App.tsx**: Integrate component into main app
5. **Add Navigation**: Update `navConfig` if adding a new view

---

## 🚢 Deployment

### **Google Cloud Run**

Family Hub is deployed on **Google Cloud Run**, providing serverless, scalable hosting with automatic HTTPS and global CDN.

**Live Application**: [https://family-hub-884439437269.us-west1.run.app/](https://family-hub-884439437269.us-west1.run.app/)

### **Deployment Architecture**

```
┌─────────────────────────────────────────────────────────┐
│                    Google Cloud Run                      │
│              (Containerized React App)                   │
│         https://family-hub-*.us-west1.run.app           │
└─────────────────┬───────────────────────────────────────┘
                  │
        ┌─────────┴─────────┬─────────────┬──────────────┐
        ▼                   ▼             ▼              ▼
  ┌──────────┐      ┌──────────┐   ┌──────────┐  ┌──────────┐
  │ Firebase │      │ Firebase │   │ Firebase │  │  Gemini  │
  │Firestore │      │   Auth   │   │ Storage  │  │   AI     │
  └──────────┘      └──────────┘   └──────────┘  └──────────┘
```

### **Why Cloud Run?**

- **Serverless**: No server management required
- **Auto-scaling**: Scales from zero to handle any traffic
- **Cost-effective**: Pay only for actual usage
- **Global**: Fast delivery worldwide with automatic CDN
- **HTTPS**: Automatic SSL certificates
- **Container-based**: Consistent environments across dev and production

### **Environment-Specific Configurations**

For production deployments:
- Update Firebase security rules
- Configure Firebase Storage CORS
- Set up Firebase Authentication domains
- Enable Firebase Analytics
- Configure service worker caching strategies
- Set up Cloud Run environment variables for API keys

---

## 📄 License

This project is open source and available under the MIT License.

---

## 📞 Support

For questions or issues:
- 📖 Check the **Help Center** within the app
- 🐛 Report bugs via GitHub Issues
- 💬 Join community discussions

---

## 🙏 Acknowledgments

- **Google Gemini AI** - Powering intelligent features
- **Firebase** - Backend infrastructure and real-time sync
- **React** - UI framework
- **Vite** - Lightning-fast build tool
- **Open-Meteo** - Weather data API
- **Tailwind CSS** - Utility-first styling

---

<div align="center">
  <p>Made with ❤️ for families everywhere</p>
  <p>⭐ Star this repo if you find it useful!</p>
</div>
