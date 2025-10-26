# Monorepo Learning Project

<a alt="Nx logo" href="https://nx.dev" target="_blank" rel="noreferrer"><img src="https://raw.githubusercontent.com/nrwl/nx/master/images/nx-logo.png" width="45"></a>

A learning project to practice **monorepo architecture** using [Nx](https://nx.dev), featuring two applications that share code and tooling.

## 🎯 Project Overview

This repository demonstrates a monorepo setup with:

- **Next.js App** (`sso`) - Server-side rendered web application
- **React Native App** (`mobile`) - Cross-platform mobile application (iOS/Android/Web)
- **Shared tooling** - ESLint, TypeScript, Jest, and CI/CD configuration
- **Code sharing** - Ability to create shared libraries used by both apps

## 🚀 Getting Started

### Prerequisites

- Node.js 20+ and npm
- For React Native development:
  - **Android**: Android Studio and Android SDK
  - **iOS**: Xcode (macOS only)

### Installation

```bash
npm install
```

## 📱 Running the Applications

### Next.js App (SSO)

```bash
# Development server
npx nx dev sso

# Production build
npx nx build sso

# Start production server
npx nx start sso
```

Open [http://localhost:4200](http://localhost:4200) in your browser.

### React Native App (Mobile)

#### Web Development (Fastest)

```bash
# Run as web app (fastest for development)
npx nx dev mobile
# Open http://localhost:4200
```

#### Android Development (Local)

**Prerequisites:**

- Android Studio installed with Android SDK
- Android emulator configured or physical device connected

**Steps:**

1. **Start Metro bundler** (in one terminal):

```bash
cd apps/mobile
npx metro start
```

2. **Run the app** (in another terminal):

```bash
cd apps/mobile
npx react-native run-android
```

**Alternative: Using Android Studio**

1. Start Metro bundler:

```bash
cd apps/mobile
npx metro start
```

2. Open `apps/mobile/android` folder in Android Studio

3. Wait for Gradle sync to complete

4. Click the green **Run** button to launch the app on emulator/device

5. If you get "Unable to load script" error, run:

```bash
adb reverse tcp:8081 tcp:8081
```

#### iOS Development (macOS only)

```bash
# Run on iOS simulator
npx nx run-ios mobile

# Build for iOS
npx nx build-ios mobile
```

## 🛠️ Development Commands

### Running Tasks

```bash
# Run tests for all projects
npx nx run-many -t test

# Lint all projects
npx nx run-many -t lint

# Build all projects
npx nx run-many -t build

# Type-check all projects
npx nx run-many -t typecheck
```

### Project Information

```bash
# See all available commands for a project
npx nx show project sso
npx nx show project mobile

# Visualize project dependencies
npx nx graph

# List all projects
npx nx show projects
```

## 📦 Adding Shared Libraries

Create shared libraries that both apps can use:

```bash
# Create a shared utilities library
npx nx g @nx/js:lib shared-utils

# Create a shared React component library
npx nx g @nx/react:lib shared-ui

# Create a shared React Native component library
npx nx g @nx/react-native:lib mobile-ui
```

Then import from these libraries:

```typescript
// In both apps
import { someUtil } from '@org/shared-utils';
import { Button } from '@org/shared-ui';
```

## 🏗️ Project Structure

```
org/
├── apps/
│   ├── sso/              # Next.js application
│   └── mobile/           # React Native application
├── libs/                 # Shared libraries (create as needed)
├── .github/
│   └── workflows/
│       └── ci.yml        # CI/CD pipeline
├── nx.json               # Nx configuration
├── package.json          # Dependencies
└── tsconfig.base.json    # Shared TypeScript config
```

## 🔧 Tech Stack

- **Build System**: [Nx](https://nx.dev)
- **Web Framework**: [Next.js 15](https://nextjs.org)
- **Mobile Framework**: [React Native 0.79](https://reactnative.dev)
- **UI Library**: [React 19](https://react.dev)
- **Language**: [TypeScript](https://www.typescriptlang.org)
- **Styling**: [Tailwind CSS](https://tailwindcss.com)
- **Testing**: [Jest](https://jestjs.io)
- **Linting**: [ESLint](https://eslint.org)
- **CI/CD**: GitHub Actions

## 📚 Learning Resources

### Nx Documentation

- [Nx Overview](https://nx.dev/getting-started/intro)
- [Module Boundaries](https://nx.dev/features/enforce-module-boundaries)
- [Task Pipeline](https://nx.dev/concepts/task-pipeline-configuration)

### Next.js

- [Next.js Documentation](https://nextjs.org/docs)
- [App Router Guide](https://nextjs.org/docs/app)

### React Native

- [React Native Docs](https://reactnative.dev/docs/getting-started)
- [Nx React Native Plugin](https://nx.dev/nx-api/react-native)

## 🎓 Learning Goals

This project helps practice:

- ✅ Monorepo architecture and tooling
- ✅ Code sharing between web and mobile
- ✅ Build system optimization with Nx
- ✅ CI/CD pipeline configuration
- ✅ Cross-platform development
- ✅ TypeScript in a large codebase
- ✅ Dependency management in workspaces

## 🤝 Contributing

This is a personal learning project, but feel free to:

- Open issues for questions or discussions
- Submit PRs with improvements or fixes
- Fork it for your own learning!

## 📄 License

MIT

---

**Happy Learning!** 🚀
