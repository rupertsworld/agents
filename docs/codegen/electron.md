# Electron

Use native TypeScript for Node & Electron, not JS building.

## IPC

Use `@rupertsworld/electron-ipc` for all main↔renderer communication. Do not use `ipcMain.handle`/`ipcRenderer.invoke` directly.

The pattern is:

1. Define a shared service interface extending `IPCService<Events>` in a shared module
2. Implement and register it in main with `createIPCService(name, ServiceClass)`
3. Call `enableIPCServiceBridge()` in preload
4. Resolve in renderer with `resolveIPCService<IMyService>(name)` — calls become async, events are typed

See the package README for full usage: https://github.com/rupertsworld/electron-ipc
