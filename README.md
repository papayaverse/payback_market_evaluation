
# Papaya Market Simulator

This simulation models two competing data exchange markets:  
- **IPDM (Information Privacy Decision Market)**, based on Raul Castro Fernandez’s work.  
- **Papaya Market**, an extension incorporating Data Unions and Contextual Integrity (CI).

It simulates **100 users and 2 types of platforms** (Advertisers, Retailers), running over **multiple rounds**, to compare economic and social outcomes between the two systems.

---

## 1. How the Simulated Market Works (Step-by-Step)

### 🔁 For Each Round:
#### Step 1: **User Preferences Initialization**
- Each user is assigned 1–3 "Data Preference Statements":
  - Each statement includes:
    - Anonymization level (A)
    - Platform type (P)
    - A set of data-use purposes (R)

#### Step 2: **Calculate Privacy Sensitivity**
- For each (P, R, A) tuple, the user's **privacy sensitivity** \( v(P, R, A) \) is calculated:
  - Higher if data is anonymized or going to advertisers.
  - Lower if many purposes are approved.

#### Step 3: **Calculate Privacy Cost**
- A function estimates the **privacy cost** \( \rho(P, R, A) \):
  - Higher for de-anonymized data.
  - Higher for invasive purposes (Targeted Ads, Email Marketing).
  - Higher for advertiser platforms.

#### Step 4: **Platforms Bid for Data**
- Each platform values data differently depending on purpose and anonymization.
- They offer a **price** adjusted by:
  - Profitability factor (δR)
  - Privacy sensitivity
  - Anonymization penalty (0.8x)

#### Step 5: **User Decision to Participate**
- In **IPDM**:
  - Users participate **only if** price ≥ privacy cost.
  - If a single (P, R, A) fails this, **user opts out completely from that platform.**
- In **Papaya Market**:
  - Users evaluate each purpose individually.
  - If price ≥ cost **for a given purpose**, they share.

#### Step 6: **Transaction Processing**
- If user and platform agree:
  - Papaya takes a 10% commission.
  - In Papaya Market, earnings are boosted by a **Data Union multiplier** based on how many users share the same (P, R, A) tuple.

#### Step 7: **Earnings, Budget Updates**
- User receives payout.
- Platform’s budget is reduced by total price.

---

## 2. Key Assumptions

### 🧠 From IPDM Model
- **User Utility is Conditional**: Users only participate if they benefit.
- **Privacy Cost and Sensitivity Matter**: Both factor into the pricing and decision logic.
- **Market is a Coordination Problem**: Data value depends on context, purpose, and trust.

### 🍊 Papaya Payback-Specific Extensions (Departures from IPDM)
- **Per-Purpose Participation**: Papaya allows purpose-level sharing, unlike IPDM’s platform-level binary choice.
- **Data Union Effect**: Multiple users sharing similar data increases its market value.
- **Commissioned Broker Model**: Papaya takes a cut as a broker, unlike neutral IPDM coordination.

### 📉 Simplifications & Limitations
- Privacy sensitivity is derived **heuristically**, not empirically.
- All platform prices are calculated based on fixed formulae; **no strategic bidding** or learning.
- User preferences are **random**, not based on real-world personas or clusters.
- **Platform utility and downstream outcomes (e.g., conversion rate)** are not modeled.

---

## 3. Questions

### 🎯 Validation & Theoretical Grounding
- Does this simulation **correctly interpret the core mechanics** of IPDM?
- Is the **platform-level participation vs. per-purpose participation** split theoretically valid?
- Should privacy sensitivity \( v(P, R, A) \) be **fixed per user** or **vary across contexts**?

### 📈 Market Behavior and Pricing
- How should we model **platform bidding** more realistically?
- Should **Data Union effects** be explicitly part of the IPDM + Union model? If yes, is our multiplier assumption valid?
- In IPDM, if user drops out due to one P-R-A mismatch, should they reject **all purposes from that platform** or just the offending tuple?

---

