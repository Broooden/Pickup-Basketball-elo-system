
# Pickup Basketball Elo System

## 🎯 What We’re Trying to Achieve

We are building an **Elo-based matchmaking system** for pickup basketball.  
The goals:

- Use **Elo rating** to create balanced 5v5 teams
- **No performance stats** required — only win/loss results
- Over time, ratings stabilize so **everyone stays around a 50% win rate**
- Similar to chess Elo, but adapted for a team sport

---

## 📌 Known Methodologies

### Chess Elo Basics

Before a match, the system uses the rating difference to calculate the chance each side will win:

- **Win = 1**
- **Draw = 0.5** (not applicable in pickup basketball)
- **Loss = 0**

Expected score formula:

E = 1 / (1 + 10 ^ ((OpponentRating - YourRating) / 400))

---

## 📊 Data Format (Example Use Case)

### Day 0 — Initial Ratings

Curry - 1500  
LeBron - 1500  
Giannis - 1500  
Jokic - 1500  
Tatum - 1500  
Durant - 1500  
Luka - 1500  
Embiid - 1500  
Shai - 1500  
Butler - 1500  

---

## 🏀 Day 1

**Teams**

Team A: Curry, LeBron, Giannis, Jokic, Tatum  
Team B: Durant, Luka, Embiid, Shai, Butler  

**Ratings After Day 1**

Curry - 1507  
LeBron - 1507  
Giannis - 1507  
Jokic - 1507  
Tatum - 1507  
Durant - 1493  
Luka - 1493  
Embiid - 1493  
Shai - 1493  
Butler - 1493  

---

## 🏀 Day 2

**Teams**

Team A: Curry, Tatum, Durant, Embiid, Shai  
Team B: LeBron, Giannis, Jokic, Luka, Butler  

**Game Results**
B wins, B wins, A wins, B wins, B wins

**Ratings After Day 2**

Curry - 1480  
Tatum - 1480  
Durant - 1467  
Embiid - 1467  
Shai - 1467  
LeBron - 1533  
Giannis - 1533  
Jokic - 1533  
Luka - 1520  
Butler - 1520  

---

## 🏀 Day 3

**Teams**

Team A: Curry, LeBron, Luka, Shai, Butler  
Team B: Giannis, Jokic, Tatum, Durant, Embiid  

**Game Results**
A, A, A, B, A

**Final Ratings After Day 3**

Curry - 1505  
LeBron - 1558  
Giannis - 1509  
Jokic - 1509  
Tatum - 1456  
Durant - 1442  
Luka - 1544  
Embiid - 1442  
Shai - 1492  
Butler - 1544  

---

## 🧮 Elo Calculation Method

### Step 1 — Team Rating

Team rating = average of all 5 players’ ratings

### Step 2 — Win Probability Before the Game

E_A = 1 / (1 + 10 ^ ((R_B - R_A) / 400))  
E_B = 1 - E_A

### Step 3 — Update Ratings After Game Result

Δ = K × (Result - ExpectedScore)

- Result = 1 for win, 0 for loss
- K recommended value = 20

All 5 players share the same Δ

---

## 🔍 Win % Estimation by Rating Difference

| Difference | Win Chance |
|-----------|------------|
| 0 Elo | 50% |
| +100 Elo | 64% |
| +200 Elo | 76% |
| +300 Elo | 85% |

---

## ✔ Overall Summary

| Feature | Status |
|--------|--------|
| Team size | 5v5 |
| Stats needed | Only Win/Loss |
| Rating tracked | Player Elo |
| Goal | Balanced games & fair matchmaking |
| Complexity | Simple, scalable, automated |

---
