# 🌊 The Wave Cafe — Full Stack Food Ordering Website

A modern, feature-rich food ordering website inspired by Swiggy & Zomato, built with Node.js, Express, MongoDB and Vanilla JS.

---

## 📁 Project Structure

```
wave-cafe/
├── index.html              ← Landing page
├── menu.html               ← Food menu with filters & search
├── cart.html               ← Cart page
├── checkout.html           ← Checkout & order placement
├── success.html            ← Order success with confetti
├── admin/
│   ├── admin-login.html    ← Admin login
│   └── admin-dashboard.html ← Full admin panel
├── css/
│   └── style.css           ← Global stylesheet (dark mode included)
├── js/
│   ├── main.js             ← Shared utilities, cart, toasts, theme
│   ├── auth.js             ← OTP phone login system
│   ├── menu.js             ← Menu page logic
│   ├── cart.js             ← Cart page logic
│   ├── checkout.js         ← Checkout & order placement
│   └── admin.js            ← Admin panel logic
├── server/
│   ├── server.js           ← Express app entry point
│   ├── routes/
│   │   ├── authRoutes.js   ← OTP login/logout
│   │   ├── menuRoutes.js   ← Menu CRUD + seed data
│   │   ├── orderRoutes.js  ← Place & view orders
│   │   └── adminRoutes.js  ← Admin management APIs
│   └── models/
│       ├── User.js         ← User model (phone + OTP)
│       ├── Order.js        ← Order model
│       ├── MenuItem.js     ← Menu item model
│       └── Admin.js        ← Admin model (bcrypt password)
├── .env                    ← Environment variables
├── package.json
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites
- Node.js v16+
- MongoDB (local or MongoDB Atlas)

### Installation

```bash
# 1. Install dependencies
npm install

# 2. Configure environment (optional — defaults work for local dev)
# Edit .env with your MongoDB URI and secrets

# 3. Start the server
node server/server.js

# Or with auto-reload (install nodemon):
npm run dev
```

### Open in browser
```
http://localhost:3000
```

---

## 🔑 Default Credentials

### Admin Panel
- **URL:** `http://localhost:3000/admin/admin-login.html`
- **Email:** `admin@wavecafe.com`
- **Password:** `admin123`

### User Login (OTP)
- Enter any 10-digit phone number
- The demo OTP is shown directly in the UI response (for development)
- In production: integrate Twilio / MSG91 for real SMS

---

## ✨ Features

### Customer Side
- 🏠 **Landing page** — Hero, categories, featured items, stats
- 🍔 **Menu page** — 16+ items, category filters, live search, add-to-cart
- 🛒 **Cart sidebar** — Real-time cart popup with quantity controls
- 🛒 **Cart page** — Full cart management, promo codes, order summary
- 💳 **Checkout** — Delivery form, order summary, place order
- 🎉 **Success page** — Confetti animation, order tracking steps, live ETA
- 📱 **OTP Login** — Phone number + 6-digit OTP verification
- 🌙 **Dark mode** — Full dark theme toggle
- 📱 **Mobile responsive** — Works on all screen sizes

### Admin Panel
- 📊 **Dashboard** — Revenue, orders, users, menu stats
- 📦 **Orders** — View all orders, update status (Pending → Preparing → Delivered)
- 🍽️ **Menu Management** — Add, edit, delete food items
- 👥 **Users** — View registered customers

---

## 🌐 API Endpoints

### Auth
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/send-otp` | Send OTP to phone |
| POST | `/api/auth/verify-otp` | Verify OTP, get JWT token |
| POST | `/api/auth/logout` | Logout user |
| GET  | `/api/auth/me` | Get current user |

### Menu
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/menu` | Get all menu items (supports `?category=Burgers&search=wave`) |
| GET | `/api/menu/featured` | Get featured items |

### Orders
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/orders/create` | Place a new order (auth required) |
| GET  | `/api/orders/history` | Get order history (auth required) |

### Admin
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST   | `/api/admin/login` | Admin login |
| GET    | `/api/admin/menu` | Get all menu items |
| POST   | `/api/admin/add-food` | Add food item |
| PUT    | `/api/admin/edit-food/:id` | Edit food item |
| DELETE | `/api/admin/delete-food/:id` | Delete food item |
| GET    | `/api/admin/orders` | Get all orders |
| PUT    | `/api/admin/update-order-status/:orderId` | Update order status |
| GET    | `/api/admin/stats` | Get dashboard stats |
| GET    | `/api/admin/users` | Get all users |

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | HTML5, CSS3, Vanilla JavaScript |
| Backend  | Node.js, Express.js |
| Database | MongoDB + Mongoose |
| Auth     | JWT + Phone OTP |
| Admin auth | bcryptjs |

---

## 📱 Production SMS Integration

Replace the demo OTP in `authRoutes.js` with a real SMS provider:

```js
// Twilio example
const twilio = require('twilio')(TWILIO_SID, TWILIO_TOKEN);
await twilio.messages.create({
  body: `Your Wave Cafe OTP is: ${otp}`,
  from: process.env.TWILIO_PHONE,
  to: `+91${phone}`
});
```

---

## 🎨 Design Features
- Syne display font + DM Sans body
- CSS custom properties (easy theme customization)
- Glassmorphism navbar with blur
- Swiggy-style quantity selector
- Skeleton loading states
- Intersection Observer animations
- Floating hero with CSS animation
- Confetti on order success

---

Made with ❤️ — The Wave Cafe Team
