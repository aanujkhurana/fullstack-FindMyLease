<h1 align="center">🏢 fullstack-FindMyLease</h1>

<p align="center">
  <strong>An enterprise-grade rental property management platform</strong><br/>
  Built with <code>Next.js</code>, <code>AWS</code>, and <code>PostgreSQL</code> for seamless listings, secure logins, and tenant/manager management.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Next.js-13+-black?logo=next.js" />
  <img src="https://img.shields.io/badge/AWS-Deployed-orange?logo=amazonaws" />
  <img src="https://img.shields.io/badge/PostgreSQL-Database-blue?logo=postgresql" />
  <img src="https://img.shields.io/badge/Prisma-ORM-lightblue?logo=prisma" />
  <img src="https://img.shields.io/badge/License-MIT-green.svg" />
</p>

---

## 🚀 Overview

**FindMyLease** is a fullstack property rental management platform for real estate managers and tenants. It features interactive listings, authentication, image uploads, and admin tools — all cloud-hosted and production-ready.

---

## 🖼️ Live Demo & Preview

> 🌐 [Live Site](https://your-live-url.com)  
> 🎬 [Figma Design Preview](./docs/ui-preview.png)  
> 🧩 [Entity Relationship Diagram](./docs/entity-diagram.png)

---

## 📂 Project Structure

```bash
fullstack-FindMyLease/
├── client/         # Next.js frontend (hosted on Amplify)
├── server/         # Backend (hosted on EC2)
│   ├── prisma/     # DB schema, seed, and migrations
│   └── api/        # REST/GraphQL endpoints
├── docs/           # Architecture, ERD, Figma UI previews
└── README.md
