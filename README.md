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

## 🧠 Architecture

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

## 🧪 Local Development Setup

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/aanujkhurana/fullstack-FindMyLease.git
cd fullstack-FindMyLease
```

---

### 2️⃣ Environment Setup

#### 🔹 client/.env

```env
NEXT_PUBLIC_API_BASE_URL=http://localhost:90
NEXT_PUBLIC_AWS_COGNITO_USER_POOL_ID=
NEXT_PUBLIC_AWS_COGNITO_USER_POOL_CLIENT_ID=
NEXT_PUBLIC_MAPBOX_ACCESS_TOKEN=
```

#### 🔹 server/.env

```env
DATABASE_URL="postgresql://postgres:0000@localhost:5432/findmylease?schema=public"
S3_BUCKET_NAME="findmylease-s3-image"
PORT=90
```

> 🔁 Both `client` and `server` have their own `.env` files

---

### 3️⃣ Install Dependencies

> The project uses `.npmrc` with `legacy-peer-deps=true` to allow React 19 compatibility with older packages.

#### 🔹 client

```bash
cd client
npm install
```

#### 🔹 server

```bash
cd ../server
npm install
```

---

### 4️⃣ Prisma Setup

In `server/`:

```bash
npx prisma migrate reset
npm run prisma:generate
npx prisma migrate dev --name init
npm run seed
```

---

### 5️⃣ Start the Backend (via PM2)

In `server/`:

```bash
pm2 start ecosystem.config.js
```

> Port will be set to `90` from `.env`

---

### 6️⃣ Start the Frontend

In a new terminal:

```bash
cd client
npm run dev
```

> Frontend will be live at: `http://localhost:3000`  
> Backend API served from: `http://localhost:90`

---

## 🔁 User Flow

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

## ✅ Tech Stack

- **Frontend**: Next.js 13+, Mapbox, Cognito Auth, Tailwind CSS
- **Backend**: Node.js, Express, Prisma ORM
- **Database**: PostgreSQL (RDS)
- **Cloud**: AWS S3, EC2, Amplify, API Gateway, VPC, Cognito
- **Dev Tools**: PM2, Postman, Figma, pgAdmin, Mermaid
- **Bonus**: `.npmrc` for React 19 legacy support

---

## 🤝 Contributing

To contribute to **FindMyLease**, follow these steps:

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/aanujkhurana/fullstack-FindMyLease.git
cd fullstack-FindMyLease
```

This will download the full project including both frontend (`client`) and backend (`server`) folders.

---

### 2️⃣ Set Up Environment Variables

You'll need to create two `.env` files:

#### 🔹 `client/.env`

```env
NEXT_PUBLIC_API_BASE_URL=http://localhost:90
NEXT_PUBLIC_AWS_COGNITO_USER_POOL_ID=
NEXT_PUBLIC_AWS_COGNITO_USER_POOL_CLIENT_ID=
NEXT_PUBLIC_MAPBOX_ACCESS_TOKEN=
```

#### 🔹 `server/.env`

```env
DATABASE_URL="postgresql://postgres:0000@localhost:5432/findmylease?schema=public"
S3_BUCKET_NAME="findmylease-s3-image"
PORT=90
```

Make sure your local database and AWS credentials match these variables.

---

### 3️⃣ Install Dependencies

Install all packages for both the frontend and backend:

#### 🔹 Frontend

```bash
cd client
npm install
```

#### 🔹 Backend

```bash
cd ../server
npm install
```

> Note: This project includes a `.npmrc` file with `legacy-peer-deps=true` for React 19 compatibility.

---

### 4️⃣ Start the Backend

From the `server/` directory:

```bash
pm2 start ecosystem.config.js
```

Or if you want to use `npm` directly for development:

```bash
cd server
npm run dev
```

---

### 5️⃣ Start the Frontend

From the `client/` directory:

```bash
cd client
npm run dev
```

The app will now be running locally at:

- Frontend: `http://localhost:3000`  
- Backend API: `http://localhost:3001`

👏 You're all set! Submit a pull request once you're done contributing.

---

## 📄 License

Licensed under [MIT License](./LICENSE)

---

> Built with ☁️ and ❤️.
