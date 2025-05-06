# Voice Agent Backend

## Overview

This document provides an overview of the backend system for the Voice Agent. Please note that the source code for this backend cannot be shared publicly due to a Non-Disclosure Agreement (NDA) with the company for which it was developed.

The backend is responsible for the core functionalities of the voice agent, the architecture and components of which are described in this document.

## Folder Structure

The backend is organized into the following main directories and files within the `src` folder:

- `src/`
  - `index.ts`: This is the main entry point for the backend application. It likely initializes the server (e.g., Express, NestJS), sets up middleware, connects to the database, and starts listening for incoming network requests.
  - `events.ts`: This file is dedicated to managing event-driven architecture within the application. It probably defines, emits, and handles various application events, allowing for decoupled communication between different modules (e.g., using Node.js `EventEmitter` or a custom event bus system).
  - `config/`: Contains configuration files for the application. These files manage settings for different environments (development, production), database connections, third-party API keys, and other tunable parameters.
    - _Example files:_ `database.config.ts` (for database connection strings and options), `app.config.ts` (for general application settings like port, logging levels), `jwt.config.ts` (for JWT secret keys and expiration times).
  - `db/`: Handles all database-related concerns. This includes schema definitions, migration scripts to manage database structure changes over time, and potentially data seeding scripts for initial data setup.
    - _Example subdirectories/files:_ `models/` or `entities/` (containing data model definitions, e.g., for an ORM like Prisma or TypeORM), `migrations/` (for database migration scripts), `seeds/` (for data seeding scripts).
  - `engine/index.ts`: This directory likely houses the core business logic or specialized processing units unique to the voice agent. This could include algorithms for voice recognition, natural language understanding, state management for conversations, or integrations with AI/ML models.
    - _Example files:_ `voice-input-processor.ts`, `nlp-handler.ts`, `dialogue-manager.ts`, `intent-classifier.ts`.
  - `lib/`: A collection of shared libraries, helper functions, or reusable modules that provide common functionalities across different parts of the application but don't belong to a specific feature domain.
    - _Example files:_ `logger.ts` (for custom logging), `api-client.ts` (for making requests to external APIs), `crypto.ts` (for encryption/decryption utilities).
  - `server/`: Responsible for setting up the HTTP server, defining API routes, and handling incoming requests and outgoing responses. It acts as the interface between the client and the backend logic.
    - _Example subdirectories/files:_ `app.ts` (core server setup, e.g., Express app instance), `routes/` (directory for API route definitions like `user.routes.ts`, `agent.routes.ts`), `controllers/` (handlers for specific API endpoints), `middlewares/` (for request processing steps like authentication, validation).
  - `services/`: Contains the business logic for various features or domains of the application. Services are typically called by controllers or other services to perform specific tasks, often involving data manipulation and interaction with the database or external APIs.
    - _Example files:_ `user.service.ts` (for user authentication, profile management), `voice.service.ts` (for voice processing logic), `session.service.ts` (for managing user sessions).
  - `types/`: This directory defines TypeScript types, interfaces, and enums used throughout the backend. This ensures type safety and clear data contracts between different modules and for API request/response payloads.
    - _Example files:_ `index.ts` (often re-exporting all types), `user.types.ts`, `request.types.ts`, `response.types.ts`.
  - `utils/`: A collection of general-purpose utility functions and helper classes that perform common, small, and isolated tasks, used across various parts of the application.
    - _Example files:_ `validators.ts` (for input validation), `formatters.ts` (for data formatting, e.g., dates, strings), `error-handler.ts` (for consistent error handling), `constants.ts`.


## How it Works

It is based on a event-based architecture, where the main event loop is the `EventEmitter` instance. There is a core `engine.ts` file that handles all the events and makes the flow of the application possible. The `engine.ts` file is responsible following : 
1. Listening for incoming requests from the frontend or any service (TTS, STT, LLM, etc).
2. Processing the requests and emitting events.
3. Listening for these events and processing them.
4. Sending responses back to the frontend or any service.
5. For easy plug and play of TTS ,STT and LLM providers

## Further Information

For a more in-depth discussion about the backend architecture and its workings, or to explore potential collaborations, please feel free to book a meeting with me:

[cal.com/whycurious101](https://cal.com/whycurious101)
