# CampusMemory

> A student-first campus information hub that brings notices, events, discussions, certificates, and an AI campus assistant into one place.

## 🚀 About

CampusMemory is a student-focused web application designed to make important campus information easier to discover, understand, and act on.

Instead of searching through scattered posters, messages, and announcements, students can use one dashboard to find campus notices, event details, deadlines, rooms, discussions, and certificates.

The project was built for the **AWS Student Builder Hackathon 2026** under the **Open Innovation** theme.

## 🎯 Problem

Students often receive important information through different channels such as posters, WhatsApp messages, college announcements, and event pages. This makes it easy to miss:

- Registration deadlines
- Event dates and venues
- Workshops and opportunities
- Important campus notices
- Links and other useful details

CampusMemory aims to provide a single, searchable place for this information.

## 💡 Solution

CampusMemory combines a clean student dashboard with a backend-powered information system.

Students can:

- Browse campus notices and events
- View event dates, deadlines, venues, and registration links
- Search campus information
- Ask Campus Copilot questions about available campus notices
- Participate in campus discussions
- View available campus spaces
- Generate participation certificates using their verified student profile
- Sign in securely with their student account

Administrators can manage campus information and publish notices with poster images.

## ✨ Key Features

### Campus Dashboard
A central dashboard for important campus information, upcoming events, deadlines, and student resources.

### Notices & Events
Notices can contain:

- Title
- Category
- Description
- Event date
- Deadline
- Venue
- Registration URL
- Source
- Poster image

### Campus Copilot 🤖
An AI assistant designed to answer student questions using available campus information.

Example questions:

> "What workshops are happening this week?"

> "When is the registration deadline?"

> "Where is the event happening?"

The architecture uses an AWS API layer and Lambda backend with Amazon Bedrock planned as the model layer.

### Student Authentication
Authentication is handled through Supabase Auth, with student profile information linked to the authenticated account.

### Discussions
Students can create discussions and replies around campus topics.

### Certificates
Students can generate participation certificates using information from their verified student profile.

### Admin Notice Management
Authorized administrators can add, edit, delete, and publish campus notices, including poster uploads.

## 🏗️ Architecture

```text
                         ┌─────────────────────┐
                         │     CampusMemory    │
                         │      Web App        │
                         └──────────┬──────────┘
                                    │
                   ┌────────────────┴────────────────┐
                   │                                 │
                   ▼                                 ▼
          ┌─────────────────┐               ┌─────────────────┐
          │    Supabase     │               │  API Gateway    │
          │ Auth + Database │               │      HTTP API   │
          └─────────────────┘               └────────┬────────┘
                                                     │
                                                     ▼
                                            ┌─────────────────┐
                                            │     AWS Lambda  │
                                            │ Campus Copilot  │
                                            └────────┬────────┘
                                                     │
                                                     ▼
                                            ┌─────────────────┐
                                            │ Amazon Bedrock  │
                                            │   AI Model      │
                                            └─────────────────┘
```

## ☁️ AWS Services

CampusMemory uses AWS for the AI assistant backend:

| AWS Service | Purpose |
|---|---|
| **AWS Lambda** | Runs the Campus Copilot backend without managing servers |
| **Amazon API Gateway** | Provides the HTTP API used by the web application |
| **Amazon Bedrock** | Intended AI model layer for generating Campus Copilot responses |

The application also uses **Supabase** for authentication, PostgreSQL data, and notice poster storage.

## 🛠️ Technology Stack

### Frontend

- HTML
- CSS
- JavaScript
- Vite

### Backend / Data

- Supabase Auth
- Supabase PostgreSQL
- Supabase Storage

### AWS

- AWS Lambda
- Amazon API Gateway
- Amazon Bedrock

## 🔐 Authentication & Authorization

CampusMemory uses Supabase Authentication for student sign-in.

Administrative access is checked against an `admins` table, while student information is stored in a linked `students` table.

Example student profile information includes:

- Full name
- Enrollment ID
- Department
- Year

## 📁 Project Structure

```text
NEXUS-main/
├── index.html
├── package.json
├── .gitignore
├── README.md
└── src/
    ├── main.js
    ├── style.css
    ├── config/
    │   └── supabase.js
    └── services/
        ├── authService.js
        ├── discussionService.js
        └── noticeService.js
```

## ⚙️ Local Setup

### 1. Clone the repository

```bash
git clone <repository-url>
cd NEXUS-main
```

### 2. Install dependencies

```bash
npm install
```

### 3. Configure environment variables

Create a `.env.local` file:

```env
VITE_SUPABASE_URL=your_supabase_project_url
VITE_SUPABASE_PUBLISHABLE_KEY=your_supabase_publishable_key
```

Do **not** commit `.env.local` or other secrets to GitHub.

### 4. Start the development server

```bash
npm run dev
```

The application will be available at the local Vite development URL shown in the terminal.

### 5. Build for production

```bash
npm run build
```

## 🔭 Future Scope

CampusMemory can be extended with:

- Automatic poster/PDF text extraction
- Automatic event and deadline extraction
- Semantic search across campus documents
- Source-grounded AI answers with the original notice displayed beside the answer
- Push notifications for important deadlines
- Personalized student feeds
- College-wide document ingestion
- Mobile application support

## 🧠 Trust & AI Safety

Campus information can directly affect students, especially when it involves dates, deadlines, venues, and registration links.

The intended Campus Copilot experience therefore prioritizes answers grounded in available campus information rather than allowing the assistant to invent missing details.

Where information cannot be confidently determined from the available source, the system should make that limitation clear.

## 👥 Team

**AWS Student Builder Hackathon 2026**

Team members:

- Linus Aaron
- Anurag Kumar
- Prajakta Sapale
- Team Member 4

> Replace the final placeholder with the fourth team member's name before submitting.

## 📜 Hackathon

**Event:** AWS Student Builder Hackathon 2026  
**Theme:** Open Innovation  
**Project:** CampusMemory

---

Built with ❤️ by students, for students.
