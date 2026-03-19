# ShieldPay AI – Parametric Income Protection for Gig Workers

---

## Inspiration

India’s gig delivery workforce operates in highly unpredictable environments. A single day of heavy rain, extreme heat, or hazardous pollution can wipe out a significant portion of a worker’s income. These disruptions are frequent, uncontrollable, and currently unprotected.

We were inspired to build a system that removes the traditional insurance friction — no claims, no paperwork — and instead delivers **instant, automated income protection** using real-time data and AI.

---

## Target Persona

Food delivery rider in Chennai working 8–10 hours daily, earning ₹500–₹800 per day, highly affected by heatwaves, heavy rainfall, and pollution spikes that directly reduce working hours and income.

---

## What it does

ShieldPay AI is an AI-powered parametric insurance platform that:

* Calculates **weekly premiums dynamically** based on hyperlocal risk
* Monitors **real-time environmental disruptions**
* Automatically triggers **income compensation payouts**
* Detects and prevents **fraudulent claims (GPS spoofing, fake activity, coordinated attacks)**

The system focuses strictly on **income loss protection**, not health, accident, or asset coverage.

---

## Example Scenario

Ravi, a delivery partner in Chennai, is active from 10 AM–8 PM. At 2 PM, rainfall exceeds 60mm, forcing delivery operations to halt. The system detects the disruption, verifies Ravi’s active status and location, and automatically credits ₹250 to compensate for lost working hours — without any manual claim.

---

## How we built it

### 🧩 Architecture Overview

* **Frontend**: React (Vite) – Mobile-first worker dashboard
* **Backend**: Node.js (Express) – API handling policies, triggers, and payouts
* **Database**: MongoDB – Worker profiles, policies, claims history
* **AI/ML Layer**:

  * Risk scoring model for premium calculation
  * Fraud detection using anomaly + behavioral patterns
* **External APIs (mocked)**:

  * Weather data
  * AQI / pollution data
  * Traffic/disruption signals

---

## ⚙️ Core System Modules

### 1. Risk Engine (AI-Based Premium Model)

Calculates a **weekly premium** based on environmental risk factors:

Inputs:

* Historical rainfall intensity
* Pollution (AQI) patterns
* Zone-based disruption frequency
* Worker’s active hours

Formula:

$$
Premium = BaseRate + (WeatherRisk \times W_1) + (PollutionRisk \times W_2)
$$

This ensures fair, dynamic pricing aligned with real-world risk exposure.

---

### 2. Parametric Trigger System (Zero-Claim Model)

Automatically triggers payouts when predefined thresholds are crossed:

Triggers:

* Rainfall > threshold (e.g., 50mm)
* Temperature > threshold (e.g., 42°C)
* AQI > threshold (e.g., 400)
* Zone-level disruption (curfew / shutdown)

Example:

```js
if (rainfall > 50 || AQI > 400) {
  triggerPayout(workerId);
}
```

---

### 3. Automated Claim & Payout Pipeline

Flow:

Disruption Detected → Worker Match → Validation → Payout Triggered

* No manual claims
* Fully automated process
* Instant payout simulation

---

### 4. Fraud Detection Engine

Hybrid system combining rules + AI:

* Location verification
* Activity tracking
* Behavioral anomaly detection
* Claim pattern analysis

---

## 🚨 Adversarial Defense & Anti-Spoofing Strategy (Market Crash Response)

### Problem

A coordinated fraud ring uses GPS spoofing to simulate presence in disruption zones and triggers mass payouts, draining system funds.

---

### Defense Strategy

#### 1. Multi-Signal Location Verification

We do not rely on GPS alone:

* GPS coordinates
* Network/IP location
* Device motion patterns

Mismatch between signals → flagged.

---

#### 2. Movement & Activity Validation

Real workers:

* Show continuous movement between delivery points

Fraud indicators:

* Static location during active shift
* Teleport-like jumps
* Unrealistic speed patterns

---

#### 3. Behavioral Profiling (AI)

Each worker has a baseline behavior:

* Working hours
* Movement radius
* Delivery frequency

Anomaly score:

$$
Anomaly = deviation(current, historical)
$$

Higher deviation → higher fraud risk.

---

#### 4. Fraud Ring Detection (Cluster Analysis)

We detect coordinated attacks using:

* Multiple claims in same zone/time window
* Shared device/IP fingerprints
* Identical movement patterns

Suspicious clusters are blocked or delayed.

---

#### 5. Risk-Based Payout Control

* Low-risk users → instant payout
* Medium-risk → delayed verification
* High-risk → blocked / flagged

---

#### 6. Reputation Scoring

Each worker has a trust score:

* Consistent behavior → high trust
* Suspicious activity → reduced trust

Lower trust leads to stricter validation.

---

## Challenges we ran into

* Designing fraud detection without penalizing genuine workers
* Simulating real-time disruption events
* Balancing instant payouts with security
* Building fair premium models across regions

---

## Accomplishments that we're proud of

* Built a **zero-claim insurance system**
* Designed a **multi-layer fraud defense architecture**
* Created a **dynamic AI-based pricing model**
* Structured a scalable, real-world system

---

## What we learned

* Parametric insurance removes friction in claims
* Fraud detection is the most critical component
* AI is most valuable in risk prediction and anomaly detection
* Simplicity is key for gig-worker UX

---

## What's next for ShieldPay AI

* Hyperlocal risk prediction (street-level accuracy)
* Integration with real delivery platforms
* Real-time predictive disruption modeling
* Graph-based fraud detection systems

---

## Built With

React, Vite, Node.js, Express, MongoDB, Python (ML), REST APIs

---

## Try It Out

Coming soon

---

## GitHub Repository

https://github.com/Dhanushri26/Guidewire
---

## Demo Video

Coming soon
