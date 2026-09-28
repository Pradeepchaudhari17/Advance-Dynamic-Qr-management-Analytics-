# QRFlow — Dynamic QR Code Generator & Analytics Platform

A production-style Dynamic QR Code Generator and real-time Analytics SaaS web application built with **Next.js (App Router)**, **TypeScript**, **Prisma ORM**, **SQLite**, and **NextAuth**.

---

## 🚀 Quick Start

The server is currently running at:
**[http://localhost:3000](http://localhost:3000)**

### Demo Account Credentials
- **Email:** `demo@qrflow.dev`
- **Password:** `demo123456`
- Or simply click **"⚡ Explore with Demo Account"** on the [Login page](http://localhost:3000/login).

---

## 🌟 Key Architecture & Features

### 1. Dynamic Redirect Backend (`/q/:shortCode`)
- When creating a **Dynamic QR Code**, the physical image encodes a permanent redirect URL:  
  `http://localhost:3000/q/:shortCode` (e.g. `/q/SUMMER24`).
- When a user scans the QR code:
  1. The backend inspects the short code in the database.
  2. Parses user-agent, device (Mobile/Desktop/Tablet), browser, and OS.
  3. Records the scan event and increments the scan counter.
  4. Issues an **HTTP 302 redirect** to the configured destination URL.
  5. If the QR code is disabled, shows a branded **"QR Code Unavailable"** page.
- **Zero Reprinting Required:** The owner can change the destination URL anytime from the dashboard modal without altering the QR code image.

### 2. Multi-Format QR Generator (`/dashboard/create`)
Supports 12 content types with dynamic input forms:
- 🌐 Website URL
- 📝 Plain Text
- 📶 Wi-Fi Credentials (SSID, Password, WPA/WEP/Open, Hidden)
- ✉️ Email (Recipient, Subject, Body)
- 📞 Phone Call
- 💬 SMS Message
- 📇 vCard / Contact Card
- 📍 Map Location (Latitude/Longitude coordinates)
- 📅 Calendar Event
- 💳 UPI / Payment Link
- 📱 Social Media Profile
- ⚙️ Custom Data

### 3. QR Customization Studio
- **Pattern styles:** Square, Rounded, Dots, Soft
- **Finder Eye styles:** Square, Rounded, Circle, Leaf
- **Colors:** Custom foreground, background, and linear gradients
- **Logo Integration:** Upload custom image, resize slider, background padding, and automatic error correction (`H`)

### 4. Real-time Analytics Dashboard (`/dashboard`)
- Total QR Codes, Total Scans, Today, This Week, This Month, and Active Rate
- Interactive 30-Day SVG Scan Activity Timeline
- Device distribution (Mobile vs Desktop vs Tablet)
- Operating System & Browser analytics
- Top performing QR codes with direct links
- Live audit log of recent scans

### 5. Management & History
- **My QR Codes (`/dashboard/qrs`):** Search, filtering (All, Dynamic, Static, Active, Disabled), sorting, status toggle, destination URL editor modal, deletion.
- **Scan History (`/dashboard/scans`):** Full audit trail with device/date filters and **CSV Export**.
- **Individual QR Analytics (`/dashboard/qr/:id`):** Per-code breakdown, timeframe filters (7, 30, 90 days), and device metrics.
