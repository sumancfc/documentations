# Important commands

## Terminate a running process

### Check the running process and terminate

- Windows

```sh
netstat -ano | findstr :port
taskkill /PID <PID> /F
```

- Linux/macOS

```sh
lsof -i :port
kill -9 <PID>
```
