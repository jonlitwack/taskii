# Server-Sent Events Real-Time Updates

---
type: Architecture
c4_level: Component
created: 2025-10-16
last_updated: 2025-10-16
status: active
---

## Title

Server-Sent Events (SSE) Real-Time Updates System

## Description

The Server-Sent Events system enables real-time communication between the server and connected clients, allowing instant updates to the todo list when new items are created. This provides a seamless user experience where changes made through the CopilotKit interface are immediately reflected across all connected browser sessions without requiring manual page refreshes.

## Architecture Overview

The SSE implementation consists of three main components:

1. **SSE API Endpoint** (`/api/todos/events/route.ts`) - Manages client connections and broadcasts events
2. **Event Broadcasting** - Server-side function to send events to all connected clients
3. **Client Event Listener** (`TodoList.tsx`) - Frontend component that listens for and handles real-time events

## Backend Implementation

### SSE API Route Structure

```typescript
// /src/app/api/todos/events/route.ts
import { NextRequest } from 'next/server';

// Store active SSE connections
const clients = new Set<ReadableStreamDefaultController>();
```

### Connection Management

The SSE endpoint handles client connections using a ReadableStream:

```typescript
export async function GET(request: NextRequest) {
  const stream = new ReadableStream({
    start(controller) {
      clients.add(controller);
      // Send initial connection message
      const data = `data: ${JSON.stringify({ type: 'connected' })}\n\n`;
      controller.enqueue(new TextEncoder().encode(data));
    }
  });

  return new Response(stream, {
    headers: {
      'Content-Type': 'text/event-stream',
      'Cache-Control': 'no-cache',
      'Connection': 'keep-alive',
      'Access-Control-Allow-Origin': '*',
      'Access-Control-Allow-Headers': 'Cache-Control',
    },
  });
}
```

### Event Broadcasting

The `broadcastTodoCreated` function sends events to all connected clients:

```typescript
export function broadcastTodoCreated(todo: any) {
  const data = `data: ${JSON.stringify({
    type: 'todo_created',
    todo: todo
  })}\n\n`;

  const encodedData = new TextEncoder().encode(data);

  for (const controller of clients) {
    try {
      controller.enqueue(encodedData);
    } catch (error) {
      clients.delete(controller);
    }
  }
}
```

## Frontend Implementation

### EventSource Connection

The TodoList component establishes an SSE connection on mount:

```tsx
// /src/components/TodoList.tsx
useEffect(() => {
  const eventSource = new EventSource('/api/todos/events');

  eventSource.onopen = () => {
    setConnected(true);
  };

  eventSource.onmessage = (event) => {
    const data = JSON.parse(event.data);
    if (data.type === 'connected') {
      setConnected(true);
    } else if (data.type === 'todo_created') {
      fetchTodos(); // Refresh the todo list
    }
  };

  eventSource.onerror = (error) => {
    setConnected(false);
  };

  return () => {
    eventSource.close();
  };
}, []);
```

## Integration Points

### CopilotKit Integration

When a todo is created via CopilotKit, the system broadcasts the event:

```typescript
// In CopilotKit action handler
const todo = await prisma.todo.create({ data: { title } });
broadcastTodoCreated({
  id: todo.id,
  title: todo.title,
  done: todo.done,
  createdAt: todo.createdAt,
});
```

## Event Types

The SSE system currently supports two event types:

1. **`connected`** - Sent when a client successfully connects to the SSE stream
2. **`todo_created`** - Broadcast when a new todo item is created, containing the todo data

## Connection Management

- **Connection Storage**: Active connections are stored in a `Set` of ReadableStream controllers
- **Automatic Cleanup**: Disconnected clients are automatically removed from the set
- **Error Handling**: Failed broadcasts don't crash the server; disconnected clients are cleaned up
- **CORS Support**: Headers allow cross-origin connections for development flexibility

## Performance Considerations

- **Memory Management**: Client connections are tracked in memory using a Set
- **Scalability**: Current implementation is suitable for small to medium applications
- **Connection Limits**: No explicit connection limits; relies on browser and server constraints
- **Event Frequency**: Events are only sent when todos are created, minimizing server load

## Browser Support

- **Modern Browsers**: Full support for EventSource API
- **Fallback**: No fallback mechanism implemented; assumes modern browser support
- **Connection Recovery**: Basic error handling; could be enhanced with reconnection logic

## Security Considerations

- **Origin Control**: CORS headers allow all origins (`*`) for development
- **Data Exposure**: Only todo data is broadcast; no sensitive information included
- **Connection Security**: Uses standard HTTP/HTTPS; no additional authentication on SSE endpoint

## Error Handling

- **Client Disconnection**: Gracefully handles client disconnects without server errors
- **Parse Errors**: Frontend includes try-catch for malformed event data
- **Connection Failures**: Logs errors but doesn't implement automatic reconnection

## Future Enhancements

Potential improvements for the SSE system:

- **Authentication**: Add user-specific event filtering
- **Event Types**: Support for todo updates, deletions, and status changes
- **Connection Pooling**: Implement connection limits and management
- **Message Queuing**: Add Redis or similar for horizontal scaling
- **Heartbeat**: Periodic ping messages to detect stale connections

## Dependencies

- **Built-in APIs**: Uses native Web APIs (EventSource, ReadableStream)
- **No External Libraries**: Pure Node.js/Next.js implementation

## Testing

The SSE system can be tested by:

1. Opening multiple browser tabs/windows
2. Creating todos via CopilotKit in one tab
3. Observing real-time updates in other tabs
4. Monitoring browser developer tools for SSE connection status

## Related Components

- [CopilotKit Integration](./03-copilotkit-integration.md) - Uses SSE for real-time updates
- [TodoList Component](../../components/TodoList.md) - Consumes SSE events
- [Database Layer](./02-prisma-database-layer.md) - Data persistence layer</content>
