CORE ERP – WORK RULES (MODULAR MONOLITH)

SYSTEM TYPE

Modular Monolith ERP Project
Single repository (monorepo)
Multiple business modules inside /modules
Shared infrastructure inside /packages
Applications inside /apps

PROJECT STRUCTURE RULES

/modules (Business Domains)
Each module is a separate business domain (NOT a full app)
Example modules: pos, hrms, ims, wms, crm, accounting, finance
Each module follows Clean Architecture: domain, application, infrastructure

domain
Contains pure business logic only

entities
value-objects
services
events
enums
exceptions
index.ts
Rules: No database access, No Express/React/framework code, No external APIs

application
Contains application/use-case layer

use-cases
dtos
services
interfaces
Rules: Orchestrates business logic, Defines use-cases, Uses domain layer, No direct DB/framework code

infrastructure
Contains technical implementations

database
repositories
orm
external-services
index.ts
Rules: Database implementations, ORM logic, External API integrations, Infrastructure concerns only

/Apps (Running Applications)

apps/web
Frontend application

React, Vite, Feature-Sliced Design (FSD)

apps/api
Backend API gateway

Node.js, Express, Clean Architecture
Responsibilities: Routes, Controllers, Middleware, Authentication, API orchestration

/Packages (Shared Libraries)

auth → shared authentication logic
database → shared DB connection + ORM setup
ui → reusable UI components
utils → helper functions
types → shared TypeScript types

WORKFLOW

Requirements Definition: define business needs, module scope, user roles
Schema Design: database schema, relationships, constraints, permissions
UI/UX Design: Figma, user flows, screens, component system
Backend + Frontend Development: define API contracts first, develop backend, develop frontend, integrate modules

IMPORTANT RULES

Backend APIs live ONLY in /apps/api
Frontend lives ONLY in /apps/web
Modules are business/domain logic only
Shared code must go into /packages
Always design before coding
