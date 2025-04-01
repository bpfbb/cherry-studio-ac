# Electron Architecture Documentation

## Overview
Cherry Studio is built as an Electron application, which enables it to run as a cross-platform desktop application on Windows, macOS, and Linux. This document outlines the key components and configuration that make this possible.

## Key Electron Components

### Build System
- **electron-vite**: Used for development and building the application
- **electron-builder**: Handles packaging the app for various platforms
- **Build Scripts**: Specialized scripts for building on Windows, macOS, and Linux platforms
- **Configuration Files**: 
  - `electron-builder.yml`: Defines packaging configuration
  - `electron.vite.config.ts`: Configuration for electron-vite build process

### Application Structure
The application follows the standard Electron architecture with:

1. **Main Process** (`src/main/`)
   - Entry point: `src/main/index.ts`
   - Window management: `src/main/services/WindowService.ts`
   - Tray support: `src/main/services/TrayService.ts`
   - IPC communication: `src/main/ipc.ts`
   - Protocol handling: `src/main/services/ProtocolClient.ts`

2. **Renderer Process** (`src/renderer/`)
   - Web-based UI that runs in the Electron window
   - Communicates with the main process via IPC

3. **Preload Scripts** (`src/preload/`)
   - Bridge between main and renderer processes
   - Expose selective Electron APIs to the renderer

### Platform-Specific Features
- Customized builds for Windows, macOS, and Linux
- Platform detection: `window.electron?.process?.platform`
- Platform-specific window management and UI adjustments
- Auto-updates via `AppUpdater` service

### Configuration and Settings
- App configuration through `ConfigManager`
- System integration options:
  - Launch on boot
  - Launch to tray
  - System tray integration
  - Close to tray behavior

## Building the Application
To build the application for different platforms:

- Windows: `npm run build:win` or `npm run build:win:x64`
- macOS: `npm run build:mac`, `npm run build:mac:arm64`, or `npm run build:mac:x64`
- Linux: `npm run build:linux`, `npm run build:linux:arm64`, or `npm run build:linux:x64`

## Development
For development:
- `npm run dev`: Start the application in development mode
- `npm run start`: Preview the built application

## Packaging
The application is packaged as a standalone executable with all dependencies bundled, creating a native-like experience on each supported platform. 