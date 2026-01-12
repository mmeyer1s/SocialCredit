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
4. **Public Posts & Announcements**
    - Make public announcements and apologies

### **User Flow**

1. **User Profile Page**:
    - View details about your own social credit, including public votes and comments.
    - Profile pictures and user bio
2. **Search Engine**:
    - Search for other users by name or username to find their account on the platform.
    - Photo facial recognition scanner to identify the accounts associated with people in real life even if they don't want to give it to you. Also doubles to prevent impersonators/alt accounts on the platform
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

- **Programming Language:** TypeScript
- **Frontend (Web):** React + Vite + Tailwind CSS
- **Mobile:** React Native
- **Backend / API:** Node.js
- **Database:** PostgreSQL
- **Search:** PostgreSQL Full-Text Search
- **Authentication:** JWT

### **2. Architecture**

- **Client–Server Architecture:** Web/mobile clients communicate with a centralized API.
and database access (repositories/models).
- **Modular Pages:** Profile, Search, and Leaderboard as separate feature modules.


### **4. Security and Performance**

- **Authentication Security:** Password hashing, email/phone verification, and secure session/token handling.
- **Privacy Controls:** Anonymous votes are stored for counting but voter identity is never returned in public API responses.