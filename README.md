# Waterwise: Smart Water Tracking for South Africa

**Waterwise** is a cross-platform mobile application designed to empower South African consumers and utility providers by automating the traditional, manual process of water sub-meter reading. Using advanced Computer Vision and OCR technology, Waterwise transforms smartphone photos into accurate water consumption data—eliminating manual meter readings, reducing errors, and enabling real-time leak detection.

[![Status](https://img.shields.io/badge/Status-MVP-blue)]()
[![License](https://img.shields.io/badge/License-MIT-green)]()

---

## 📋 Table of Contents

- [The South African Context](#-the-south-african-context--challenges)
- [How It Works](#-how-waterwise-works-the-workflow)
- [Key Features](#-key-features)
- [Tech Stack](#-tech-stack)
- [Project Architecture](#️-project-architecture)
- [Installation & Setup](#-installation--setup)
- [Core System Rules](#-core-system-rule)
- [Future Enhancements](#-future-enhancements)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🇿🇦 The South African Context & Challenges

Traditional water sub-metering in South Africa heavily relies on manual municipal or landlord tracking, which introduces several critical pain points:

- **Inefficient Data Collection:** Personnel must manually visit properties to log meter readings into spreadsheets, which is both costly and slow.
- **Environmental Wear & Tear:** Meters are frequently dirty, weather-worn, or placed in dark, inaccessible spots, making them incredibly difficult to read accurately.
- **Human Error & Data Disputes:** Disconnects between paper logs and central accounting software often lead to billing anomalies, shock "estimated" bills, and prolonged consumer disputes.
- **Lack of Transparency:** Consumers and tenants rarely have access to real-time consumption trends, making it difficult to detect leaks or actively conserve water in drought-prone areas.

**The Solution:** Waterwise eliminates these challenges by turning any smartphone into an intelligent water meter reader.

---

## 🚀 How Waterwise Works (The Workflow)

Waterwise simplifies water tracking into a few seamless steps:

1. **Snap a Photo:** The consumer or representative opens the app and takes a photo of the water meter.

2. **Quality Check:** Embedded Computer Vision techniques automatically assess image quality (checking for blur, low resolution, or poor lighting). If it falls below a specific threshold, the user is prompted to retake the photo.

3. **Automated Extraction:** Approved images undergo a two-fold Deep Learning process to extract data securely:
   - **Text Detection (Area of Interest):** The app isolates the specific numeric display box using highly efficient scene text detectors like **EAST** or **Single Shot Detectors (YOLO/SSD)**.
   - **Digit Extraction (CRNN & OCR):** The isolated digits are processed using a Convolutional Recurrent Neural Network (CRNN) paired with OCR tools like Tesseract to accurately transcribe the exact water reading.

4. **Instant Billing & Analytics:** The numeric data is sent to the central database, calculating the accurate amount owed based on local tariffs, updating accounting systems instantly, and generating consumption insights for the user.

---

## ✨ Key Features

### 📊 1. Smart Consumption Tracking
- Monthly water usage calculations
- Cost estimation using mock tariffs
- Historical comparison of usage trends
- Automatic detection of consumption spikes

### 🧠 2. AI Water Insights Engine
- Personalized water usage recommendations
- Efficiency scoring (Excellent → High Usage)
- Leak detection alerts
- Environmental impact insights

### 📈 3. Analytics Dashboard
- Monthly usage bar charts
- Cost breakdown visualization
- Trend analysis
- Savings tracking

### 🧾 4. History Tracking
- Full reading history
- OCR + final corrected readings
- Image previews of meter submissions
- Search and filtering

### 🌍 5. Community & Emergency Support
- Nearby plumbers (mock data)
- Water outage alerts (mock municipal data)
- Rand Water emergency contact integration
- Map-based service discovery (future-ready)

### 🔔 6. Smart Notifications
- Monthly meter reading reminders
- End-of-month alerts
- Browser-based notifications system

### 🌙 7. UI & Experience
- Dark mode / Light mode
- Mobile-first responsive design
- Clean ShadCN UI components
- Modern glassmorphism styling

---

## ✨ Key Benefits

- **Empowered Consumers:** South Africans can track their daily consumption metrics, gain visual insights to reduce waste, catch leaks early, and ensure they only pay for what they use.
- **Streamlined Operations:** Organizations and property managers can redirect personnel from manual logs to high-priority maintenance tasks.
- **Hardware Agnostic:** No need for expensive, specialized smart meter upgrades. Existing smartphones act as the reading devices, requiring zero technical training for the end-user.
- **Reduced Financial Loss:** Drastically minimizes the multi-billion rand losses typically caused by poor data standards, duplicate data entry, and inaccurate estimations.

---

## 🛠️ Technical Limitations & Ongoing Improvements

While Deep Learning streamlines the pipeline, the underlying OCR engines face specific challenges that the app actively works to mitigate:

- **Small or Sparse Fonts:** Font sizes under 12 points or unstructured meter backgrounds can occasionally lower recognition accuracy.
- **Extreme Environments:** Capturing images in pitch-black or highly obscured settings requires heavy image preprocessing, which can cause information loss.
- **Dataset Dependencies:** Achieving high accuracy requires continuously training and updating models on varied, localized, and accurately labeled datasets of South African water meter variants.

---

## 🧱 Tech Stack

### Frontend
- **Next.js 16** (App Router)
- **React 19**
- **TypeScript**
- **Tailwind CSS**
- **ShadCN UI**
- **Lucide Icons**

### State Management
- **React Context API** (WaterWiseContext)
- **LocalStorage persistence** (no backend required for MVP)

### AI / OCR
- **Tesseract.js** (OCR engine)
- **Custom preprocessing pipeline** (image cleaning + digit filtering)

### Charts & Visualization
- **Recharts**

### Notifications
- **Browser Notifications API**

### Future Integrations (Planned)
- Firebase (Auth + Cloud Storage)
- Google Maps / Mapbox API
- Backend AI API (optional LLM integration)

---

## 🏗️ Project Architecture

```
src/
├── app/              # Pages (App Router)
├── components/       # UI components
├── context/          # Global state (WaterWiseContext)
├── services/         # Business logic (OCR, AI, calculations)
├── types/            # TypeScript models
└── lib/              # Utilities
```

---

## ⚙️ Installation & Setup

### Prerequisites

- **Node.js** 18+ and **npm** (or yarn/pnpm)
- **Git**

### Steps

#### 1. Clone the Repository

```bash
git clone https://github.com/M082/waterwise.git
cd waterwise
```

#### 2. Install Dependencies

```bash
npm install
```

#### 3. Install Additional Required Packages

```bash
npm install tesseract.js recharts lucide-react
```

#### 4. Run Development Server

```bash
npm run dev
```

The app will run at: **[http://localhost:3000](http://localhost:3000)**

#### 5. Build for Production

```bash
npm run build
npm start
```

---

## 📦 Key Dependencies

```json
{
  "dependencies": {
    "next": "16.x",
    "react": "19.x",
    "react-dom": "19.x",
    "typescript": "^5.0",
    "tailwindcss": "^3.x",
    "tesseract.js": "^5.x",
    "recharts": "^2.x",
    "lucide-react": "^0.x"
  }
}
```

---

## 🔐 Core System Rule

After the first real OCR meter reading:

- ❌ **Mock data is disabled** for future months
- ✅ **All calculations use real user data**
- 📊 **Dashboard + Insights auto-update**
- 🧠 **AI engine recalculates insights dynamically**

This ensures that once a user provides their first real meter reading, the app transitions from MVP demo mode to production-ready tracking.

---

## 🌱 Future Enhancements

- **Firebase authentication** (multi-device support)
- **Cloud database** (real-time sync across devices)
- **Google Maps plumber routing** (integrated service discovery)
- **AI chatbot** (personalized water-saving advice)
- **Municipality API integration** (official tariff updates)
- **Smart leak prediction** (ML-powered anomaly detection)
- **Smart meter hardware integration** (optional upgrade path)

---

## 📝 Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -am 'Add your feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

---

## 🤝 Support

Have questions or found an issue?

- **GitHub Issues:** [Create an issue](https://github.com/M082/waterwise/issues)
- **Documentation:** See the [Wiki](https://github.com/M082/waterwise/wiki)

---

## 🙏 Acknowledgments

- Built for the South African community by developers committed to water conservation
- Powered by Tesseract.js, React, and Next.js
- Special thanks to Rand Water and local utility providers for insights

---

**Made with 💙 for a water-wise South Africa**
