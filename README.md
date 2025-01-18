# Groq App Generator

An interactive web application that generates and modifies web applications using Groq's LLM API. Built with Next.js and TypeScript.

## Features

- Real-time app generation based on natural language queries
- Content safety checking using LlamaGuard
- Interactive feedback system for iterative improvements
- Version control and history tracking
- Share and export functionality

## Tech Stack

- Next.js 14 (App Router)
- TypeScript
- Groq SDK
- React Syntax Highlighter
- UUID for session management

## Environment Variables

Required environment variables:
- `GROQ_API_KEY`: Your Groq API key

## Getting Started

1. Clone the repository
2. Install dependencies: `npm install`
3. Set up your environment variables
4. Run the development server: `npm run dev`

The application will be available at `http://localhost:3000`.

## How It Works

The `groq-appgen` repository is an interactive web application that generates and modifies web applications using Groq's LLM (Large Language Model) API. The application is built with Next.js and TypeScript, and it includes several key features such as real-time app generation, content safety checking, an interactive feedback system, version control, and share/export functionality.

### Key Components:
1. **Next.js (App Router):**
   - Handles routing and server-side rendering.
2. **TypeScript:**
   - Provides type safety and enhances code quality.
3. **Groq SDK:**
   - Interacts with Groq's LLM API for generating and modifying web applications.
4. **React Syntax Highlighter:**
   - Used for syntax highlighting in the code editor.
5. **UUID for Session Management:**
   - Manages user sessions uniquely.

## Architecture Diagrams

### Overall Architecture:
```mermaid
graph TD
    A[User] -->|Interacts with| B[Web Application]
    B -->|Uses| C[Groq's LLM API]
    C -->|Hosted on| D[Servers]
    B -->|Checks| E[LlamaGuard for Content Safety]
    B -->|Provides| F[Interactive Feedback System]
    B -->|Tracks| G[Version Control and History]
    B -->|Includes| H[Share and Export Functionality]
    B -->|Frontend| I[Next.js + TypeScript]
    B -->|Backend| J[Groq SDK]
    B -->|Manages| K[Session with UUID]
    subgraph Session Management
        K
    end
    subgraph Frontend
        I[Next.js] --> L[TypeScript]
    end
    subgraph Backend
        J --> M[Groq SDK]
    end
    subgraph Infrastructure
        D[Servers] --> N[Database]
    end
```

### Component Interaction:
```mermaid
graph TD
    A[MainView Component] -->|Renders| B[StudioView Component]
    A -->|Renders| C[PromptView Component]
    B -->|Uses| D[useStudio Hook]
    B -->|Includes| E[PromptInput Component]
    B -->|Includes| F[VersionSwitcher Component]
    B -->|Includes| G[NewButton Component]
    B -->|Includes| H[OptionsButton Component]
    B -->|Includes| I[ShareButton Component]
    B -->|Includes| J[ReloadButton Component]
    B -->|Includes| K[CopyButton Component]
    C -->|Uses| D
```

### Data Flow:
```mermaid
graph TD
    A[User Input] -->|Triggers| B[PromptInput Component]
    B -->|Sends Request to| C[Groq's LLM API]
    C -->|Processes Request and Returns| D[Generated HTML Code]
    D -->|Displayed in| E[StudioView Component]
    E -->|Updates| F[History and Version Control]
    F -->|Provides Feedback to| G[Interactive Feedback System]
    G -->|Updates| H[Generated HTML Code]
    H -->|Displayed in| E
```

You can explore more details and view additional files in the [repository](https://github.com/andiekobbietks/groq-appgen).

If you need further details or additional diagrams, please let me know!

```mermaid
architecture-beta
    group infrastructure(cloud)[Infrastructure]
        service dns(server)[Route53] in infrastructure
        service cdn(cloud)[CloudFront] in infrastructure
        service app_server(server)[ApplicationServer] in infrastructure
        service db(database)[Database] in infrastructure

    group frontend(cloud)[Frontend]
        service nextjs(code)[NextJS] in frontend
        service ts(code)[TypeScript] in frontend

    group backend(cloud)[Backend]
        service groq_sdk(code)[GroqSDK] in backend
        service session_manager(server)[SessionManager] in backend
        service content_guard(internet)[LlamaGuard] in backend

    group features(cloud)[Features]
        service feedback(server)[InteractiveFeedbackSystem] in features
        service version_control(server)[VersionControl] in features
        service sharing(server)[SharingExport] in features

    group user_interaction(cloud)[UserInteraction]
        service user(internet)[User] in user_interaction

    user:R --> L:dns
    dns:R --> L:cdn
    cdn:R --> L:app_server
    app_server:R --> L:nextjs
    nextjs:R --> L:ts
    nextjs:B -- T:groq_sdk
    groq_sdk:R --> L:session_manager
    groq_sdk:R --> L:content_guard
    groq_sdk:R --> L:db
    ts:R --> L:feedback
    feedback:R --> L:version_control
    version_control:R --> L:sharing
    feedback:B -- T:groq_sdk
```

To ensure the diagrams work on GitHub, we need to follow GitHub's Markdown syntax for Mermaid diagrams. Here’s how you can format the two simplified diagrams to work on GitHub:

### **Diagram 1: Infrastructure and Frontend**
This diagram focuses on the Infrastructure and Frontend components and their interactions.

```mermaid
architecture-beta
    group infrastructure(cloud)[Infrastructure]
        service dns(server)[Route53] in infrastructure
        service cdn(cloud)[CloudFront] in infrastructure
        service app_server(server)[ApplicationServer] in infrastructure
        service db(database)[Database] in infrastructure

    group frontend(cloud)[Frontend]
        service nextjs(code)[NextJS] in frontend
        service ts(code)[TypeScript] in frontend

    group user_interaction(cloud)[UserInteraction]
        service user(internet)[User] in user_interaction

    user:R --> L:dns
    dns:R --> L:cdn
    cdn:R --> L:app_server
    app_server:R --> L:nextjs
    nextjs:R --> L:ts
```

### **Diagram 2: Backend and Features**

This diagram focuses on the **Backend** and **Features** components and their interactions.

```mermaid
architecture-beta
    group backend(cloud)[Backend]
        service groq_sdk(code)[GroqSDK] in backend
        service session_manager(server)[SessionManager] in backend
        service content_guard(internet)[LlamaGuard] in backend

    group features(cloud)[Features]
        service feedback(server)[InteractiveFeedbackSystem] in features
        service version_control(server)[VersionControl] in features
        service sharing(server)[SharingExport] in features

    nextjs:B -- T:groq_sdk
    groq_sdk:R --> L:session_manager
    groq_sdk:R --> L:content_guard
    groq_sdk:R --> L:db
    ts:R --> L:feedback
    feedback:R --> L:version_control
    version_control:R --> L:sharing
    feedback:B -- T:groq_sdk
```


