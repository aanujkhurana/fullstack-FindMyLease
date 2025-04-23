<h1 align="center">FindMyLease - Rental Management System 🏢</h1>

<p align="center">
  <strong>An enterprise-grade rental property management platform</strong><br/>
  Built with <a href="https://nextjs.org/" target="_blank"><code>Next.js</code></a>, 
  <a href="https://aws.amazon.com/" target="_blank"><code>AWS</code></a>, and 
  <a href="https://www.postgresql.org/" target="_blank"><code>PostgreSQL</code></a> for seamless listings, secure authentication, and tenant/manager management.
</p>

<p align="center">
  <img src="https://img.shields.io/github/languages/top/aanujkhurana/fullstack-FindMyLease?color=blue&style=flat-square" />
  <img src="https://img.shields.io/badge/Next.js-13+-black?logo=next.js" />
  <img src="https://img.shields.io/badge/AWS-Deployed-orange?logo=amazonaws" />
  <img src="https://img.shields.io/badge/PostgreSQL-Database-blue?logo=postgresql" />
  <img src="https://img.shields.io/badge/Prisma-ORM-lightblue?logo=prisma" />
  <img src="https://img.shields.io/badge/License-MIT-green.svg" />
</p>

## 🚀 Tech Stack

- **Frontend**: [Next.js 13+](https://nextjs.org/), [Mapbox](https://www.mapbox.com/), [Amazon Cognito](https://aws.amazon.com/cognito/), [Tailwind CSS](https://tailwindcss.com/)
- **Backend**: [Node.js](https://nodejs.org/), [Express](https://expressjs.com/), [Prisma ORM](https://www.prisma.io/)
- **Database**: [PostgreSQL (RDS)](https://aws.amazon.com/rds/postgresql/)
- **Cloud Infrastructure**: [AWS S3](https://aws.amazon.com/s3/), [EC2](https://aws.amazon.com/ec2/), [Amplify](https://aws.amazon.com/amplify/), [API Gateway](https://aws.amazon.com/api-gateway/), [VPC](https://aws.amazon.com/vpc/), [Cognito](https://aws.amazon.com/cognito/)
- **Dev Tools**: [PM2](https://pm2.keymetrics.io/), [Postman](https://www.postman.com/), [Figma](https://www.figma.com/), [pgAdmin](https://www.pgadmin.org/), [Mermaid](https://mermaid.js.org/)
- **Extras**: `.npmrc` for [React 19](https://react.dev/) legacy support

## ✨ Features

- 🔐 Secure login with AWS Cognito
- 🏠 Property listings with location via Mapbox
- 📷 Image uploads to AWS S3
- 👥 Role-based access for tenants and managers
- 📊 Admin dashboard with analytics (planned)
- 🗂️ Organized backend via Node.js and Prisma
- ☁️ Fully deployed using AWS services (Amplify, EC2, RDS, S3, API Gateway)


## 🔗 Quick Links

- 🌐 [Live Demo](https://main.dykb851k9y38f.amplifyapp.com)
- 🎨 [UI Design](./docs/ui-preview.jpg)
- 📊 [Entity Relationship Diagram](./docs/entity-diagram.jpg)


## 🏗️ Architecture

```mermaid
graph TD
  A[Client - Next.js + Mapbox] -->|API Requests| B(API Gateway)
  B --> C[EC2 Backend - Node.js + Prisma]
  C --> D[RDS - PostgreSQL]
  C --> E[S3 - Image Storage]
  C --> F[Cognito - Auth]
  C --> G[VPC - Network]
```

## 🔄 User Flow

```mermaid
sequenceDiagram
  participant User
  participant Client
  participant Backend
  participant DB
  participant Cognito

  User->>Client: Sign up / login
  Client->>Cognito: Authenticate user
  Cognito-->>Client: Token
  Client->>Backend: Fetch listings
  Backend->>DB: Query
  DB-->>Backend: Return results
  Backend-->>Client: Send data
```

## 🧭 Entity Flow Diagram

```mermaid
flowchart TD
  Manager --> Applications
  Manager --> Property

  Property --> Location
  Property --> Leases
  Leases --> Payments

  Applications -->|Approved?| Decision{Approved?}
  Decision -->|YES| LeadsToLease

  LeadsToLease --> Tenant
  Location --> Tenant
  Tenant --> CurrentResidences

  LeadsToLease --> Payments
```


## 📁 Folder Structure

```bash
fullstack-FindMyLease/
├── client/         # Next.js frontend (Amplify)
│   ├── .env        # Frontend env vars
│   └── .npmrc      # React 19 compatibility
├── server/         
│   ├── service/    # Node.js backend source code
│   ├── prisma/     # DB schema & seeds
│   ├── .env        # Server env vars
│   └── ecosystem.config.js  # PM2 config
└── docs/           # Diagrams, UI mocks
```

## 🧪 Local Development Setup

### 1. Clone the Repository

```bash
git clone https://github.com/aanujkhurana/fullstack-FindMyLease.git
cd fullstack-FindMyLease
```

### 2. Configure Environment Variables

#### `client/.env`

```env
NEXT_PUBLIC_API_BASE_URL=http://localhost:3001
NEXT_PUBLIC_AWS_COGNITO_USER_POOL_ID=
NEXT_PUBLIC_AWS_COGNITO_USER_POOL_CLIENT_ID=
NEXT_PUBLIC_MAPBOX_ACCESS_TOKEN=
```

#### `server/.env`

```env
DATABASE_URL="postgresql://postgres:0000@localhost:5432/findmylease?schema=public"
S3_BUCKET_NAME="findmylease-s3-image"
PORT=3002
```

### 3. Install Dependencies

```bash
cd client && npm install
cd ../server && npm install
```

---

### 4. Prisma Setup (server)

```bash
npx prisma migrate reset
npm run prisma:generate
npx prisma migrate dev --name init
npm run seed
```

### 5. Start Backend

```bash
pm2 start ecosystem.config.js
# or
npm run dev
```

> Server runs on port `3002`.


### 6. Start Frontend

In a new terminal:

```bash
cd client
npm run dev
```

> App runs at [http://localhost:3001](http://localhost:3001)


## 🤝 Contribution Guide

To contribute:

1. Fork and clone the repository
2. Create a new branch
3. Make your changes
4. Submit a pull request

---

## 📜 License

This project is licensed under the [MIT License](./LICENSE)

---

> Built with ☁️ cloud power and ❤️.
