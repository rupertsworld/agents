## User interface

Keep UI components light. Use services to abstract away functionality. UI components should only listen to events, update UI, and send actions to services.

## Testing

Use vitest. Keep test scripts simple and direct in `package.json` — no shell script wrappers:

```json
{
  "scripts": {
    "type-check": "tsc --noEmit",
    "test": "vitest run",
    "test:watch": "vitest"
  }
}
```
