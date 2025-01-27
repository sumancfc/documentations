# Swagger API Documentation Setup

This guide explains how to integrate Swagger API documentation into your Node.js Express.js project.

## Prerequisites

Ensure you have the following installed and configured:

1. **Node.js** (LTS version recommended)
2. **Express.js**
3. **TypeScript** (if applicable to your project)
4. **Swagger UI** package


## Installation

1. Install the necessary packages for Swagger integration:

   ```bash
   npm install swagger-jsdoc swagger-ui-express
   ```

## Configuration

1. Create a `swagger.ts` (or `swagger.js` if not using TypeScript) file in your project for Swagger configuration.

   **Example for `swagger.ts`:**

   ```typescript
   import swaggerJsdoc from 'swagger-jsdoc';
   import swaggerUi from 'swagger-ui-express';
   import { Express } from 'express';

   const options = {
     definition: {
       openapi: '3.0.0',
       info: {
         title: 'API Documentation',
         version: '1.0.0',
         description: 'A simple API documentation',
       },
       servers: [
         {
           url: 'http://localhost:3000',
         },
       ],
     },
     apis: ['./src/routes/*.ts'], // Adjust the path to match your project structure
   };

   const specs = swaggerJsdoc(options);

   export const setupSwagger = (app: Express) => {
     app.use('/api-docs', swaggerUi.serve, swaggerUi.setup(specs));
   };
   ```

2. Import and use the `setupSwagger` function in your main application file (`app.ts` or `server.ts`).

   ```typescript
   import express from 'express';
   import { setupSwagger } from './swagger';

   const app = express();

   // Middleware and routes setup
   app.use(express.json());

   // Swagger setup
   setupSwagger(app);

   app.listen(3000, () => {
     console.log('Server is running on http://localhost:3000');
     console.log('API Docs available at http://localhost:3000/api-docs');
   });
   ```

3. Annotate your API routes with Swagger comments.

   **Example route (`src/routes/user.ts`):**

   ```typescript
   /**
    * @swagger
    * /users:
    *   get:
    *     summary: Retrieve a list of users
    *     responses:
    *       200:
    *         description: A list of users
    */
   app.get('/users', (req, res) => {
     res.send([]);
   });
   ```

## Usage

1. Start your server:

   ```bash
   npm start
   ```

2. Open your browser and navigate to:

   ```
   http://localhost:3000/api-docs
   ```

   You should see the Swagger UI with your API documentation.

## Troubleshooting

- Ensure the `apis` path in the Swagger configuration matches the location of your route files.
- If you encounter CORS issues, use a middleware like `cors`.
- For dynamic server URLs, adjust the `servers` array in the Swagger options.

## Additional Resources

- [Swagger JSDoc Documentation](https://www.npmjs.com/package/swagger-jsdoc)
- [Swagger UI Express Documentation](https://www.npmjs.com/package/swagger-ui-express)
