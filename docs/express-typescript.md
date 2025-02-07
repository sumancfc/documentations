# Add Typescript in an Express Project

## Install `TypeScript` and type definitions:

```bash
   npm install -D typescript @types/node @types/express ts-node @ts-node-dev
```

## Generate a `tsconfig.json` file:

```bash
   npx tsc --init
```

## Configure `tsconfig.json`:
```json
  {
    "compilerOptions": {
      "target": "ES6",
      "module": "commonjs",
      "outDir": "./dist",
      "rootDir": "./src",
      "strict": true,
      "esModuleInterop": true
    },
    "include": ["src/**/*"],
    "exclude": ["node_modules"]
  }
```

## Create a `src` folder and add an `index.ts` or `server.ts` file:
```typescript
  import express, { Express, Request, Response } from 'express';

  const app: Express = express();
  const port: number = 3000;
  
  app.get('/', (req: Request, res: Response) => {
    res.send('Hello, TypeScript Express!');
  });
  
  app.listen(port, () => {
    console.log(`Server running at http://localhost:${port}`);
  });
```

## Update `package.json` scripts:
```json
  "scripts": {
    "build": "tsc",
    "start": "node dist/index.js",
    "dev": "ts-node-dev --respawn --transpile-only src/index.ts"
  }
```

## Run the development server
```bash
  npm run dev
```

## Build the program
```bash
  npm run build
```

## Start the program
```bash
  npm start
```
