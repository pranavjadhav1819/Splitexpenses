<div align="center">

# 💸 TALLY

### Smart Expense Splitter

**Split expenses. Track balances. Settle up. Stay organized.**

A modern, responsive expense-splitting web app designed for groups, trips, roommates, friends, and everyday shared expenses.

<br>

![TALLY](https://img.shields.io/badge/TALLY-Smart%20Expense%20Splitter-7c5cff?style=for-the-badge)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge\&logo=html5\&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge\&logo=css3\&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge\&logo=javascript\&logoColor=black)
![PWA](https://img.shields.io/badge/PWA-Ready-5A0FC8?style=for-the-badge)

<br>

[✨ Live Demo](https://splitexpenses-2w4b.onrender.com) •
[🚀 Features](#-features) •
[🛠️ Installation](#-installation) •
[📖 Usage](#-usage) •
[📁 Project Structure](#-project-structure)

</div>

---

## 📌 About

**TALLY** is a modern client-side expense management and splitting application.

It allows users to create groups, add members, record shared expenses, automatically calculate balances, and generate optimized settlement transactions.

The application is designed around a simple idea:

> **You enter who paid and who shared the expense — TALLY calculates the rest.**

No backend or account is required for the core experience. Group data is stored locally on the user's device using browser `localStorage`.

---

## ✨ Features

### 👥 Group Management

* Create multiple expense groups
* Rename groups
* Delete groups
* Switch between groups
* Independent people and expenses for every group
* Automatic local persistence

### 💰 Expense Tracking

Record expenses with:

* Description
* Amount
* Payer
* Category
* Date
* People sharing the expense

Supported categories:

* 🍔 Food
* ✈️ Travel
* 🏨 Hotel
* 🛍️ Shopping
* ⛽ Fuel
* 📦 Other

---

### ⚖️ Smart Expense Splitting

TALLY supports two splitting methods:

#### Even Split

Automatically divides the expense equally between selected members.

Example:

```text
Dinner = ₹1200

Pranav
Swapnil
Rahul
Amit

₹1200 ÷ 4 = ₹300 each
```

#### Custom Split

Specify exactly how much each selected person owes.

Example:

```text
Total = ₹1500

Pranav  → ₹500
Swapnil → ₹400
Rahul   → ₹350
Amit    → ₹250

Total   → ₹1500 ✓
```

TALLY validates custom allocations to ensure they match the total expense.

---

### 📊 Live Dashboard

The dashboard automatically displays:

```text
┌─────────────────────┐
│ Total Spending      │
│ ₹12,450.00          │
└─────────────────────┘

┌─────────────────────┐
│ People              │
│ 5                   │
└─────────────────────┘

┌─────────────────────┐
│ Expenses            │
│ 14                  │
└─────────────────────┘
```

Counters animate whenever the underlying data changes.

---

### 💳 UPI Settlement

Members can optionally save their UPI ID.

When a settlement is generated, TALLY can display:

**Pay via UPI**

The application generates a UPI payment URI containing:

* UPI ID
* Receiver name
* Amount
* INR currency
* Settlement description

This allows compatible mobile UPI applications to handle the payment.

---

### 🤝 Smart Settlement Algorithm

TALLY calculates who owes whom and simplifies the required transactions.

Instead of showing every individual expense relationship, it calculates a reduced set of transfers.

Example:

```text
Rahul owes ₹500
Amit gets ₹500

        ↓

Rahul ──────────₹500──────────> Amit
```

The settlement algorithm separates members into:

* Creditors
* Debtors

and matches their balances to produce settlement transactions.

---

### 📈 Spending by Category

Expenses are automatically grouped into categories.

Example:

```text
Food       ████████████████  ₹4,500
Travel     ██████████       ₹2,800
Hotel      ███████          ₹1,900
Shopping   ████             ₹900
Fuel       ██               ₹500
```

The visualization updates automatically whenever expenses change.

---

### 🔎 Expense Search

Search through the expense ledger by:

* Description
* Payer
* Category
* Amount

Example:

```text
Search: dinner
```

TALLY instantly filters matching transactions.

---

### ✏️ Edit & Delete Expenses

Existing transactions can be:

* Edited
* Re-split
* Re-categorized
* Re-dated
* Removed

The edit interface automatically restores the existing split information.

---

### 📤 Export Data

TALLY supports two export formats:

#### CSV

Export the expense ledger as:

```text
Date
Description
Category
Paid by
Amount
Split between
```

#### Excel

Generate an `.xlsx` workbook containing:

```text
Expenses
Balances
Settlements
```

Excel export uses the SheetJS/XLSX library loaded dynamically when required.

---

### 🌙 Dark / ☀️ Light Mode

TALLY includes a complete theme system.

**Dark Mode**

* Deep background
* Purple gradients
* Glassmorphism
* Aurora effects
* Particle mesh

**Light Mode**

* Light surfaces
* Soft shadows
* Adjusted contrast
* Light aurora effects

The selected theme is saved locally.

---

### 🎨 Modern UI

The interface uses a combination of:

* Glassmorphism
* Aurora gradients
* Animated particles
* Noise texture
* Gradient typography
* Floating cards
* Micro-interactions
* Ripple effects
* 3D card tilt
* Scroll reveal animations
* Animated counters
* Toast notifications

---

### 🎉 Celebration Animation

When everyone is completely settled, TALLY displays:

```text
✓

Everyone is settled up
```

with a celebration/confetti animation.

---

### 📱 Responsive Design

Designed for:

* 💻 Desktop
* 💻 Laptop
* 📱 Mobile
* 📲 Tablet

On mobile devices, TALLY provides a floating action button for quickly jumping to the expense form.

---

### 📲 Progressive Web App

TALLY includes PWA support through:

```text
manifest.json
service-worker.js
icon.svg
```

The application can be configured for installation as a web app on supported browsers.

---

## 🧠 How TALLY Calculates Balances

For every expense:

```text
Payer receives credit for the full amount.
Each participant receives a debit equal to their share.
```

For example:

```text
Dinner = ₹1000

Pranav paid ₹1000

Pranav share = ₹250
Rahul share  = ₹250
Amit share   = ₹250
Swapnil share = ₹250
```

Balances become:

```text
Pranav  +₹750
Rahul   -₹250
Amit    -₹250
Swapnil -₹250
```

TALLY then converts these balances into settlement transactions.

---

## 🏗️ Architecture

TALLY follows a lightweight client-side architecture:

```text
                 ┌──────────────────────┐
                 │       TALLY UI       │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │    JavaScript App    │
                 └──────────┬───────────┘
                            │
          ┌─────────────────┼─────────────────┐
          ▼                 ▼                 ▼
     Expense Logic     Balance Engine    Group Manager
          │                 │                 │
          └─────────────────┼─────────────────┘
                            ▼
                 ┌──────────────────────┐
                 │    localStorage      │
                 └──────────────────────┘
```

---

## 🛠️ Tech Stack

| Technology         | Purpose                            |
| ------------------ | ---------------------------------- |
| HTML5              | Application structure              |
| CSS3               | UI, animations & responsive design |
| Vanilla JavaScript | Application logic                  |
| LocalStorage API   | Local data persistence             |
| Canvas API         | Particles & confetti               |
| Web APIs           | PWA & browser functionality        |
| SheetJS / XLSX     | Excel export                       |
| Google Fonts       | DM Sans & Space Mono               |

### Fonts

* **DM Sans** — primary interface font
* **Space Mono** — numerical/data font

---

## 🎨 Design System

### Primary Palette

```text
Primary Purple     #7c5cff
Secondary Purple   #9b85ff
Cyan               #36d1dc
Green              #38d996
Red                #ff5f6d
Yellow             #ffc857
```

### Background

```text
Dark Background    #080a0f
Secondary          #0e1118
```

### Category Colors

```text
Food       → Pink
Travel     → Cyan
Hotel      → Yellow
Shopping   → Purple
Fuel       → Orange
Other      → Gray
```

---

## 📸 Screenshots

Add screenshots of the application here:

```text
screenshots/
├── dashboard.png
├── expense-form.png
├── settlements.png
├── analytics.png
└── mobile.png
```

Example:

<div align="center">

### Dashboard

<img src="screenshots/dashboard.png" width="850">

### Expense Management

<img src="screenshots/expense-form.png" width="850">

### Settlement

<img src="screenshots/settlements.png" width="850">

</div>

> Replace the screenshot paths with your actual repository images.

---

## 🚀 Live Demo

**TALLY — Smart Expense Splitter**

deployed application URL :

```text
https://splitexpenses-2w4b.onrender.com
```

---

## ⚙️ Installation

### 1. Clone the repository

```bash
git clone https://github.com/pranavjadhav1819/tally.git
```

### 2. Open the project

```bash
cd tally
```

### 3. Run locally

Because TALLY is a client-side web application, you can run it with any static server.

Using VS Code Live Server:

```text
Right click index.html
        ↓
Open with Live Server
```

Or using Python:

```bash
python -m http.server 5500
```

Then open:

```text
http://localhost:5500
```

---

## 📁 Project Structure

A recommended repository structure:

```text
tally/
│
├── index.html
├── manifest.json
├── service-worker.js
├── icon.svg
│
├── screenshots/
│   ├── dashboard.png
│   ├── expense-form.png
│   ├── settlements.png
│   └── mobile.png
│
├── README.md
└── LICENSE
```

---

## 💾 Data Storage

TALLY currently uses browser `localStorage`.

The primary storage key is:

```javascript
tally-groups-v2
```

Theme preference is stored using:

```javascript
tally-mode
```

This means:

* No account is required
* No database is required
* No backend is required
* Data stays on the current browser/device
* Clearing browser storage can remove application data

The footer intentionally communicates this behavior:

> **Your expenses stay on this device**

---

## 🔐 Privacy

TALLY is designed around local-first expense management.

The core application does not require users to create an account or send their expense information to a server.

Expense and group information is stored locally through the browser's `localStorage`.

### Important

Because data is stored locally:

```text
Browser data cleared
        ↓
Local TALLY data may be lost
```

Users should export important expense records when necessary.

---

## 📊 Excel Export

The Excel exporter dynamically loads:

```text
SheetJS / XLSX
```

Only when the user requests an Excel export.

The generated workbook contains three sheets:

### Expenses

```text
Date
Description
Category
Paid by
Amount
Split between
```

### Balances

```text
Person
Status
Amount
```

### Settlements

```text
From
To
Amount
```

---

## 📱 PWA Support

The project includes:

```text
manifest.json
service-worker.js
icon.svg
```

The service worker is registered only when the application is served through HTTP/HTTPS:

```javascript
if ("serviceWorker" in navigator && location.protocol.startsWith("http")) {
    ...
}
```

For production deployment, make sure the service worker and manifest are served from the correct paths.

---

## 🧪 Example Workflow

### Create a group

```text
Trip to Goa
```

### Add members

```text
Pranav
Swapnil
Rahul
Amit
```

### Add an expense

```text
Description: Dinner
Amount: ₹2400
Paid by: Pranav
Category: Food
Split: Even
```

TALLY calculates:

```text
₹2400 ÷ 4

₹600 each
```

Pranav's net balance:

```text
₹2400 - ₹600 = +₹1800
```

The other three members each owe:

```text
₹600
```

Settlement:

```text
Swapnil ──₹600──> Pranav
Rahul   ──₹600──> Pranav
Amit    ──₹600──> Pranav
```

---

## 🔄 Data Flow

```text
User Action
     │
     ▼
JavaScript Event Handler
     │
     ▼
Application State
     │
     ├── People
     ├── Expenses
     ├── Groups
     └── Settings
     │
     ▼
Balance Calculation
     │
     ▼
Settlement Algorithm
     │
     ▼
UI Rendering
     │
     ▼
localStorage
```

---

## 🧩 Core Functions

Some of the main application functions include:

```javascript
addPerson()
removePerson()

addExpense()
removeExpense()
startEditExpense()
cancelEdit()

computeBalances()
simplifySettlements()

renderExpenses()
renderBalances()
renderSettlements()
renderCategoryChart()

exportCSV()
exportExcel()

addGroup()
renameGroup()
deleteGroup()
switchGroup()

setPersonUpi()
```

---

## 🎯 Future Improvements

Potential future versions could include:

* ☁️ Cloud synchronization
* 🔐 User authentication
* 👥 Shared real-time groups
* 📧 Expense reminders
* 📲 Native mobile application
* 📊 Advanced analytics
* 📅 Monthly spending reports
* 🔔 Settlement notifications
* 📎 Receipt image attachments
* 🧾 OCR receipt scanning
* 💱 Multiple currencies
* 🌐 Multi-language support
* 🔗 Shareable expense groups
* 📈 Spending trends
* 🤖 AI expense categorization
* 🏦 Direct payment integrations

---

## 🐛 Known Considerations

### Local Storage

Data belongs to the current browser/device.

### UPI

UPI payment links depend on the user's device and installed UPI applications.

### Excel Export

Excel export requires an internet connection the first time the XLSX library is dynamically loaded, unless the library is bundled locally.

### PWA

Service-worker functionality requires the application to be served from a supported HTTP/HTTPS environment rather than directly opening the HTML file using `file://`.

---

## 🤝 Contributing

Contributions are welcome.

### Fork the repository

```bash
git fork https://github.com/pranavjadhav1819/tally
```

### Create a branch

```bash
git checkout -b feature/new-feature
```

### Commit your changes

```bash
git commit -m "feat: add new feature"
```

### Push

```bash
git push origin feature/new-feature
```

Then open a Pull Request.

---

## 📜 License

This project is available for personal and educational use.

If you add a specific open-source license to the repository, update this section accordingly.

---

## 👨‍💻 Author

<div align="center">

### Pranav Jadhav

**Computer Engineering Student • Web Developer • Programmer**

<br>

[![GitHub](https://img.shields.io/badge/GitHub-pranavjadhav1819-181717?style=for-the-badge\&logo=github)](https://github.com/pranavjadhav1819)

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Pranav%20Jadhav-0A66C2?style=for-the-badge\&logo=linkedin)](https://www.linkedin.com/in/pranav-jadhav-31006b373/)

[![Website](https://img.shields.io/badge/Portfolio-pranav18.onrender.com-7c5cff?style=for-the-badge\&logo=google-chrome\&logoColor=white)](https://pranav18.onrender.com)

[![Email](https://img.shields.io/badge/Email-jadhav.pranav.1819%40gmail.com-EA4335?style=for-the-badge\&logo=gmail\&logoColor=white)](mailto:jadhav.pranav.1819@gmail.com)

</div>

---

<div align="center">

### 💸 TALLY

**Track less. Settle faster.**

Made with ❤️ by **Pranav Jadhav**

⭐ If you find TALLY useful, consider giving the repository a star!

</div>
