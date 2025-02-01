# Important commands

## Terminate a running process

Check the running process and terminate

### Windows Commands

```text
netstat -ano | findstr :port
taskkill /PID <PID> /F
```

### Linux/macOS Commands

```text
lsof -i :port
kill -9 <PID>
```
