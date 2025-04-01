# Learner's directive

## Cherry Studio: Project Overview

Cherry Studio is a cross-platform AI assistant desktop application built with Electron and React. It serves as a powerful AI-powered productivity tool with multiple specialized features.

## Core Architecture

### Electron Application Structure

The application follows the standard Electron architecture:

1. **Main Process (`src/main/`)**: 
   - Controls application lifecycle, window management, and system integration
   - Manages IPC communication between renderer and main processes
   - Handles system-level features like the system tray, protocol registration, etc.

2. **Renderer Process (`src/renderer/src/`)**: 
   - Implements the React-based UI
   - Manages application state with Redux
   - Handles user interactions and UI rendering

3. **Preload Scripts (`src/preload/`)**: 
   - Bridge between main and renderer processes
   - Expose selective Electron APIs securely to the renderer

### Key Technologies

- **Frontend**: React, React Router, Redux, styled-components, Ant Design
- **Database**: IndexedDB via Dexie.js for client-side storage
- **AI Integration**: Support for multiple AI providers (OpenAI, Anthropic, Gemini)
- **Build System**: electron-vite for development and building
- **Packaging**: electron-builder for distribution

## Main Features

The application is organized into several core features:

1. **Chat Interface (`/home`)**: 
   - Conversational UI for interacting with AI assistants
   - Support for multiple topics/conversations
   - Real-time streaming responses from AI models

2. **AI Agents (`/agents`)**: 
   - Specialized AI assistants for different tasks
   - Customizable agent behaviors and capabilities

3. **AI Image Generation (`/paintings`)**: 
   - Create images using AI models
   - Manage and organize generated images

4. **Translation Service (`/translate`)**: 
   - AI-powered text translation
   - Support for multiple languages

5. **File Management (`/files`)**: 
   - Upload and manage files
   - Process various file types (PDF, Office documents, etc.)

6. **Knowledge Base (`/knowledge`)**: 
   - Store and organize information
   - AI-powered knowledge retrieval

7. **Applications (`/apps`)**: 
   - Mini-applications built on the platform
   - Extend functionality beyond core features

8. **Settings (`/settings`)**: 
   - Configure application behavior
   - Manage AI provider connections
   - Customize UI preferences
   - Backup and restore user data

## Data Architecture

1. **Local Database (IndexedDB)**:
   - Files: Store file metadata
   - Topics: Store conversation history
   - Settings: Store application configuration
   - Knowledge Notes: Store knowledge base items
   - Translation History: Store translation records

2. **Redux Store**:
   - LLM: AI provider configurations and model settings
   - Messages: Chat history and message state
   - Settings: Application preferences
   - Agents: Agent configurations
   - Assistants: Assistant configurations
   - Knowledge: Knowledge base management
   - And various other feature-specific states

## AI Integration

The application supports multiple AI providers through a unified interface:

1. **Provider System**:
   - Base provider implementation (`BaseProvider`)
   - Specific provider implementations:
     - OpenAI (`OpenAIProvider`)
     - Anthropic (`AnthropicProvider`)
     - Gemini (`GeminiProvider`)

2. **AI Services**:
   - Text generation (chat completions)
   - Image generation
   - Text embedding
   - Translation
   - Summarization
   - Suggestions

## Cross-platform Support

The application is designed to run on:
- Windows
- macOS
- Linux

With platform-specific adaptations for:
- Window management
- System integration (tray, shortcuts)
- Installation procedures

## Development and Build Process

The project uses:
- `electron-vite` for development
- `electron-builder` for packaging
- Custom scripts for versioning and release management
- Comprehensive TypeScript type definitions
- ESLint and Prettier for code formatting

## Backup and Restore

The application includes features for:
- Local data backup
- WebDAV-based cloud backup
- Import/export functionality

This architecture creates a powerful, extensible platform for AI-powered desktop applications with a rich set of features and integrations.
