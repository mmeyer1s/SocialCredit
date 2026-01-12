# Social Credit
# Majority Rule Design + Tech Spec

---

# **App**

## **Overview**

Majority Rule is a web and phone app where users can search through profiles of different people, and press a button to upvote or downvote that person. Unlike social media where users can only choose to follow or not follow, users would be able to additionally downvote someone, publicly shaming them.

## **1. Project Choice**

- **Option**: Web App Design
- **App Title**: “Majority Rule”

---

## **2. Purpose of the Game**

- **Goal**: Provide a platform for people to endorse or express their anger towards an individual
- **Target Audience**:
    - **Age Group**: Ages 16+
    - **Interests**: Pretty much everyone

---

## **3. Design**

# **A. Functionality**

### **Core Features**

1. **Profile Search**:
    - Account based, profile system to easily find others on the platform.
2. **Permanent Upvote/Downvote Buttons**:
    - When one user votes on another, that vote is permanent until changed. Nobody can have more than one vote at a time per person
3. **Anonymous or Public Votes**:
    - When users cast a vote, they can either make it public for other users (and the user being voted on) to view, or anonymous, hiding it from other users
3. **Comments**:
    - In addition to votes, users can leave comments on other users, potentially describing a reason for their vote.

### **User Flow**

1. **User Profile Page**:
    - View details about your own social credit, including public votes and comments.
2. **Search Engine**:
    - Search for other users by name or username to find their account on the platform.
    - Photo facial recognition scanner to identify the accounts associated with people in real life even if they don't want to give it to you.
3. **Leaderboard Page**:
    - View the accounts with the greatest numbers of upvotes and downvotes across all users on the platform


### **Interactive Elements**

- **Nav Bar**: Switch through pages with a bottom navigation bar
- **Pages**: Profile, Search, and Leaderboard pages

# B. Aesthetics


### **Visual Style**

- **Theme**: Modern simple UI, similar to Instagram or other various social media platforms

### **Color Scheme**

- **Palette**: Blue, White, and gray theme
    - **Background**: Light gray page backgrounds
    - **Buttons and Elements**: Dark Gray with blue highlights

### **Typography**

- **Font Style**: Open Sans font

### **Layout**

- **Screen Arrangement**:
    - **Navbar**: The navbar sits at the bottom of the screen for mobile, or on the left side of the screen for computer users.
    - **Personal and Other Profiles**: Scrollable from top to bottom to view data


# **Technical Specifications**

### **1. Technology Stack**

- **Programming Language:** TypeScript (JavaScript-compatible)
- **Frontend (Web):** React + HTML5 + CSS3 (or Tailwind CSS)
- **Mobile:** React Native (iOS/Android) **or** Progressive Web App (PWA)
- **Backend / API:** Node.js (Express or NestJS)
- **Database:** PostgreSQL
- **Search:** PostgreSQL Full-Text Search **or** Meilisearch/Elasticsearch
- **Authentication:** JWT (access/refresh) or secure cookie sessions
- **Hosting / Deployment:** Vercel (frontend) + Render/Fly.io/AWS/GCP (API + DB)

### **2. Architecture**

- **Client–Server Architecture:** Web/mobile clients communicate with a centralized API.
- **MVC / Service Layer Pattern:** Separate routing/controllers, business logic (services), and database access (repositories/models).
- **Modular Pages:** Profile, Search, and Leaderboard as separate feature modules.

### **3. Data Model**

- **Users:** Objects with properties for `id`, `username`, `displayName`, `avatarUrl`, `bio`, and timestamps.
- **Votes:** Objects with `voterId`, `targetUserId`, `value` (+1 / -1), `visibility` (public/anonymous), and timestamps.
  - **Constraint:** One vote maximum per `(voterId, targetUserId)` (unique pair).
- **Comments:** Objects with `authorId`, `targetUserId`, `text`, `visibility` (public/anonymous), and timestamps.
- **Leaderboard Aggregates (Optional):** Cached totals for `upvotes`, `downvotes`, and `netScore` per user for fast ranking.

### **4. Security and Performance**

- **Authentication Security:** Password hashing (bcrypt/argon2), email/phone verification, and secure session/token handling.
- **Rate Limiting & Abuse Prevention:** Limit votes/comments/search requests per minute to reduce spam and botting.
- **Privacy Controls:** Anonymous votes are stored for counting but voter identity is never returned in public API responses.
- **Database Integrity:** Use indexes and transactional updates so vote toggles remain consistent and accurate.
- **Performance Optimization:** Pagination for search/comments/leaderboards and caching for frequently accessed profiles/leaderboards.

### **5. Specific Functionalities**

### a. Profile Search

- **Specification:** Implement search by username/display name with pagination and optional fuzzy matching. Use indexed queries and return results ranked by relevance.

### b. Voting System (Permanent Upvote/Downvote)

- **Specification:** Enforce one vote per user per target account. If a vote exists, update it; otherwise create it. Vote remains until changed by the voter.

### c. Anonymous or Public Votes

- **Specification:** Store vote visibility as a field. Public votes may appear on the target profile with voter identity; anonymous votes only affect totals and do not reveal who voted.

### d. Comments

- **Specification:** Allow users to leave comments on profiles, optionally anonymous. Provide moderation tools such as reporting, filtering, and pagination.

### e. Leaderboard

- **Specification:** Rank users by total upvotes, total downvotes, and net score. Use cached aggregates updated on vote changes to keep leaderboard queries fast.

### f. User Interface

- **Specification:** Responsive UI with bottom navigation on mobile and left-side navigation on desktop. Pages include Profile, Search, and Leaderboard, with consistent components and accessibility-friendly design.
