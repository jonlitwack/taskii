# CopilotKit Integration

---
type: Architecture
c4_level: Component
created: 2025-10-16
last_updated: 2025-10-16
status: active
---

## Title

CopilotKit Runtime Integration

## Description

CopilotKit provides AI-powered conversational interfaces and actions for the task management application. The integration enables users to interact with the application through natural language commands, specifically for creating and managing todo items.

## Architecture Overview

The CopilotKit integration consists of three main components:

1. **Backend Runtime** (`/api/copilotkit/route.ts`) - Defines available actions and handles AI model communication
2. **Frontend Provider** (`layout.tsx`) - Wraps the application with CopilotKit context
3. **UI Components** (`page.tsx`) - Provides the conversational sidebar interface

## Backend Implementation

### API Route Structure

```typescript
// /src/app/api/copilotkit/route.ts
import {
  CopilotRuntime,
  OpenAIAdapter,
  copilotRuntimeNextJSAppRouterEndpoint,
} from '@copilotkit/runtime';
```

### Available Actions

The CopilotKit runtime exposes two main actions:

#### `createTodo`
- **Purpose**: Creates a new todo item in the database
- **Parameters**:
  - `title` (string, required): The title of the todo item
- **Functionality**:
  - Creates a new todo record using Prisma
  - Broadcasts the creation event via Server-Sent Events
  - Returns the created todo data

#### `listTodos`
- **Purpose**: Retrieves all todo items from the database
- **Parameters**: None
- **Functionality**:
  - Fetches all todos ordered by creation date (newest first)
  - Returns formatted todo data

### Configuration

The runtime requires Azure OpenAI configuration:

```typescript
const apiKey = process.env["AZURE_OPENAI_API_KEY"];
const endpoint = process.env["AZURE_OPENAI_ENDPOINT"];
const model = process.env["MODEL_NAME"] || "gpt-4.1";
```

## Frontend Implementation

### Provider Setup

The application is wrapped with the CopilotKit provider in the root layout:

```tsx
// /src/app/layout.tsx
import { CopilotKit } from "@copilotkit/react-core";
import "@copilotkit/react-ui/styles.css";

export default function RootLayout({ children }) {
  return (
    <html lang="en">
      <body>
        <CopilotKit runtimeUrl="/api/copilotkit">
          {/* Application content */}
        </CopilotKit>
      </body>
    </html>
  );
}
```

### UI Integration

The CopilotKit sidebar is integrated on the main page:

```tsx
// /src/app/page.tsx
import { CopilotSidebar } from "@copilotkit/react-ui";

export default function Home() {
  return (
    <CopilotSidebar
      defaultOpen={true}
      instructions={"You are assisting the user as best as you can. Answer in the best way possible given the data you have."}
      labels={{
        title: "Sidebar Assistant",
        initial: "How can I help you today?",
      }}
    >
      {/* Page content */}
    </CopilotSidebar>
  );
}
```

## Real-time Updates

The integration leverages Server-Sent Events for real-time updates:

1. When a todo is created via CopilotKit, the `createTodo` action broadcasts the event
2. The frontend TodoList component listens for these events via EventSource
3. The todo list automatically refreshes when new items are created

## Dependencies

```json
{
  "@copilotkit/react-core": "^1.10.6",
  "@copilotkit/react-ui": "^1.10.6",
  "@copilotkit/runtime": "^1.10.6"
}
```

## Environment Variables

Required environment variables for CopilotKit functionality:

- `AZURE_OPENAI_API_KEY`: Azure OpenAI API key
- `AZURE_OPENAI_ENDPOINT`: Azure OpenAI endpoint URL
- `MODEL_NAME`: Model deployment name (defaults to "gpt-4.1")

## Error Handling

The API route includes error handling for missing configuration:

- Returns HTTP 500 with descriptive error message when Azure OpenAI credentials are not configured
- Gracefully handles database operation failures
- Provides user feedback through the CopilotKit interface

## Usage Examples

Users can interact with the application using natural language commands such as:

- "Create a todo item to buy groceries"
- "Add a task to finish the project report"
- "Show me all my todos"
- "List my current tasks"

## Security Considerations

- API keys are stored as environment variables
- No sensitive data is exposed through the CopilotKit actions
- Actions are limited to read/write operations on todo items only

## Performance Notes

- Actions are executed synchronously for immediate feedback
- Real-time updates ensure UI consistency across sessions
- Azure OpenAI integration provides reliable AI responses

## Related Components

- [TodoList Component](../components/TodoList.md) - Displays and manages todo items
- [Database Layer](./02-prisma-database-layer.md) - Data persistence
- [Server-Sent Events](./04-sse-real-time-updates.md) - Real-time communication</content>
