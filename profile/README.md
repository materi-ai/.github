<div align="center">

# Materi

### The Intelligent Document Platform for Modern Teams

[![Website](https://img.shields.io/badge/Website-getmateri.com-6366f1?style=flat-square)](https://getmateri.com)
[![License](https://img.shields.io/badge/License-Proprietary-64748b?style=flat-square)](#)
[![Status](https://img.shields.io/badge/Status-Production-10b981?style=flat-square)](https://getmateri.com)

<p align="center">
  <em>Empowering teams to create, collaborate, and scale content with intelligent automation and real-time collaboration</em>
</p>

[Overview](#overview) · [Features](#core-features) · [Tech Stack](#technology-stack) · [Projects](#key-projects) · [Contributing](#contributing)

</div>

---

## Overview

Materi is a next-generation document collaboration platform that combines the familiarity of traditional editors with intelligent content management and real-time collaboration. Built for teams who demand speed, consistency, and scale.

### Why Materi?

-   **Fragment System** — Reusable content blocks that maintain consistency across all documents
-   **AI-Powered Writing** — Intelligent suggestions and automated content generation
-   **Real-Time Collaboration** — Built-in presence, comments, and live editing
-   **Knowledge Management** — Institutional memory that grows with your team
-   **API-First Design** — Extensible platform for custom workflows and integrations

---

## Core Features

### Fragment-Based Content Management

Reusable content blocks that maintain consistency and accelerate content creation across your organization.

### Real-Time Collaboration

Built on WebSocket infrastructure with operational transformation for seamless multi-user editing.

### AI Writing Assistant

Intelligent suggestions, tone analysis, and automated content generation powered by modern LLMs.

### Enterprise-Ready Security

Role-based access control, audit logging, and SOC 2 compliance readiness.

### Extensible API

RESTful and GraphQL APIs with comprehensive SDK support for custom integrations.

---

## Technology Stack

### Frontend

-   **Next.js 14** — React framework with App Router
-   **TypeScript** — Type-safe development
-   **TailwindCSS** — Utility-first styling
-   **Tiptap** — Extensible rich-text editor

### Backend

-   **Go** — High-performance microservices
-   **PostgreSQL** — Primary data store
-   **Redis** — Caching and session management
-   **gRPC** — Inter-service communication

### Infrastructure

-   **Kubernetes** — Container orchestration
-   **Railway** — Cloud deployment platform
-   **Grafana Stack** — Observability (Loki, Prometheus, Tempo)
-   **Alloy** — Unified telemetry collection

### DevOps

-   **Terraform** — Infrastructure as code
-   **GitHub Actions** — CI/CD pipelines
-   **Docker** — Containerization

---

## Key Projects

| Project          | Description                      | Tech Stack                  | Repository |
| ---------------- | -------------------------------- | --------------------------- | ---------- |
| **Canvas**       | Main document editor application | Next.js, TypeScript, Tiptap | [products/canvas](https://github.com/materi/products-canvas) |
| **Manuscript**   | Document management service      | Go, PostgreSQL              | [domain/manuscript](https://github.com/materi/domain-manuscript) |
| **Printery**     | Export and rendering engine      | Go, PDF generation          | [domain/printery](https://github.com/materi/domain-printery) |
| **Relay**        | Real-time collaboration service  | Go, WebSocket, Redis        | [domain/relay](https://github.com/materi/domain-relay) |
| **Intelligence** | AI and ML services               | Python, TypeScript          | [platform/intelligence](https://github.com/materi/platform-intelligence) |
| **Shield**       | Authentication and authorization | Go, JWT                     | [domain/shield](https://github.com/materi/domain-shield) |

---

## Contributing

We welcome contributions from the community! Whether you're fixing bugs, improving documentation, or proposing new features.

### Getting Started

Each service has its own repository with contribution guidelines. Start by:

1. Choose a service to contribute to
2. Read the service's README and contribution guidelines
3. Set up your local environment using the service's setup instructions
4. Submit pull requests following the service's workflow

### Development Resources

-   [Architecture Documentation](https://docs.getmateri.com/architecture)
-   [API Reference](https://docs.getmateri.com/api)
-   [SDK Documentation](https://docs.getmateri.com/sdk)
-   [Development Guide](https://docs.getmateri.com/development)

---

## Status & Health

-   **Production Status** — Live and serving customers
-   **Monitoring** — Full observability with Grafana Stack
-   **Deployment** — Automated CI/CD pipeline with GitHub Actions
-   **Uptime** — 99.9% SLA target

---

## Contact & Community

-   **Website**: [getmateri.com](https://getmateri.com)
-   **Documentation**: [docs.getmateri.com](https://docs.getmateri.com)
-   **Email**: hello@getmateri.com
-   **Twitter**: [@getmateri](#)
-   **LinkedIn**: [Materi](#)

---

## License

Copyright © 2026 Materi. All rights reserved.

This software is proprietary. Unauthorized copying, distribution, or modification is strictly prohibited.

---

<div align="center">

**Built by the Materi Team**

<sub>Making document collaboration intelligent, scalable, and delightful</sub>

</div>
