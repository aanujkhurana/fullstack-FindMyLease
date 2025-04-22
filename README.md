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


## Quick Links

- 🚀 [Live Site](https://your-live-url.com)
- 🎨 [Figma Design Preview](./docs/ui-preview.png)
- 🧩 [Entity Relationship Diagram](./docs/entity-diagram.png)

---

## Architecture

```mermaid
graph TD
  A[Client - Next.js + Mapbox] -->|API Requests| B(API Gateway)
  B --> C[EC2 Backend - Node.js + Prisma]
  C --> D[RDS - PostgreSQL]
  C --> E[S3 - Image Storage]
  C --> F[Cognito - Auth]
  C --> G[VPC - Network]
```

---

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

---

## Local Development Steps;

### 1. Clone the Repository

```bash
git clone https://github.com/aanujkhurana/fullstack-FindMyLease.git
cd fullstack-FindMyLease
```

### 2. Environment Setup

#### client/.env

```env
NEXT_PUBLIC_API_BASE_URL=http://localhost:3001
NEXT_PUBLIC_AWS_COGNITO_USER_POOL_ID=
NEXT_PUBLIC_AWS_COGNITO_USER_POOL_CLIENT_ID=
NEXT_PUBLIC_MAPBOX_ACCESS_TOKEN=
```

#### server/.env

```env
DATABASE_URL="postgresql://postgres:0000@localhost:5432/findmylease?schema=public"
S3_BUCKET_NAME="findmylease-s3-image"
PORT=3002
```

> 🔁 Both `client` and `server` have their own `.env` files


### 3. Install Dependencies

#### Frontend

```bash
cd client
npm install
```

#### Backend

```bash
cd ./server
npm install
```

---

### 4. Prisma Setup

In `server/`:

```bash
cd server/

npx prisma migrate reset
npm run prisma:generate
npx prisma migrate dev --name init
npm run seed
```

---

### Start the Backend (via PM2 or Npde)

```bash
cd server/

pm2 start ecosystem.config.js
or
npn run dev

```

> Port will be set to `3002` from `.env`

---

### Start the Frontend

In a new terminal:

```bash
cd client
npm run dev
```

> Frontend will be live at: `http://localhost:3001`  
> Backend API served from: `http://localhost:3002`

---

## User Flow

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


---

## Tech Stack

- **Frontend**: Next.js 13+, Mapbox, Cognito Auth, Tailwind CSS
- **Backend**: Node.js, Express, Prisma ORM
- **Database**: PostgreSQL (RDS)
- **Cloud**: AWS S3, EC2, Amplify, API Gateway, VPC, Cognito
- **Dev Tools**: PM2, Postman, Figma, pgAdmin, Mermaid
- **Extra**: `.npmrc` for React 19 legacy support

---

## Contribution

To contribute to **FindMyLease**:

### Clone the Repository

```bash
git clone https://github.com/aanujkhurana/fullstack-FindMyLease.git
cd fullstack-FindMyLease
```
This will download the full project including both frontend (`client`) and backend (`server`) folders.

Create a bracnh
 
Submit a pull request once you're done contributing.

---

## License

Licensed under [MIT License](./LICENSE)

---

> Built with ☁️ and ❤️.
