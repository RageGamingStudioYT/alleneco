[README.md](https://github.com/user-attachments/files/32694679/README.md)
# alleneco# ALLEN EcoLearn 2040

**"Learn. Act. Earn. Build a Greener Campus."**

A hackathon prototype for ALLEN's *Mission Campus 2040* challenge, combining three tracks into one connected student-life system.

## 1. Problem

Campus sustainability programmes fail because learning, action and reward live in separate places. Students learn about climate in class, recycle in a different app, and see no personal benefit from either. Nothing closes the loop.

## 2. Solution

EcoLearn 2040 makes one loop: a student learns a concept, applies it as a campus mission, the Green Meter measures the simulated impact, the student earns Carbon Coins, and spends them in the Smart Canteen — which updates campus-wide statistics.

```
LEARN → ACT → EARN → SPEND → IMPACT
```

## 3. EduTech component — Bhasha Learn

- Structured lesson (Solar Energy, Physics, Class 9) with five sections
- AI tutor with Ask AI / Summarise / Explain Simply
- Multilingual: English, Hindi, Kannada
- 5-question generated quiz; 5/5 → +10 CC, 4/5 → +8 CC, 3/5 → +5 CC
- Rewards are only granted when a student beats their previous best score, preventing repeat farming

## 4. GreenTech component — Green Meter

- Simulated campus telemetry: solar generation, energy saved, water saved, recycling rate
- Four sustainability missions with simulated verification
- Completing a mission records environmental impact and raises the personal and campus green score
- All sensor values are clearly labelled **SIMULATED CAMPUS DATA**

## 5. FinTech component — Carbon Wallet

- Fictional campus wallet holding Carbon Coins (not real currency, no banking connection)
- Transaction history of every earn and spend
- Smart Canteen with four items; purchases are simulated and blocked when the balance is insufficient

## 6. AI usage

The AI tutor runs in **mock mode by default** and requires no API key. Predefined multilingual explanations, summaries and simplified explanations are served locally, and the quiz uses local question data. Optional environment variables allow a live provider:

```
GEMINI_API_KEY=
GROK_API_KEY=
```

Keys are never read in frontend source; any live call would run server-side. If a provider is unavailable, the app automatically falls back to local content and never crashes.

## 7. Architecture

```
Student
   ↓
EcoLearn
   ↓
AI Learning
   ↓
Lessons + Quizzes
   ↓
Green Missions
   ↓
Green Meter
   ↓
Carbon Coins
   ↓
Carbon Wallet
   ↓
Smart Canteen
   ↓
Campus Impact
```

Implementation: React 19 + TypeScript on TanStack Start (Vite), Tailwind CSS v4, Lucide icons, Recharts. A single `EcoProvider` context holds all shared state (coins, green score, missions, transactions, activity) and persists it to `localStorage`, so every screen reads and writes the same live loop.

## 8. Mock data explanation

All data is simulated. Carbon Coins have no monetary value, environmental figures are illustrative estimates rather than measurements, and no real sensors, banking systems or health data are connected. No sensitive student data is collected.

## 9. How the three tracks connect

Completing a quiz credits coins to the same wallet a mission credits. The wallet funds canteen purchases. Every mission raises the green score shown on the Green Meter and the campus impact dashboard. Remove any one track and the loop breaks — that is the point.

## 10. Future scalability to 100 campuses

Each campus becomes a tenant with its own Green Meter feed and leaderboard; shared lesson content and AI tutoring are served centrally while wallets and missions are scoped per campus. Real IoT meters would replace the simulated telemetry, and inter-campus green score rankings would drive competition across the network.

## 11. Hackathon AI-tool disclosure

This prototype was built with AI assistance (Lovable) for code generation, UI implementation and content drafting. All product decisions, architecture and the track integration concept are authored by the team.
