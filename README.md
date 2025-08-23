# Angular Enterprise Project Structure

This project was generated with [Angular CLI](https://github.com/angular/angular-cli).

## About The Project

This repository serves as a template for building scalable and maintainable enterprise-level Angular applications. It follows best practices for project organization, separating concerns into distinct modules and directories. This structure is designed to improve developer experience, simplify onboarding, and promote code reusability.

## Project Structure

The project is organized into two main parts: the standard Angular CLI workspace configuration at the root level, and a feature-driven application structure within the `src/` directory.

### High-Level Overview

-   **`e2e/`**: Contains end-to-end (E2E) tests that simulate user behavior from start to finish.
-   **`node_modules/`**: Stores all third-party libraries and dependencies required for the project. Managed by npm or yarn and should not be committed to source control.
-   **`src/`**: Contains the application's source code. This is where all development happens.
-   **`angular.json`**: The configuration file for the Angular CLI. It defines project- and workspace-specific settings, build options, and other configurations.
-   **`package.json`**: Lists project dependencies and defines npm scripts for common tasks like testing, building, and serving.
-   **`tsconfig.json`**: The root TypeScript configuration file that specifies compiler options.

### Application (`src/`) Structure

The `src/` folder contains the core logic of our application, organized for clarity and scalability.

```
src/
├── app/
│   ├── core/
│   │   ├── guards/
│   │   ├── interceptors/
│   │   ├── services/
│   │   └── models/
│   │
│   ├── pages/ (or features/)
│   │   ├── home/
│   │   └── user-profile/
│   │
│   ├── shared/
│   │   ├── components/
│   │   ├── directives/
│   │   ├── pipes/
│   │   └── shared.module.ts
│   │
│   ├── app-routing.module.ts
│   ├── app.component.ts
│   └── app.module.ts
│
├── assets/
│   ├── images/
│   └── fonts/
│
├── environments/
│   ├── environment.ts
│   └── environment.prod.ts
│
├── index.html
├── main.ts
└── styles.css
```

#### `app/core/`
**Purpose**: Contains singleton services, interceptors, guards, and other logic that should only be created once per application. This module is imported only once in the root `AppModule`.
-   **`guards/`**: Route guards to protect routes (e.g., `AuthGuard`).
-   **`interceptors/`**: HTTP interceptors to modify requests/responses (e.g., adding auth tokens).
-   **`services/`**: Application-wide singleton services (e.g., `AuthService`, `LoggerService`). These services are typically provided in 'root'.
-   **`models/`**: TypeScript interfaces and classes for core data structures used across the application (e.g., `User`, `Product`).

#### `app/pages/` (or `app/features/`)
**Purpose**: This directory holds the different features or pages of your application, with each feature encapsulated in its own folder and module. This promotes lazy loading and separation of concerns.
-   **`home/`**: Contains all components, services, and routing related to the "Home" feature.
-   **`user-profile/`**: Contains everything related to the "User Profile" feature.

#### `app/shared/`
**Purpose**: Contains reusable components, directives, and pipes that are used across multiple feature modules. The `SharedModule` exports these common elements so they can be imported by any feature module that needs them.
-   **`components/`**: Reusable "dumb" components like custom buttons, loaders, or modals.
-   **`directives/`**: Custom directives for DOM manipulation (e.g., a `highlight` directive).
-   **`pipes/`**: Custom data transformation pipes (e.g., a `truncate` pipe).

#### `assets/`
**Purpose**: For static assets that are copied as-is to the build output.
-   **`images/`**: Contains all static images, icons, and logos.
-   **`fonts/`**: For custom font files.
-   **`i18n/`**: If your application supports multiple languages, translation files (e.g., `.json`) can be stored here.

#### `environments/`
**Purpose**: Manages environment-specific configurations.
-   **`environment.ts`**: Configuration for the development environment.
-   **`environment.prod.ts`**: Configuration for the production environment. You can add other files like `environment.staging.ts` for other stages.

## Getting Started

To get a local copy up and running, follow these simple steps.

### Prerequisites
Make sure you have Node.js and the Angular CLI installed on your machine.
*   **Node.js**: Download & Install Node.js
*   **Angular CLI**:
    ```sh
    npm install -g @angular/cli
    ```

### Installation
1.  Clone the repository to your local machine.
2.  Navigate to the project directory:
    ```sh
    cd structureAngular
    ```
3.  Install NPM packages:
    ```sh
    npm install
    ```

## Development Workflow

### Development Server
Run `ng serve` for a development server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

### Code Scaffolding
Run `ng generate component component-name` to generate a new component. You can also use `ng generate` for directives, pipes, services, classes, guards, interfaces, enums, and modules.

### Build
Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--prod` flag for a production build.

### Running Unit Tests
Run `ng test` to execute the unit tests via Karma.

### Key Dependencies
-   **@angular/core**: The core Angular framework.
-   **@angular/cli**: The command-line interface for Angular.
-   **@algolia/client-insights**: Algolia client for sending insights and analytics events.

## Further help
To get more help on the Angular CLI use `ng help` or go check out the Angular CLI Overview and Command Reference page.
