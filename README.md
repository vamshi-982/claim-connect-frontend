# Claim Connect — React Frontend

![React](https://img.shields.io/badge/React-18.2.0-blue)
![Vite](https://img.shields.io/badge/Vite-5.x-purple)
![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3-blue)
![Axios](https://img.shields.io/badge/Axios-1.6-green)
![License](https://img.shields.io/badge/License-MIT-yellow)

A **React-based frontend** for the Claim Connect Insurance Claims Management System. Features role-based dashboards for Hospitals, Patients, and Insurance Companies with JWT-secured API communication.

---

## 📌 Table of Contents
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Role-Based Portals](#role-based-portals)
- [Screenshots](#screenshots)

---

## ✨ Features

- 🏥 **Hospital Portal** — Search patients, create and manage claims
- 👤 **Patient Portal** — View, accept, revert or reject claims
- 🏢 **Insurance Portal** — Review and approve/reject accepted claims
- 🔐 **JWT Authentication** — Secure login with token-based auth
- 🛡️ **Protected Routes** — Role-based route guards
- 📡 **Axios Interceptors** — Automatic JWT attachment on all API calls
- 📱 **Responsive Design** — Bootstrap 5 based UI

---

## 🛠️ Tech Stack

| Category | Technology |
|---|---|
| Framework | React 18 |
| Build Tool | Vite 5 |
| Routing | React Router DOM v6 |
| HTTP Client | Axios |
| UI Library | Bootstrap 5, React Bootstrap |
| Forms | React Hook Form |
| Notifications | React Toastify |
| Icons | React Icons |

---

## 📁 Project Structure

```
Frontend/
├── src/
│   ├── components/
│   │   ├── LandingPage/
│   │   │   ├── Navigationbar.jsx
│   │   │   ├── Hero.jsx
│   │   │   ├── Features.jsx
│   │   │   └── Footer.jsx
│   │   ├── SideNav/
│   │   │   ├── SideNavBar.jsx
│   │   │   └── SideNavBar.css
│   │   ├── ClaimHistory.jsx
│   │   ├── MyClaims.jsx
│   │   ├── NewClaimRequest.jsx
│   │   ├── HomePage.jsx
│   │   ├── DetailsPopup.jsx
│   │   └── CustomPrivateRoute.jsx
│   ├── pages/
│   │   ├── Auth/
│   │   │   ├── SignIn.jsx
│   │   │   └── SignUp.jsx
│   │   ├── Hospital/
│   │   │   ├── HospitalHome.jsx
│   │   │   └── hospitalNavData.jsx
│   │   ├── Patient/
│   │   │   ├── PatientHome.jsx
│   │   │   └── patientNavLinks.js
│   │   ├── InsuranceComp/
│   │   │   ├── InsuranceCompHome.jsx
│   │   │   └── insuranceNavLinks.js
│   │   └── LandingPage.jsx
│   ├── utils/
│   │   └── axiosInstances.js
│   ├── App.jsx
│   ├── App.css
│   ├── main.jsx
│   └── index.css
├── index.html
├── package.json
└── vite.config.js
```

---

## ✅ Prerequisites

- Node.js 18+
- npm 9+
- Claim Connect Backend running locally (all 7 services)

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/vamshi-982/claim-connect-frontend.git
cd claim-connect-frontend
```

### 2. Install dependencies

```bash
npm install
```

### 3. Start the development server

```bash
npm run dev
```

### 4. Open in browser

```
http://localhost:5173
```

> ⚠️ Make sure all 7 backend services are running before using the frontend.
> Backend API Gateway must be running at `http://localhost:3434`

---

## 🎭 Role-Based Portals

### 🏥 Hospital Portal (`/hospital/*`)
- View hospital profile and update password
- Search for patients by email
- Create new claim requests
- View claim history with status tracking
- Edit claims that were reverted by patient

### 👤 Patient Portal (`/patient/*`)
- View patient profile and update password
- View all claims raised by hospitals
- **Accept** claims → forwards to insurance company
- **Revert** claims → sends back to hospital for editing
- **Reject** claims → terminates the claim

### 🏢 Insurance Company Portal (`/insurance/*`)
- View insurance company profile
- View all accepted claims from patients
- **Approve** claims → final approval ✅
- **Revert** claims → sends back to hospital
- **Reject** claims → terminates the claim ❌

---

## 🔐 Authentication Flow

```
1. User selects role (Hospital / Patient / Insurance)
2. Enters credentials → POST /api/{role}/authenticate
3. Backend returns JWT token
4. Token stored in localStorage
5. Axios interceptor attaches token to all future requests
6. CustomPrivateRoute checks role before rendering pages
7. On 401 response → clears token → redirects to login
```

---

## 🌐 API Configuration

All API calls go through the **API Gateway** at:

```javascript
// src/utils/axiosInstances.js
baseURL: 'http://localhost:3434/api/hospital/'   // Hospital
baseURL: 'http://localhost:3434/api/patient/'    // Patient
baseURL: 'http://localhost:3434/api/insuranceComp/' // Insurance
```

---

## 👨‍💻 Author

**Siddapuram Vamshi**
- GitHub: [@vamshi-982](https://github.com/vamshi-982)
- LinkedIn: [siddapuramvamshi](https://linkedin.com/in/siddapuramvamshi)

---

## 📄 License

This project is licensed under the MIT License.
