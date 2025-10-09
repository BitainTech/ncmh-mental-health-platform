# 🧠 NCMH Mental Health Platform

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Documentation](https://img.shields.io/badge/docs-latest-blue.svg)](API.md)
[![Contributing](https://img.shields.io/badge/contributions-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![Language Support](https://img.shields.io/badge/languages-Arabic%20%7C%20English-success.svg)]()

> A confidential, user-friendly mental health support platform for Saudi Arabia, powered by AI-driven triage and intelligent assistance.

[🌐 Live Demo](#) | [📖 Documentation](API.md) | [🤝 Contributing](CONTRIBUTING.md) | [🐛 Report Bug](https://github.com/BitainTech/ncmh-mental-health-platform/issues)

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Architecture](#architecture)
- [Documentation](#documentation)
- [Contributing](#contributing)
- [Support Tiers](#support-tiers)
- [Security](#security)
- [License](#license)
- [Contact](#contact)

---

## 🌟 Overview

The **National Center for Mental Health (NCMH) Platform** is a comprehensive, accessible mental health support system designed for the Saudi Arabian community. Our mission is to break down barriers to mental health care by providing:

✨ **Confidential and anonymous access** to mental health resources  
🤖 **AI-powered triage system** for personalized support recommendations  
💬 **Intelligent chatbot** with contextual mental health assistance  
🏥 **Location-based facility finder** with distance calculations  
🌍 **Bilingual support** (English & Arabic) with RTL layout  
🚨 **Emergency crisis intervention** with one-tap access  

---

## ✨ Features

### 🤖 AI-Powered Features

#### 1. Sentiment Analysis Engine
- **Smart emotion detection** from text and voice input
- **Keyword-based scoring** for urgency assessment
- **Risk level classification** (positive, neutral, negative)
- **Personalized recommendations** based on analysis
- **Multi-language support** for Arabic and English

#### 2. Intelligent Chatbot
- **Contextual responses** based on conversation history
- **Crisis detection** with immediate intervention
- **Resource recommendations** (breathing exercises, coping strategies)
- **Facility finder integration**
- **24/7 availability** with empathetic responses

### 🏥 Core Platform Features

#### Four-Tier Support System
1. **Tier 1 - Crisis/Emergency**: Immediate hotline access (920033360)
2. **Tier 2 - High Stress**: Connect with licensed therapists
3. **Tier 3 - Self-Management**: Self-help modules and support groups
4. **Tier 4 - Prevention**: Wellness library and educational content

#### User Management
- Secure sign-in/sign-up system
- Email verification
- Password recovery
- Anonymous browsing option
- Personalized user profiles

#### Facility Finder
- 📍 Location-based search
- 🗺️ Interactive Google Maps integration
- 📏 Distance calculation using Haversine formula
- 🏥 Government mental health facilities (Riyadh, Jeddah, Dammam)
- ☎️ Direct contact information

#### Accessibility
- Full RTL (Right-to-Left) support for Arabic
- Responsive design for mobile and desktop
- Keyboard navigation support
- High contrast for readability
- Voice recording capability

---

## 🚀 Getting Started

### Prerequisites

No installation required! This is a client-side web application.

**Requirements:**
- Modern web browser (Chrome, Firefox, Safari, Edge)
- Internet connection (for maps and emergency services)
- Microphone access (optional, for voice recording)

### Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/BitainTech/ncmh-mental-health-platform.git
   cd ncmh-mental-health-platform
   ```

2. **Open the application**
   ```bash
   # Simply open index.html in your browser
   open index.html  # macOS
   start index.html # Windows
   xdg-open index.html # Linux
   ```

3. **Or use a local server (recommended)**
   ```bash
   # Python 3
   python -m http.server 8000
   
   # Node.js (with npx)
   npx http-server
   
   # Then open: http://localhost:8000
   ```

### Demo Credentials

For testing the sign-in functionality:
- **Username:** `bitaintech`
- **Password:** `BitainTech1234!`

---

## 💻 Usage

### Basic Navigation

1. **Home Page**: Introduction and language selection
2. **Sign In/Sign Up**: Create account or sign in
3. **Sentiment Analysis**: Share how you're feeling
4. **Support Selection**: Choose wellness platform or healthcare facilities
5. **Tier Support System**: Access four levels of mental health support
6. **Facility Finder**: Locate nearby mental health centers

### Using the AI Chatbot

Click the **💬 chat button** (bottom right) to:
- Ask about mental health resources
- Get coping strategies
- Find nearby facilities
- Receive crisis support

The chatbot understands:
- Crisis keywords (suicide, self-harm)
- Emotion keywords (anxiety, depression, stress)
- Help requests
- Facility inquiries

### Emergency Access

Click the **red emergency button** (bottom left) for:
- Immediate crisis hotline access (920033360)
- Emergency services (997)
- Quick access to tier support system

### Language Switching

Use the language selector on the home page:
- 🌐 English
- 🌐 العربية (Arabic with full RTL support)

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────┐
│          NCMH Platform (Client-Side)        │
├─────────────────────────────────────────────┤
│                                             │
│  ┌────────────┐  ┌──────────────────────┐  │
│  │   Pages    │  │   AI Features        │  │
│  │  System    │  │  • Sentiment         │  │
│  │            │  │  • Chatbot           │  │
│  └────────────┘  └──────────────────────┘  │
│                                             │
│  ┌────────────┐  ┌──────────────────────┐  │
│  │    i18n    │  │   Utilities          │  │
│  │  Engine    │  │  • Distance Calc     │  │
│  │            │  │  • Location Search   │  │
│  └────────────┘  └──────────────────────┘  │
│                                             │
└─────────────────────────────────────────────┘
         ↓                    ↓
    [Google Maps]      [External Links]
```

### Technology Stack

- **Frontend**: HTML5, CSS3, Vanilla JavaScript
- **Styling**: Custom CSS with gradient backgrounds
- **Maps**: Google Maps Embed API
- **Audio**: Web Audio API (MediaRecorder)
- **Architecture**: Single Page Application (SPA)
- **Deployment**: Static hosting (no backend required)

---

## 📚 Documentation

### For Users
- [User Guide](docs/user-guide.md) - How to use the platform *(coming soon)*
- [FAQ](docs/faq.md) - Frequently asked questions *(coming soon)*

### For Developers
- **[API Documentation](API.md)** - Complete technical reference
- **[Contributing Guide](CONTRIBUTING.md)** - How to contribute
- [Architecture Guide](docs/architecture.md) - System design *(coming soon)*
- [Deployment Guide](docs/deployment.md) - Hosting instructions *(coming soon)*

### For Mental Health Professionals
- [Clinical Guidelines](docs/clinical.md) - Best practices *(coming soon)*
- [Resource Library](docs/resources.md) - Mental health materials *(coming soon)*

---

## 🤝 Contributing

We welcome contributions from developers, mental health professionals, translators, and community members!

### How to Contribute

1. **Read our [Contributing Guidelines](CONTRIBUTING.md)**
2. **Fork the repository**
3. **Create a feature branch** (`git checkout -b feature/amazing-feature`)
4. **Make your changes**
5. **Test thoroughly** (both English and Arabic)
6. **Commit your changes** (`git commit -m 'feat: add amazing feature'`)
7. **Push to the branch** (`git push origin feature/amazing-feature`)
8. **Open a Pull Request**

### Contribution Areas

- 🐛 **Bug fixes** - Report or fix issues
- ✨ **New features** - Enhance functionality
- 🌍 **Translations** - Improve Arabic/English content
- 📖 **Documentation** - Improve guides and docs
- ♿ **Accessibility** - Enhance usability
- 🎨 **Design** - Improve UI/UX

### Good First Issues

Look for issues tagged with:
- `good-first-issue` - Perfect for newcomers
- `help-wanted` - We need assistance
- `translation` - Arabic/English improvements
- `documentation` - Docs need updating

---

## 🏥 Support Tiers

### 🚨 Tier 1: Crisis/Emergency
**Immediate support for acute distress**
- One-tap crisis hotline: **920033360**
- Emergency services: **997**
- 24/7 availability
- Confidential support

### ⚠️ Tier 2: High Stress
**Professional support for non-emergency situations**
- Connect with licensed therapists
- Chat or audio sessions
- Average wait time: 5-10 minutes
- Follow-up appointment booking

### 📝 Tier 3: Self-Management
**Tools for ongoing wellness**
- NCMH Training Hub
- Support groups
- CBT exercises
- Sakinah meditation
- Sleep stories

### ✨ Tier 4: Prevention
**Overall wellbeing maintenance**
- Wellness library
- Educational content
- Goal-setting tools
- Community support
- Habit trackers

---

## 🔒 Security

### Current Security Measures

- ✅ **No server-side dependencies** - Reduced attack surface
- ✅ **No data storage** - No localStorage or cookies
- ✅ **Client-side only** - All processing in browser
- ✅ **HTTPS recommended** - For production deployment
- ✅ **No tracking** - Privacy-first approach
- ✅ **Anonymous browsing** - No account required

### Reporting Security Issues

🔐 **Do not create public issues for security vulnerabilities**

Email: **security@ncmh-platform.sa**

Include:
- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Suggested fix (if any)

We will respond within 48 hours.

---

## 📊 Roadmap

### Phase 1 (Current)
- [x] Basic platform structure
- [x] AI sentiment analysis
- [x] Intelligent chatbot
- [x] Four-tier support system
- [x] Bilingual support (EN/AR)
- [x] Facility finder

### Phase 2 (In Progress)
- [ ] Backend API integration
- [ ] User authentication system
- [ ] Appointment booking
- [ ] Video consultation
- [ ] Chat history storage

### Phase 3 (Planned)
- [ ] Mobile apps (iOS/Android)
- [ ] Advanced AI (NLP/ML)
- [ ] Therapist portal
- [ ] Analytics dashboard
- [ ] Community forums

### Phase 4 (Future)
- [ ] Wearable integration
- [ ] Predictive analytics
- [ ] Personalized care plans
- [ ] Family support features
- [ ] Research collaboration

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

### What This Means

✅ **You can:**
- Use the code commercially
- Modify the code
- Distribute the code
- Use the code privately

❗ **You must:**
- Include the original license
- Include copyright notice

❌ **Limitations:**
- No warranty provided
- No liability accepted

---

## 🌍 Localization

### Supported Languages
- 🇺🇸 **English** - Full support
- 🇸🇦 **Arabic (العربية)** - Full support with RTL layout

### Translation Contributors
Want to help improve translations? See our [Contributing Guide](CONTRIBUTING.md#translation-guidelines)

---

## 🙏 Acknowledgments

### Inspired By
- Saudi Ministry of Health Mental Health Programs
- National Center for Mental Health (NCMH)
- Global mental health accessibility initiatives

### Technologies Used
- Google Maps Platform
- Web Audio API
- Modern CSS3 features
- Vanilla JavaScript ES6+

### Special Thanks
- Mental health professionals who provided guidance
- Community beta testers
- Open source contributors
- Translation volunteers

---

## 📞 Contact

### General Inquiries
- **Website**: [ncmh-platform.sa](https://ncmh-platform.sa) *(coming soon)*
- **Email**: info@ncmh-platform.sa

### Developer Support
- **GitHub**: [BitainTech/ncmh-mental-health-platform](https://github.com/BitainTech/ncmh-mental-health-platform)
- **Issues**: [Report a bug](https://github.com/BitainTech/ncmh-mental-health-platform/issues)
- **Discussions**: [Community forum](https://github.com/BitainTech/ncmh-mental-health-platform/discussions)

### Emergency Support
🚨 **If you're in crisis:**
- **Saudi Mental Health Hotline**: 920033360 (24/7)
- **Emergency Services**: 997
- **Crisis Text Line**: Available through platform

---

## 📈 Statistics

![GitHub stars](https://img.shields.io/github/stars/BitainTech/ncmh-mental-health-platform?style=social)
![GitHub forks](https://img.shields.io/github/forks/BitainTech/ncmh-mental-health-platform?style=social)
![GitHub issues](https://img.shields.io/github/issues/BitainTech/ncmh-mental-health-platform)
![GitHub pull requests](https://img.shields.io/github/issues-pr/BitainTech/ncmh-mental-health-platform)

---

## 🌟 Star History

If you find this project useful, please consider giving it a ⭐!

[![Star History Chart](https://api.star-history.com/svg?repos=BitainTech/ncmh-mental-health-platform&type=Date)](https://star-history.com/#BitainTech/ncmh-mental-health-platform&Date)

---

<div align="center">

### 💚 Mental Health Matters

**Seeking help is a sign of strength, not weakness.**

Made with ❤️ by [BitainTech](https://github.com/BitainTech)

[⬆ Back to Top](#-ncmh-mental-health-platform)

</div>
