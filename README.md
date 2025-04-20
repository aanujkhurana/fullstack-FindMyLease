<h1 align="center">🏢 fullstack-FindMyLease</h1>

<p align="center">
  <strong>An enterprise-grade rental property management platform</strong><br/>
  Built with <code>Next.js</code>, <code>AWS</code>, and <code>PostgreSQL</code> for seamless listings, secure logins, and tenant/manager management.
</p>

<p align="center">
  <img src="https://img.shields.io/github/languages/top/aanujkhurana/fullstack-FindMyLease?color=blue&style=flat-square" />
  <img src="https://img.shields.io/badge/Next.js-13+-black?logo=next.js" />
  <img src="https://img.shields.io/badge/AWS-Deployed-orange?logo=amazonaws" />
  <img src="https://img.shields.io/badge/PostgreSQL-Database-blue?logo=postgresql" />
  <img src="https://img.shields.io/badge/Prisma-ORM-lightblue?logo=prisma" />
  <img src="https://img.shields.io/badge/License-MIT-green.svg" />
</p>

---

## 🔗 Quick Links

- 🚀 [Live Site](https://your-live-url.com)
- 🎨 [Figma Design Preview](./docs/ui-preview.png)
- 🧩 [Entity Relationship Diagram](./docs/entity-diagram.png)
- 🧪 [CodeSandbox Client](https://codesandbox.io/p/github/aanujkhurana/fullstack-FindMyLease/tree/main/client)

---

## 🧠 Architecture (Mermaid Diagram)

```mermaid
graph TD
  A[Client - Next.js + Mapbox] -->|API Requests| B(API Gateway)
  B --> C[EC2 Backend - Node.js + Prisma]
  C --> D[RDS - PostgreSQL]
  C --> E[S3 - Image Storage]
  C --> F[Cognito - Auth]
  C --> G[VPC - Network]
