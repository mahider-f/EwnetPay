# EwnetPay 

### AI-Powered Digital Payment Verification & Fraud Intelligence

EwnetPay is an AI-powered payment verification platform designed to help merchants quickly determine whether a digital payment is genuine, valid, and safe to accept.

The project focuses on a growing problem in Ethiopia: as digital payments become more widely used, merchants increasingly depend on screenshots, transaction receipts, and payment messages shown by customers as proof of payment.

Manually verifying every transaction can be slow and inconvenient, especially in busy environments such as shops, restaurants, transportation services, pharmacies, cafés, delivery services, and other businesses.

It also creates opportunities for fraud.

Common examples include:

- Reusing an old but genuine payment receipt
- Showing a receipt belonging to another transaction
- Editing the amount displayed on a screenshot
- Sending money to the wrong recipient
- Showing an old transaction as a new payment
- Repeatedly submitting suspicious payment proofs

EwnetPay aims to make this verification process faster, simpler, and more intelligent.

---

## The Problem

A typical digital-payment interaction often looks like this:

1. A customer makes a payment.
2. The customer shows a screenshot or transaction message.
3. The merchant checks the amount.
4. The merchant checks the recipient.
5. The merchant searches SMS notifications or banking records.
6. The merchant decides whether the payment is genuine.

During busy periods, this process creates unnecessary friction.

Merchants may accept screenshots without properly checking them because verifying every payment manually takes too much time.

EwnetPay reduces this burden by automating as much of the verification process as possible.

---

## Our Solution

EwnetPay combines:

**Authoritative payment verification**

with

**AI-powered fraud intelligence**

to provide merchants with a simple payment decision.

Instead of manually inspecting every receipt, the merchant can receive a result such as:

```text
✅ PAYMENT VERIFIED

Amount: 850 ETB

Fraud Risk: LOW
```

or:

```text
 PAYMENT NEEDS REVIEW

Possible reused receipt

Fraud Risk: HIGH
```

The goal is not to replace banks or payment providers.

EwnetPay acts as an intelligent verification layer between:

> **“The customer says they paid.”**

and:

> **“The merchant knows the payment can be trusted.”**

---

## How It Works

```text
Payment Proof
     │
     ▼
Receipt / Screenshot / Transaction Reference
     │
     ▼
Transaction Extraction
     │
     ▼
Authoritative Payment Verification
     │
     ▼
EwnetAI Fraud Engine
     │
     ├── Behaviour Analysis
     ├── Receipt Similarity Detection
     ├── Anomaly Detection
     └── Fraud Risk Scoring
     │
     ▼
Payment Decision
     │
 ┌───┼──────────────┐
 ▼   ▼              ▼               
Safe Review        Suspicious
```

---

# EwnetAI

EwnetAI is the machine-learning component of EwnetPay.

The goal is to move beyond simple `if/else` payment checks.

Traditional verification can answer questions such as:

- Does this transaction exist?
- Was the payment successful?
- Is the amount correct?
- Was the correct recipient paid?

EwnetAI asks another question:

> **Does anything about this payment or verification attempt look suspicious?**

---

## 1. Behavioural Fraud Detection

EwnetAI analyzes patterns surrounding payment-verification attempts.

Potential features include:

- Number of recent verification attempts
- Previous failed verification attempts
- Repeated receipt submissions
- Transaction age
- Time between verification attempts
- Payment amount patterns
- Payment frequency
- Repeated suspicious activity
- Device/session behaviour
- Merchant payment patterns

An anomaly-detection or supervised machine-learning model can use these features to produce a fraud-risk score.

Example:

```text
Fraud Risk Score

12 / 100
LOW
```

or:

```text
Fraud Risk Score

91 / 100
HIGH
```

---

## 2. Receipt Similarity Detection

Fraudsters may slightly modify an existing screenshot by:

- Changing the displayed amount
- Cropping the receipt
- Resizing the image
- Covering parts of the transaction
- Reusing a previously submitted receipt

EwnetAI can generate visual embeddings for receipt images and compare them with previous submissions.

Example:

```text
Previous receipt similarity:

97.4%

 Possible reused or modified payment proof
```

This allows the system to detect visually related receipts even when the files are not exactly identical.

---

## 3. Anomaly Detection

Fraud patterns are constantly changing.

EwnetPay therefore does not rely entirely on known fraud examples.

An anomaly-detection model can learn normal payment-verification behaviour and flag transactions that significantly differ from expected patterns.

This allows EwnetAI to identify suspicious behaviour that may not have appeared in the original training dataset.

---

## Important Design Principle

AI does **not** determine whether money actually moved between bank accounts.

Authoritative payment-provider verification remains the source of truth for the transaction itself.

AI is used to identify:

- suspicious behaviour,
- unusual patterns,
- receipt reuse,
- visual manipulation,
- and fraud risk.

This separation makes the system safer and easier to explain.

---

# Frictionless Verification

One of EwnetPay's main goals is reducing the number of actions merchants must perform.

The target experience is:

```text
Customer pays
      ↓
Payment proof captured
      ↓
Transaction verified
      ↓
AI risk analysis
      ↓
Merchant receives result
```

Rather than forcing users through several menus and forms, the verification interface is designed to require minimal interaction.

For example:

```text
┌─────────────────────────────┐
│         EWNETPAY            │
│                             │
│       Scan Receipt          │
│                             │
│                           │
│                             │
│  or upload payment proof    │
│                             │
└─────────────────────────────┘
```

The system handles the remaining verification steps automatically.

---

# Voice Interaction

EwnetPay can also provide voice-based confirmation.

Examples:

> “Payment verified. Eight hundred birr received.”

> “Warning. This transaction appears to have been used before.”

> “Payment amount does not match.”

> “This payment requires additional review.”

Voice confirmation is especially useful in busy merchant environments where constantly looking at a phone or screen is inconvenient.

---

# Example Use Case

A customer purchases goods worth **1,200 ETB**.

The customer provides their payment receipt.

EwnetPay:

1. Extracts the transaction information.
2. Verifies the transaction through the supported payment-verification provider.
3. Confirms the recipient and amount.
4. Checks whether the transaction has previously been submitted.
5. Runs the payment through EwnetAI.
6. Generates a fraud-risk score.
7. Displays the final verification result.

Result:

```text
 VERIFIED

Amount
1,200 ETB

Transaction
Successful

Fraud Risk
6 / 100 — LOW
```

If the same receipt is later submitted again:

```text
 PAYMENT REJECTED

Possible reused transaction

Previous verification detected
```

---

# Target Users

EwnetPay can potentially support:

- Small shops
- Cafés
- Restaurants
- Pharmacies
- Hotels
- Delivery businesses
- Transportation services
- Parking services
- Online sellers
- Service providers
- Larger merchants and retailers

The long-term goal is to make the system useful for both small merchants and businesses with existing digital systems.

---

# Proposed Technology Stack

### Frontend

- React / Next.js
- Mobile-first responsive interface
- Progressive Web App (PWA)

### Backend

- Python
- FastAPI

### Machine Learning

- Scikit-learn
- XGBoost / LightGBM
- Isolation Forest
- Image embeddings / computer vision models

### Data

- PostgreSQL

### Payment Verification

- Links.et or other supported Ethiopian payment-verification infrastructure

### Voice

- Voxide

### Deployment

- EthioDeploy / cloud deployment

---

# MVP

The initial hackathon MVP will focus on:

- Receipt/screenshot submission
- Payment-data extraction
- Transaction verification
- Duplicate transaction detection
- AI fraud-risk scoring
- Behavioural anomaly detection
- Receipt-image similarity
- Merchant verification dashboard
- Voice payment confirmation

---

# Future Development

Future versions of EwnetPay could include:

- Real-time merchant payment feeds
- POS integration
- API integration for online stores
- Feature-phone support
- SMS verification
- USSD support
- Merchant fraud analytics
- Cross-merchant fraud intelligence
- Improved Amharic support
- Advanced deep-learning fraud models
- Continuous model learning from verified fraud cases

---

# Project Vision

Digital payments should reduce friction, not create a new verification problem.

EwnetPay's vision is to make digital-payment confirmation:

**Fast. Simple. Intelligent. Trustworthy.**

### EwnetPay

**Don't trust the screenshot. Verify the payment.**
