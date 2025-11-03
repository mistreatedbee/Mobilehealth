```markdown
# 🏥 MobileHealth  
Modern Healthcare Appointment & Telemedicine System

MobileHealth is a **cross-platform healthcare system** that allows patients to book appointments, doctors to manage schedules, and admins to manage the entire platform.  
This project includes **full video consultation support** and runs on **Android** using **Capacitor + Expo**.

---

## 📦 Project Overview

| Component | Technology | Role |
|---------|------------|------|
| **Patient App (Mobile)** | React Native (Expo) + Capacitor | Appointment booking & video calls |
| **Doctor Dashboard** | React + TypeScript | Scheduling, patient profiles & telehealth |
| **Admin Dashboard** | React + TypeScript | System analytics, doctor verification & management |
| **Backend** | Node.js + Express + MongoDB | API, Auth, Notifications, Video Link Generation |
| **Video Conferencing** | **Jitsi Secure Rooms** | Online consultations inside the app |
| **Notifications** | Expo Push Notifications | Appointment updates & reminders |

---

## 🧱 Features

### Patient App (Mobile)
- Login / Register
- Complete medical profile + emergency details
- Search & book doctors by specialty
- Choose **Online** or **In-Person** appointment
- View upcoming & past bookings
- **Join video consultation inside the app** (Capacitor support ✅)
- Push notifications

### Doctor Dashboard (Web)
- Approve / decline appointments
- View detailed patient profiles & medical history
- Generate & start **video consultation rooms**
- Write & issue prescriptions
- Notifications for new appointments

### Admin Dashboard (Web)
- Manage patients & doctors
- Approve / verify new doctors
- View appointment analytics (online vs in-person)
- System status dashboard

---

## 🗂 Project Structure

```

MobileHealth/
├── backend/          # Node.js Express API
├── web/              # Admin + Doctor dashboards
└── mobile/           # Patient Mobile App (Expo + Capacitor)

````

---

## ⚙️ Backend Setup

```bash
cd backend
npm install
````

Create `.env`:

```
MONGO_URI=mongodb+srv://mobilehealth_user:mobilehealth123@myfirstcluster.oi6i2ke.mongodb.net/mobilehealth?retryWrites=true&w=majority&appName=myFirstCluster
PORT=5000
```

Start API:

```bash
npm start
```

---

## 🌐 Web Dashboard Setup (Admin + Doctor)

```bash
cd web
npm install
npm run dev
```

Runs at:

```
http://localhost:5173
```

---

## 📱 Mobile App Setup (Expo + Capacitor)

```bash
cd mobile
npm install
```

### Start App (Expo Dev mode)

```bash
npm start
```

---

## 🤖 Build for Android (Capacitor)

### 1) Add Capacitor to project (already done, but here for reference)

```bash
npx cap add android
```

### 2) Sync changes

```bash
npx cap sync
```

### 3) Open in Android Studio

```bash
npx cap open android
```

### 4) Run the app on an emulator or USB device

Click ▶ Run inside Android Studio.

---

## 🎥 Video Consultations (Jitsi + Capacitor)

### Backend (already implemented)

```js
const roomName = `mobilehealth-${appointmentId}`;
const videoCallLink = `https://meet.jit.si/${roomName}`;
```

### Mobile App Setup

Install In-App Browser (works inside Capacitor):

```bash
expo install react-native-inappbrowser-reborn
```

Use it to open video calls:

```js
import * as InAppBrowser from "react-native-inappbrowser-reborn";

export async function openVideoCall(url: string) {
  if (await InAppBrowser.isAvailable()) {
    await InAppBrowser.open(url, {
      toolbarColor: "#4f46e5",
      animated: true,
      showTitle: true,
    });
  } else {
    Linking.openURL(url);
  }
}
```

Usage Example:

```js
<Button onPress={() => openVideoCall(appointment.videoCallLink)}>Join Call</Button>
```

---

## 🧰 Common Fixes

| Issue                          | Solution                                           |
| ------------------------------ | -------------------------------------------------- |
| Blank white screen on build    | Run `expo prebuild` then `npx cap sync`            |
| Capacitor not updating changes | Run `npx cap copy android && npx cap open android` |
| Emulator not detecting device  | Enable **USB Debugging** + Install Platform Tools  |

---

## 🔮 Future Extensions

* Live chat during consultations
* Payments & Medical Aid integration
* Pharmacy prescription forwarding
* AI medical symptom assistance

---
