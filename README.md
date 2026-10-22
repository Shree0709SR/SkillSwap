# SkillSwap – Your Skills. Your Currency.

> **Full-Stack Peer-to-Peer Skill Exchange Platform**  
> **SDG Alignment: UN Sustainable Development Goal 8 – Decent Work and Economic Growth**

---

## 1. Problem Statement

Many students and young individuals possess valuable skills—such as Python programming, web development, graphic design, spreadsheet modeling, or video editing—but cannot always afford costly commercial tutoring or paid courses to learn complementary skills. At the same time, finding peers interested in mutual skill trading is difficult without a structured, trusted platform.

For example:
- **Person A** knows Python well and wants to learn Photoshop.
- **Person B** is skilled in Photoshop and wants to learn Python.
- Instead of paying money to separate services, SkillSwap allows them to discover each other and exchange their knowledge directly.

---

## 2. Proposed Solution

**Core Concept:** *Exchange skills instead of money.*

SkillSwap connects users based on:
1. **Skills they can offer** (what they can teach).
2. **Skills they want** (what they want to learn).
3. **Availability schedule** (when they can meet/collaborate).

SkillSwap provides a complete, working skill-matching engine, responsive web interface, and barter exchange request workflow.

---

## 3. SDG 8 Alignment

**UN Sustainable Development Goal 8: Decent Work and Economic Growth**  
- **Accessible Skill Development (Target 8.6):** Democratizes vocational, digital, and technical skill acquisition by eliminating financial barriers.
- **Peer-to-Peer Collaborative Learning:** Fosters peer mentorship, self-efficacy, and continuous lifelong education.
- **Opportunity Creation:** Equips students with diverse multidisciplinary capabilities, directly enhancing employability and entrepreneurship.
- **Better Utilization of Existing Human Capital:** Allows students to unlock the latent value of their existing expertise.

---

## 4. System Architecture

```text
┌─────────────────────────────────────────────────────────────┐
│                       Frontend (Vite)                       │
│     React 18 + TypeScript + Tailwind CSS + Lucide Icons     │
│             State: React Context + Axios Client             │
└──────────────────────────────┬──────────────────────────────┘
                               │
                       HTTP / REST APIs
                               │
┌──────────────────────────────▼──────────────────────────────┐
│                    Backend (Node.js & Express)              │
│       REST Controllers + JWT Auth + Rule-Based Matching     │
└──────────────────────────────┬──────────────────────────────┘
                               │
                       Mongoose ODM
                               │
┌──────────────────────────────▼──────────────────────────────┐
│                  Database (MongoDB / Memory DB)             │
│            Collections: Users & ExchangeRequests            │
└─────────────────────────────────────────────────────────────┘
```

---

## 5. Technology Stack

- **Frontend:**
  - **React.js 18** with **TypeScript**
  - **Vite** (ultra-fast build tool)
  - **Tailwind CSS** (modern design tokens & responsive utilities)
  - **React Router v6** (client-side routing & route protection)
  - **Axios** (API requests with automatic JWT bearer interceptor)
  - **Lucide React** (modern iconography)
- **Backend:**
  - **Node.js** with **Express.js** (REST API)
  - **JWT (JSON Web Tokens)** for stateless user authentication
  - **Bcrypt.js** for cryptographic password hashing
  - **CORS** & environment variables
- **Database:**
  - **MongoDB** & **Mongoose ODM**
  - Includes **automatic embedded in-memory fallback** for 100% zero-configuration local demos if local MongoDB is not running.

---

## 6. Rule-Based Matching Algorithm (50 + 30 + 20)

SkillSwap intentionally uses a transparent, explainable **rule-based algorithm** instead of opaque black-box machine learning.

The match score is calculated out of **100 points**:

$$\text{Match Score} = \text{Rule 1 (50 pts)} + \text{Rule 2 (30 pts)} + \text{Rule 3 (20 pts)}$$

| Rule | Condition | Points Awarded |
| :--- | :--- | :---: |
| **Rule 1: Offered Skill Match** | User A offers something User B wants to learn | **+50 points** |
| **Rule 2: Wanted Skill Match** | User A wants something User B offers to teach | **+30 points** |
| **Rule 3: Availability Match** | Both users share at least one schedule window or are flexible | **+20 points** |
| **Maximum Score** | Perfect bilateral complementarity | **100% Match** |

### Concrete Example:
- **Shashank (Demo User):**
  - Offers: `Python`, `JavaScript`
  - Wants: `Photoshop`, `UI Design`
  - Availability: `Weekends`
- **Ananya Sharma:**
  - Offers: `Photoshop`, `UI Design`
  - Wants: `Python`
  - Availability: `Weekends`
- **Calculation:**
  - `Python` $\rightarrow$ `Python` (Rule 1): **+50 pts**
  - `Photoshop` $\rightarrow$ `Photoshop` (Rule 2): **+30 pts**
  - `Weekends` $\rightarrow$ `Weekends` (Rule 3): **+20 pts**
  - **Total:** $50 + 30 + 20 = \mathbf{100\%}$ (**Perfect Match**)

---

## 7. Platform Features Implemented

1. **Modern Startup Landing Page:**
   - Hero section with live barter exchange visual
   - Problem and solution breakdown
   - Step-by-step workflow (4 steps)
   - Explainable matching engine highlight card
   - Dedicated UN SDG 8 alignment section
2. **Authentication:**
   - User Registration with password confirmation and field validation
   - User Login with JWT generation and token persistence
   - One-click demo login buttons for seamless evaluator demonstration
3. **User Profile & Skills Portfolio:**
   - Profile completion progress meter (e.g., 80% / 100%)
   - Multi-select "Skills I Offer" with custom skill tagging
   - Multi-select "Skills I Want" with common suggestion chips
   - Multi-select Availability options (Weekdays, Weekends, Evenings, Morning, Flexible)
4. **Dashboard:**
   - Personalized welcome banner
   - Overview metrics (Matches, Received Requests, Sent Requests)
   - Skills summary card
   - Top recommended matches sorted by score
5. **Find Matches Page:**
   - Real-time search query by skill name
   - Filtering by availability schedule
   - Filtering by minimum match score threshold
   - Match cards showing skill complementarity badges and availability
6. **Exchange Request Workflow:**
   - Interactive modal selecting offered skill from user profile and wanted skill from recipient profile
   - Custom personal message input
   - "My Requests" dashboard with **Received** and **Sent** tabs
   - Accept / Reject functionality with instant UI state updates

---

## 8. Presentation Demo Walkthrough (Step-by-Step)

Follow this exact sequence for your college evaluation:

1. **Step 1: Open Application**
   - Navigate to `http://localhost:5173`.
   - Tour the Landing Page, highlighting the **SDG 8 Alignment** and **How It Works** section.
2. **Step 2: Sign In as Demo Account**
   - Click **Login** or click the quick demo chip:
     - **Email:** `demo@skillswap.com`
     - **Password:** `Demo@123`
3. **Step 3: Review Dashboard & Profile**
   - Point out the **Profile Completion Bar** and **My Skills** (Offers: *Python, JavaScript*; Wants: *Photoshop, UI Design*; Availability: *Weekends*).
4. **Step 4: Navigate to "Find Matches"**
   - Click **Find Matches** in the navbar.
   - Point out **Ananya Sharma** at the top of the list displaying **100% Match**.
5. **Step 5: Explain the Algorithm Score**
   - Click **View Profile** on Ananya's card.
   - Explain the breakdown in the modal:
     - $+50$ pts: You offer Python which she wants.
     - $+30$ pts: She offers Photoshop which you want.
     - $+20$ pts: Both are available on Weekends.
     - Total = **100%**.
6. **Step 6: Send Exchange Request**
   - Click **Exchange** or **Send Exchange Request**.
   - Choose:
     - You offer: `Python`
     - You want: `Photoshop`
     - Personal message is auto-filled.
   - Click **Send Request**.
7. **Step 7: Check "My Requests" (Sent Tab)**
   - Navigate to **My Requests** $\rightarrow$ **Sent Requests**.
   - See the request to Ananya marked as **Pending Response**.
8. **Step 8: Switch User to Ananya**
   - Click **Logout**.
   - Go to **Login** and click the quick login button for **Ananya Sharma** (`ananya@skillswap.com` / `Demo@123`).
9. **Step 9: View Received Request**
   - Navigate to **My Requests** $\rightarrow$ **Received Requests**.
   - See the inbound request from Shashank offering Python for Photoshop.
10. **Step 10: Accept Request**
    - Click **Accept Request**.
    - The request instantly transitions to **Accepted** with a green badge.

---

## 9. Demo Accounts Seeded in System

| Name | Email | Password | Skills Offered | Skills Wanted | Availability |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Shashank (Demo User)** | `demo@skillswap.com` | `Demo@123` | Python, JavaScript | Photoshop, UI Design | Weekends |
| **Ananya Sharma** | `ananya@skillswap.com` | `Demo@123` | Photoshop, UI Design | Python | Weekends |
| **Rahul Verma** | `rahul@skillswap.com` | `Demo@123` | Python, Java | Photoshop | Weekends |
| **Arjun Patel** | `arjun@skillswap.com` | `Demo@123` | Video Editing | React | Evenings |
| **Sneha Rao** | `sneha@skillswap.com` | `Demo@123` | React, JavaScript | Video Editing | Evenings |
| **Karthik Nair** | `karthik@skillswap.com` | `Demo@123` | Excel, Data Analysis | Public Speaking | Weekdays |

---

## 10. Installation and Running Locally

### Prerequisites
- Node.js (v18+)
- npm (v9+)

### Quick Start (Single Command)

From the project root directory:

```bash
# 1. Install all dependencies (root, backend, frontend)
npm run install:all

# 2. Run both Backend and Frontend concurrently
npm run dev
```

- **Frontend:** `http://localhost:5173`
- **Backend API:** `http://localhost:5000`

---

### Running Separately

#### Backend
```bash
cd backend
npm install
npm run seed     # Seeds demo accounts
npm run dev      # Starts server on http://localhost:5000
```

#### Frontend
```bash
cd frontend
npm install
npm run dev      # Starts Vite on http://localhost:5173
```

---

## 11. Future Scope – Phase 2

The following items are planned for future engineering phases:

- **AI-Powered Natural Language Matching:** Embedding models to match synonymous skills (e.g. "ML" $\leftrightarrow$ "Machine Learning").
- **Skill Verification & Badges:** Peer quizzes or portfolio links to verify skill level before trading.
- **In-App Real-Time Chat & Video:** Integrated WebRTC / Socket.io for live peer learning sessions.
- **User Ratings & Reviews:** Post-exchange reputation score and student endorsements.
- **Push & Email Notifications:** Alerts when exchange requests are sent, accepted, or scheduled.
- **Campus & Community Chapters:** Geolocation filters to meet students from the same university or department.
- **Admin & Analytics Dashboard:** University-level impact metrics measuring hours learned and SDG 8 progress.

---

## 12. License & Academic Attribution
Developed as an academic demonstration for college mini-project evaluation. Aligned with UN Sustainable Development Goal 8 (Decent Work & Economic Growth).
