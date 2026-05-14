# Skill index

Catalog of skills FlowState may recommend. Organized by domain. Extend by appending a new `##` section using the template at the bottom.

Fields:
- **What it does** — one sentence.
- **Keywords** — comma-separated triggers (tools, file types, verbs, concepts).
- **Chains to** — skill names that often follow.
- **Priority hint:** primary | secondary

---

## DOCUMENT & FILE PROCESSING

## xlsx
- **What it does:** Reads, writes, and transforms spreadsheet data in Excel-compatible formats.
- **Keywords:** excel, xlsx, xls, csv, spreadsheet, workbook, pivot table, sheet, tabular data, rows, columns
- **Chains to:** docx, pdf
- **Priority hint:** primary when tabular ingestion or output is explicit

## docx
- **What it does:** Drafts or edits structured documents in Word-compatible formats.
- **Keywords:** word, docx, report, memo, letter, template, styles, track changes, formatted document
- **Chains to:** pdf
- **Priority hint:** primary when narrative or formatted document output is explicit

## pdf
- **What it does:** Generates, merges, splits, fills forms, or extracts content from PDFs.
- **Keywords:** pdf, print, export, forms, merge, split, extract, flatten, final artifact
- **Chains to:** —
- **Priority hint:** primary when final artifact must be PDF

## pdf-reading
- **What it does:** Reads and extracts text, tables, or images from existing PDF files.
- **Keywords:** read pdf, parse pdf, extract from pdf, pdf content, scanned pdf, ocr
- **Chains to:** docx, xlsx
- **Priority hint:** primary when the input is a PDF that must be parsed

## pptx
- **What it does:** Creates or edits PowerPoint-compatible slide decks.
- **Keywords:** presentation, slides, deck, pptx, powerpoint, pitch, slideshow
- **Chains to:** pdf
- **Priority hint:** primary when slide output is explicit

## file-reading
- **What it does:** Routes uploaded files to the correct reading strategy based on type.
- **Keywords:** uploaded file, attachment, parse file, read file, open file, file path
- **Chains to:** xlsx, docx, pdf-reading
- **Priority hint:** primary at session start when files are uploaded without explicit format handling

---

## FRONTEND DEVELOPMENT

## frontend-design
- **What it does:** Creates distinctive, production-grade web UIs with high design quality.
- **Keywords:** react, component, UI, interface, html, css, tailwind, landing page, dashboard, web app, layout, responsive, design system, figma to code
- **Chains to:** api-integration, testing
- **Priority hint:** primary when a visual interface is being built

## react-component
- **What it does:** Scaffolds and wires up React components with hooks, state, and props.
- **Keywords:** react, jsx, tsx, component, useState, useEffect, props, hooks, context, next.js
- **Chains to:** frontend-design, api-integration
- **Priority hint:** primary when React-specific component work is described

## css-styling
- **What it does:** Writes and refactors CSS, including utility frameworks and preprocessors.
- **Keywords:** css, scss, sass, tailwind, styled-components, animations, media queries, flexbox, grid, theme
- **Chains to:** frontend-design
- **Priority hint:** secondary unless styling is the explicit task

## accessibility
- **What it does:** Audits and improves UI accessibility to meet WCAG standards.
- **Keywords:** a11y, accessibility, wcag, screen reader, aria, contrast, keyboard navigation, focus
- **Chains to:** frontend-design
- **Priority hint:** secondary; primary when compliance is mentioned

## performance-optimization
- **What it does:** Identifies and fixes frontend and backend performance bottlenecks.
- **Keywords:** performance, slow, latency, load time, bundle size, lighthouse, web vitals, caching, lazy load, profiling
- **Chains to:** monitoring
- **Priority hint:** primary when slowness or performance metrics are mentioned

---

## BACKEND DEVELOPMENT

## api-design
- **What it does:** Designs and documents RESTful or GraphQL APIs with clear contracts.
- **Keywords:** api, rest, restful, graphql, endpoint, routes, swagger, openapi, postman, api docs
- **Chains to:** api-integration, auth, testing
- **Priority hint:** primary when building or designing an API layer

## api-integration
- **What it does:** Integrates and consumes third-party or internal APIs in application code.
- **Keywords:** fetch, axios, http client, webhook, third-party api, sdk, api key, integration
- **Chains to:** error-handling, testing
- **Priority hint:** primary when connecting to an external service

## auth
- **What it does:** Implements authentication and authorization flows in applications.
- **Keywords:** auth, login, jwt, oauth, oauth2, sso, session, cookies, rbac, permissions, keycloak, passport
- **Chains to:** security, testing
- **Priority hint:** primary when login, access control, or tokens are mentioned

## server-setup
- **What it does:** Scaffolds and configures a backend server with routing and middleware.
- **Keywords:** express, fastapi, django, flask, node, server, middleware, routing, cors, body parser
- **Chains to:** api-design, database
- **Priority hint:** primary at greenfield backend project start

## microservices
- **What it does:** Designs, splits, or connects services in a microservices architecture.
- **Keywords:** microservices, service mesh, grpc, event-driven, message queue, kafka, rabbitmq, service boundary, decoupled
- **Chains to:** docker, api-design, monitoring
- **Priority hint:** primary when architecture involves multiple services

## websockets
- **What it does:** Implements real-time bidirectional communication using WebSockets or SSE.
- **Keywords:** websocket, socket.io, real-time, live updates, sse, push notifications, chat
- **Chains to:** server-setup
- **Priority hint:** primary when real-time features are described

## caching
- **What it does:** Adds caching layers to reduce latency and database load.
- **Keywords:** redis, memcached, cache, ttl, cache invalidation, in-memory, session cache, cdn
- **Chains to:** database, monitoring
- **Priority hint:** secondary unless performance or scale is explicitly mentioned

## background-jobs
- **What it does:** Sets up queues, workers, and scheduled jobs for async processing.
- **Keywords:** queue, worker, cron, background job, bull, celery, scheduled task, async processing
- **Chains to:** monitoring, database
- **Priority hint:** primary when async or scheduled work is described

## error-handling
- **What it does:** Implements structured error handling, logging, and recovery patterns.
- **Keywords:** error handling, try catch, exceptions, fallback, retry, circuit breaker, status codes
- **Chains to:** monitoring, testing
- **Priority hint:** secondary; primary when reliability or error flows are the focus

---

## DATABASE

## database-design
- **What it does:** Designs schemas, relationships, and indexes for relational or NoSQL databases.
- **Keywords:** schema, erd, tables, relations, postgres, mysql, mongodb, nosql, normalize, index, foreign key
- **Chains to:** database-migration, api-design
- **Priority hint:** primary at project start when data models are being planned

## database-queries
- **What it does:** Writes and optimizes SQL or NoSQL queries for correctness and performance.
- **Keywords:** sql, query, select, join, aggregate, slow query, explain, orm, prisma, sequelize, mongoose
- **Chains to:** caching
- **Priority hint:** primary when querying or query performance is the task

## database-migration
- **What it does:** Authors and runs database migrations safely across environments.
- **Keywords:** migration, alembic, flyway, liquibase, schema change, alter table, rollback, seed
- **Chains to:** deployment
- **Priority hint:** primary when schema changes are in scope

## orm-setup
- **What it does:** Configures and uses an ORM to map application models to database tables.
- **Keywords:** orm, prisma, typeorm, sequelize, sqlalchemy, drizzle, entity, model
- **Chains to:** database-queries
- **Priority hint:** primary when an ORM is mentioned or a new DB layer is being set up

---

## DEVOPS & CI/CD

## ci-cd
- **What it does:** Sets up or repairs CI/CD pipelines for automated build, test, and deploy.
- **Keywords:** ci, cd, github actions, jenkins, circleci, gitlab ci, pipeline, failing build, deploy automation
- **Chains to:** docker, deployment
- **Priority hint:** primary when pipeline setup or failures are described

## docker
- **What it does:** Containerizes applications and sets up Docker or Docker Compose environments.
- **Keywords:** docker, dockerfile, container, docker-compose, image, registry, build context
- **Chains to:** kubernetes, deployment
- **Priority hint:** primary when containerization is mentioned

## kubernetes
- **What it does:** Deploys and manages containerized workloads with Kubernetes.
- **Keywords:** kubernetes, k8s, helm, pod, deployment, service, ingress, kubectl, cluster
- **Chains to:** monitoring, cloud-infra
- **Priority hint:** primary when orchestration or k8s is mentioned

## deployment
- **What it does:** Deploys applications to staging or production environments.
- **Keywords:** deploy, release, ship, production, staging, vercel, heroku, fly.io, railway, aws eb
- **Chains to:** monitoring, ci-cd
- **Priority hint:** primary when going live or environment promotion is described

## infrastructure-as-code
- **What it does:** Defines cloud infrastructure using code with Terraform, Pulumi, or CDK.
- **Keywords:** terraform, pulumi, cdk, iac, infrastructure as code, provision, resource, state file
- **Chains to:** cloud-infra, ci-cd
- **Priority hint:** primary when infrastructure provisioning is mentioned

---

## CLOUD & INFRASTRUCTURE

## cloud-infra
- **What it does:** Configures and manages cloud resources on AWS, GCP, or Azure.
- **Keywords:** aws, gcp, azure, cloud, ec2, s3, lambda, cloud functions, storage bucket, iam, vpc
- **Chains to:** monitoring, security
- **Priority hint:** primary when cloud resources or providers are mentioned

## serverless
- **What it does:** Builds event-driven functions on serverless platforms.
- **Keywords:** serverless, lambda, cloud functions, azure functions, edge functions, vercel functions, event trigger
- **Chains to:** api-design, monitoring
- **Priority hint:** primary when serverless or function-as-a-service is mentioned

## edge-computing
- **What it does:** Deploys logic to CDN edge nodes for low-latency global delivery.
- **Keywords:** edge, cloudflare workers, edge functions, cdn, deno deploy, low latency, geo-distributed
- **Chains to:** serverless
- **Priority hint:** secondary; primary for latency-critical global apps

## cdn-setup
- **What it does:** Configures content delivery networks for static assets and media.
- **Keywords:** cdn, cloudfront, cloudflare, fastly, static assets, media delivery, cache headers
- **Chains to:** performance-optimization
- **Priority hint:** secondary unless media or static delivery is the focus

---

## SECURITY

## security-audit
- **What it does:** Reviews code and configurations for common vulnerabilities and misconfigurations.
- **Keywords:** security, owasp, vulnerability, pen test, injection, xss, csrf, secrets, exposed keys
- **Chains to:** auth, dependency-management
- **Priority hint:** primary when security review or hardening is mentioned

## secrets-management
- **What it does:** Manages environment variables, API keys, and secrets securely.
- **Keywords:** secrets, env vars, dotenv, vault, .env, api key, secret manager, 1password, doppler
- **Chains to:** cloud-infra
- **Priority hint:** primary when secrets or credentials are part of the setup

## dependency-management
- **What it does:** Audits and updates dependencies to fix vulnerabilities and conflicts.
- **Keywords:** npm audit, dependabot, snyk, outdated packages, cve, update dependencies, lock file
- **Chains to:** ci-cd
- **Priority hint:** primary when dependency security or updates are the task

## compliance
- **What it does:** Implements controls and documentation for regulatory compliance.
- **Keywords:** gdpr, hipaa, soc2, compliance, data privacy, audit log, data retention, pii
- **Chains to:** security-audit, documentation
- **Priority hint:** primary when regulations or compliance are mentioned

---

## TESTING & QA

## unit-testing
- **What it does:** Writes unit tests for isolated functions and modules.
- **Keywords:** unit test, jest, vitest, pytest, mocha, chai, coverage, tdd, mock, stub
- **Chains to:** integration-testing, ci-cd
- **Priority hint:** primary when writing tests or coverage is mentioned

## integration-testing
- **What it does:** Tests interactions between components, services, or API layers.
- **Keywords:** integration test, supertest, testcontainers, api test, service test, end-to-end, contract test
- **Chains to:** e2e-testing, ci-cd
- **Priority hint:** primary when cross-layer testing is described

## e2e-testing
- **What it does:** Automates full end-to-end user flows in a browser environment.
- **Keywords:** e2e, playwright, cypress, selenium, browser test, ui test, user flow automation
- **Chains to:** ci-cd
- **Priority hint:** primary when browser or full-flow testing is mentioned

## load-testing
- **What it does:** Simulates traffic load to identify performance and scalability limits.
- **Keywords:** load test, k6, jmeter, locust, stress test, throughput, rps, concurrent users
- **Chains to:** monitoring, performance-optimization
- **Priority hint:** primary when scale or performance under load is mentioned

---

## MONITORING & OBSERVABILITY

## monitoring
- **What it does:** Sets up metrics, alerts, and dashboards for production observability.
- **Keywords:** prometheus, grafana, datadog, cloudwatch, alerts, metrics, uptime, sla, dashboard
- **Chains to:** logging
- **Priority hint:** primary when production health or alerting is in scope

## logging
- **What it does:** Implements structured logging and log aggregation pipelines.
- **Keywords:** logs, logging, elk, loki, splunk, cloudwatch logs, structured logs, log level, trace id
- **Chains to:** monitoring
- **Priority hint:** secondary; primary when debugging or log management is the task

## error-tracking
- **What it does:** Integrates error tracking tools to catch and triage production exceptions.
- **Keywords:** sentry, bugsnag, rollbar, error tracking, exception, crash report, stack trace
- **Chains to:** monitoring
- **Priority hint:** primary when production errors or crash reporting is described

## tracing
- **What it does:** Sets up distributed tracing to follow requests across services.
- **Keywords:** tracing, opentelemetry, jaeger, zipkin, distributed trace, span, request lifecycle
- **Chains to:** monitoring, microservices
- **Priority hint:** secondary; primary in microservices debugging contexts

---

## VERSION CONTROL & COLLABORATION

## git-workflow
- **What it does:** Manages branches, commits, rebases, and merge strategies in Git.
- **Keywords:** git, branch, rebase, merge, cherry-pick, conflict, gitflow, commit, history
- **Chains to:** code-review
- **Priority hint:** primary when branching strategy or Git issues are described

## code-review
- **What it does:** Structures and improves pull request reviews for quality and speed.
- **Keywords:** code review, pr, pull request, review comments, approval, diff, feedback
- **Chains to:** ci-cd
- **Priority hint:** primary when reviewing or improving the PR process

## pr-management
- **What it does:** Keeps pull requests merge-ready through conflicts, CI loops, and review cycles.
- **Keywords:** pr, merge, conflict, rebase, merge-ready, stacked prs, pr queue, review cycle
- **Chains to:** ci-cd
- **Priority hint:** primary when PR maintenance and merge health are the focus

## monorepo
- **What it does:** Sets up and manages monorepo tooling for shared packages and workspaces.
- **Keywords:** monorepo, turborepo, nx, lerna, workspace, shared packages, yarn workspaces
- **Chains to:** ci-cd, docker
- **Priority hint:** primary when monorepo structure or tooling is mentioned

---

## SYSTEM DESIGN & ARCHITECTURE

## system-design
- **What it does:** Plans high-level architecture for scalability, reliability, and maintainability.
- **Keywords:** architecture, system design, scalability, microservices, monolith, event-driven, trade-offs, design doc
- **Chains to:** api-design, database-design
- **Priority hint:** primary at the start of a new system or major refactor

## refactoring
- **What it does:** Restructures existing code for clarity, maintainability, and reduced duplication.
- **Keywords:** refactor, clean code, technical debt, dry, solid, code smell, restructure, modularize
- **Chains to:** unit-testing, code-review
- **Priority hint:** primary when code quality improvement is the explicit goal

## design-patterns
- **What it does:** Applies standard software design patterns to solve architectural problems.
- **Keywords:** design pattern, factory, singleton, observer, strategy, repository pattern, dependency injection
- **Chains to:** refactoring
- **Priority hint:** secondary; primary when patterns or architecture principles are being discussed

## api-versioning
- **What it does:** Manages breaking changes and backward compatibility across API versions.
- **Keywords:** api versioning, v1, v2, breaking changes, deprecation, backward compatibility, semver
- **Chains to:** api-design, documentation
- **Priority hint:** secondary; primary when API evolution or deprecation is mentioned

---

## DATA & ANALYTICS

## data-pipeline
- **What it does:** Builds ETL or ELT pipelines to move and transform data across systems.
- **Keywords:** etl, elt, pipeline, airflow, prefect, dbt, data warehouse, ingest, transform, load
- **Chains to:** database-design, monitoring
- **Priority hint:** primary when data movement or transformation is described

## data-visualization
- **What it does:** Creates charts, graphs, and dashboards to make data understandable.
- **Keywords:** chart, graph, dashboard, visualization, d3, recharts, plotly, grafana, tableau, bi
- **Chains to:** reporting
- **Priority hint:** primary when charts or visual data output is mentioned

## reporting
- **What it does:** Generates structured reports from data with formatted output.
- **Keywords:** report, summary, export, scheduled report, pdf report, data summary, weekly report
- **Chains to:** pdf, xlsx
- **Priority hint:** primary when generating output documents from data

## ml-integration
- **What it does:** Integrates machine learning model inference into applications.
- **Keywords:** ml, model inference, embedding, openai, hugging face, langchain, vector db, predict, llm
- **Chains to:** api-integration, monitoring
- **Priority hint:** primary when AI/ML model usage in an app is described

## data-cleaning
- **What it does:** Normalizes, deduplicates, and validates raw datasets for downstream use.
- **Keywords:** data cleaning, normalize, deduplicate, validate, missing values, data quality, pandas
- **Chains to:** data-pipeline, xlsx
- **Priority hint:** primary when messy or raw data needs to be processed

---

## DOCUMENTATION

## documentation
- **What it does:** Writes technical documentation, README files, and developer guides.
- **Keywords:** docs, readme, docstring, technical writing, confluence, notion, developer guide, wiki
- **Chains to:** api-design
- **Priority hint:** primary when writing or updating docs is the task

## api-docs
- **What it does:** Generates or improves API reference documentation with examples.
- **Keywords:** api docs, swagger, openapi, postman collection, api reference, endpoint docs
- **Chains to:** api-design
- **Priority hint:** primary when API documentation is explicitly needed

## adr
- **What it does:** Writes Architecture Decision Records to document key technical choices.
- **Keywords:** adr, architecture decision, decision record, trade-off, technical decision, rationale
- **Chains to:** system-design
- **Priority hint:** secondary; primary when architectural decisions need to be recorded

## onboarding-guide
- **What it does:** Creates developer onboarding documentation for a new codebase or project.
- **Keywords:** onboarding, getting started, setup guide, new developer, first steps, dev environment setup
- **Chains to:** documentation
- **Priority hint:** primary when setting up a new team member or project handoff is described

---

## AI / LLM TOOLING

## prompt-engineering
- **What it does:** Designs and optimizes prompts for LLM-powered features.
- **Keywords:** prompt, system prompt, few-shot, chain of thought, llm, claude, gpt, temperature, instruction
- **Chains to:** ml-integration
- **Priority hint:** primary when building LLM-powered features

## rag-pipeline
- **What it does:** Builds Retrieval-Augmented Generation pipelines with vector stores.
- **Keywords:** rag, vector store, embeddings, pinecone, weaviate, chroma, semantic search, retrieval
- **Chains to:** ml-integration, data-pipeline
- **Priority hint:** primary when knowledge retrieval or semantic search over docs is described

## ai-agent
- **What it does:** Architects and builds AI agents with tool use, memory, and planning.
- **Keywords:** agent, tool use, mcp, function calling, autonomous, multi-step, langgraph, autogen
- **Chains to:** prompt-engineering, api-integration
- **Priority hint:** primary when building autonomous AI workflows

---

## DEVELOPER TOOLING & DX

## dev-environment
- **What it does:** Sets up local development environments, dotfiles, and toolchain configuration.
- **Keywords:** dev environment, dotfiles, nvm, pyenv, brew, setup, local, dev container, devcontainer
- **Chains to:** docker
- **Priority hint:** primary at the start of a session where env setup is the blocker

## linting-formatting
- **What it does:** Configures linters and formatters to enforce code style automatically.
- **Keywords:** eslint, prettier, ruff, black, flake8, lint, format, pre-commit, code style, husky
- **Chains to:** ci-cd
- **Priority hint:** secondary; primary when code quality automation is being set up

## package-management
- **What it does:** Manages project dependencies, lock files, and package registries.
- **Keywords:** npm, yarn, pnpm, pip, poetry, cargo, packages, dependencies, lock file, registry
- **Chains to:** ci-cd
- **Priority hint:** secondary; primary when dependency conflicts or setup is the task

## scripting
- **What it does:** Writes shell or Python scripts to automate repetitive developer tasks.
- **Keywords:** bash, shell script, python script, automate, cli, task runner, makefile, just
- **Chains to:** ci-cd
- **Priority hint:** primary when the user wants to automate a manual workflow

## debugging
- **What it does:** Diagnoses and traces bugs across the stack using logs, breakpoints, and tools.
- **Keywords:** debug, breakpoint, devtools, stack trace, reproduce bug, log, inspect, fix bug
- **Chains to:** error-handling, logging
- **Priority hint:** primary when an active bug or unexpected behavior is described

## code-generation
- **What it does:** Generates boilerplate, scaffolding, or repetitive code patterns automatically.
- **Keywords:** scaffold, generate, boilerplate, template, code gen, plop, yeoman, stub, seed
- **Chains to:** refactoring
- **Priority hint:** primary when the user needs to bootstrap new files or modules quickly

## create-skill
- **What it does:** Authors new Claude Agent Skills (SKILL.md structure, keywords, trigger logic).
- **Keywords:** new skill, skill.md, agent skill, cursor skill, create skill, package workflow
- **Chains to:** create-rule
- **Priority hint:** primary when building reusable agent behavior

## create-rule
- **What it does:** Adds or edits Cursor project rules (.cursor/rules or AGENTS.md) for persistent AI guidance.
- **Keywords:** cursor rule, agents.md, project conventions, coding standards, ai rules
- **Chains to:** —
- **Priority hint:** primary when the user wants to encode standards for the repo

## humanizer
- **What it does:** Removes AI-generated writing patterns to make text sound more natural.
- **Keywords:** ai writing, humanize, rewrite, natural tone, remove ai, sounding human, text cleanup
- **Chains to:** documentation
- **Priority hint:** primary when editing or reviewing AI-generated text

## short-responses
- **What it does:** Switches Claude to compact 3–5 line response mode using the % prefix.
- **Keywords:** short answers, brief, tldr, compact mode, quick response, less text
- **Chains to:** —
- **Priority hint:** secondary; only surface when the user wants brevity by default

## product-self-knowledge
- **What it does:** Provides accurate, up-to-date facts about Anthropic products and Claude capabilities.
- **Keywords:** claude api, anthropic, model pricing, rate limits, claude features, which model, claude plans
- **Chains to:** —
- **Priority hint:** primary when the user asks about Claude itself or the Anthropic API

---

### Template for new skills

```markdown
## skill-name

- **What it does:** …
- **Keywords:** …
- **Chains to:** skill-a, skill-b
- **Priority hint:** primary | secondary
```
