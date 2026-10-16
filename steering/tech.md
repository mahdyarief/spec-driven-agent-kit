# Technology Steering Document

> Project-level technology stack, engineering standards, and technical constraints.

## 1. Core Stack & Frameworks
| Layer | Technology | Version | Notes / Conventions |
|---|---|---|---|
| **Language** | TypeScript / Python / Go / etc. | {Version} | Strict type checking enabled |
| **Frontend** | React / Vue / Next.js / etc. | {Version} | State management & styling standard |
| **Backend** | Express / NestJS / FastAPI / etc. | {Version} | REST / GraphQL / gRPC |
| **Database** | PostgreSQL / MySQL / MongoDB / etc. | {Version} | ORM / Migration tool (Prisma/Drizzle/Sequelize) |
| **Testing** | Vitest / Jest / Pytest / Playwright | {Version} | Unit, integration & e2e standards |

## 2. Technical Constraints & Invariants
- **API Contracts:** OpenAPI / Swagger spec is authoritative; client SDKs must be generated, never hand-edited.
- **Data Validation:** Dual validation rule — Frontend validates for user feedback, Backend validates for authoritative truth.
- **Timezone & Dates:** Standardized date formats (e.g. ISO-8601 or `YYYY-MM-DD` in DB/API) with explicit project timezone.
- **Performance & Queries:** Bounded queries, explicit pagination, indexed filters, zero N+1 queries.

## 3. Third-Party Integrations & Services
- **Auth Provider:** {e.g. Auth0, Clerk, Supabase, internal JWT}
- **Storage / CDN:** {e.g. AWS S3, Cloudflare R2}
- **Notifications / Queues:** {e.g. Redis BullMQ, RabbitMQ, SQS, Webhooks}
