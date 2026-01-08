
# Gemini Instructions

When the user types "start project", read this file and execute the steps outlined in it.

# Project mission

Sandbox project for creating a starter template for my way of software development. Goal is to create agents.md file that can be used by gemini or other cli agents to recreate starter template from scratch. Create README.md for human readabiliy with shortest instructions to start environments for local development and links to production deployment practises. This document should also be updated according to future sessions.

# Initial setup

User should be first asked for information about which platforms should starter template be created if project is empty.

Starter templates:

- Databases:
  - [] Supabase
  - [] Firebase
- Back-end:
  - [] Java Spring Boot
  - [] Kotlin Spring Boot
  - [] Go Gin
- Front-end
  - [] Angular Prime-ng Sakai 
  - [] Compose multi-platform
  - [] Flutter cross-platform

# Architecture

Project will consist of multi layer applications. 

## Database 

There will be database layer that should be plug and play primarily for Firebase or Supabase. Also, there could be a possibility to use other implementations like self-hosted postges or any other mainstrean database engines

Folder for database should be created for potential future scripts or notes 

## Back-end

Depending if serverless architecture back-end is optional. If enabled starter for either java or kotlin with spring boot or go with gin should be created as a separate folder

## Front-end

Multiple choice can be selected. Each creates separate folder with coresponding platform or technology

### Angular Prime-ng Sakai

#### Prerequisites

- angular-cli
- git and optional github-cli

#### Steps

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/primefaces/sakai-ng
    ```
    Then, navigate into the `sakai-ng` directory, install dependencies, and start the development server to verify the initial setup:
    ```bash
    cd sakai-ng
    npm install
    ng serve
    ```
    Once the application is running, please confirm if it's working correctly in your browser.

2.  **Remove the existing .git directory:**
    ```bash
    rm -rf sakai-ng/.git
    ```

3.  **Remove unnecessary sample pages:**
    ```bash
    rm -rf sakai-ng/src/app/pages/auth/ sakai-ng/src/app/pages/crud/ sakai-ng/src/app/pages/documentation/ sakai-ng/src/app/pages/landing/ sakai-ng/src/app/pages/notfound/ sakai-ng/src/app/pages/service/ sakai-ng/src/app/pages/uikit/
    ```

4.  **Simplify the main application routes in `sakai-ng/src/app.routes.ts`:**
    *   **Instruction:** Update imports and appRoutes to only include AppLayout and DashboardComponent, removing all other sample page routes and their associated imports.
    *   **File:** `sakai-ng/src/app.routes.ts`
    *   **Action:** Replace the entire file content with:
        ```typescript
        import { Routes } from '@angular/router';
        import { AppLayout } from './app/layout/component/app.layout';
        import { DashboardComponent } from './app/pages/dashboard/dashboard';

        export const appRoutes: Routes = [
            {
                path: '',
                component: AppLayout,
                children: [
                    { path: '', component: DashboardComponent }
                ]
            }
        ];
        ```

5.  **Simplify the navigation menu in `sakai-ng/src/app/layout/component/app.menu.ts`:**
    *   **Instruction:** In the `ngOnInit` method, replace the `this.model` assignment with a new array that only contains the 'Dashboard' link.
    *   **File:** `sakai-ng/src/app/layout/component/app.menu.ts`
    *   **Action:** Find the `ngOnInit()` method and replace the `this.model = [...]` block with:
        ```typescript
        this.model = [
            {
                label: 'Home',
                items: [{ label: 'Dashboard', icon: 'pi pi-fw pi-home', routerLink: ['/'] }]
            }
        ];
        ```

6.  **Recreate the Dashboard component from the Empty page template:**
    1.  Clear the `dashboard` directory: `rm -rf sakai-ng/src/app/pages/dashboard/*`
    2.  Copy `empty` page content to `dashboard`: `cp -r sakai-ng/src/app/pages/empty/* sakai-ng/src/app/pages/dashboard/`
    3.  Rename the component file: `mv sakai-ng/src/app/pages/dashboard/empty.ts sakai-ng/src/app/pages/dashboard/dashboard.ts`
    4.  Update the component file `sakai-ng/src/app/pages/dashboard/dashboard.ts`. Replace the entire content with:
        ```typescript
        import { Component } from '@angular/core';

        @Component({
            selector: 'app-dashboard',
            standalone: true,
            template: ` <div class="card">
                <div class="font-semibold text-xl mb-4">Dashboard Page</div>
                <p>Use this page to start from scratch and place your custom content.</p>
            </div>`
        })
        export class DashboardComponent {}
        ```

7.  **Clean up unused routes in `sakai-ng/src/app/pages/pages.routes.ts`:**
    *   **Instruction:** Remove all routes from `pages.routes.ts` as they are no longer needed.
    *   **File:** `sakai-ng/src/app/pages/pages.routes.ts`
    *   **Action:** Replace the entire file content with:
        ```typescript
        import { Routes } from '@angular/router';

        export default [] as Routes;
        ```

