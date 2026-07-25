# ⚡ VoltCam — Smart Grid Monitoring & IoT Appliance Protection System

[![Build Android APK](https://github.com/arispacco/PowerVision/actions/workflows/build_apk.yml/badge.svg)](https://github.com/arispacco/PowerVision/actions/workflows/build_apk.yml)
[![Flutter](https://img.shields.io/badge/Flutter-3.24.x-02569B?logo=flutter)](https://flutter.dev)
[![Gemini AI](https://img.shields.io/badge/Gemini%20AI-1.5%20Flash-8E75B2?logo=google)](https://deepmind.google/technologies/gemini/)
[![Firebase](https://img.shields.io/badge/Firebase-Cloud%20Functions%20%26%20Firestore-FFCA28?logo=firebase)](https://firebase.google.com)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

**VoltCam** transforme les signaux d'un boîtier domotique / IoT en alertes de protection compréhensibles, en scores de confiance de quartier (**GridTrust**) et en conseils personnalisés via l'**IA Gemini**.

Projet développé dans le cadre du **GDG Hackathon 2026** (Build with AI).

---

## 📸 Aperçu de l'Application (Screenshots)

<div align="center">

| 🗺️ Carte Live Grid Monitoring | 📱 Tableau de bord Boîtier IoT & Protect Mode |
|:---:|:---:|
| ![Carte Live](captures/Screenshot%202026-07-25%20221909.png) | ![Boîtier IoT](captures/Screenshot%202026-07-25%20222035.png) |

| 🤖 Assistant IA Gemini (FR / EN / Pidgin) | 📢 Réseau Social & Signalement Citoyen |
|:---:|:---:|
| ![Assistant IA](captures/Screenshot%202026-07-25%20221957.png) | ![Réseau Social](captures/Screenshot%202026-07-25%20221934.png) |

| 👥 Communauté & Score GridTrust |
|:---:|
| ![Communauté](captures/Screenshot%202026-07-25%20222011.png) |

</div>

---

## ✨ Fonctionnalités Principales

1. 🗺️ **Carte Live Grid Monitoring** : Visualisation en temps réel des zones électriques (Polygones d'instabilité, pannes confirmées, maintenance ENEO) avec bascule dynamique de thème (Clair / Sombre).
2. 🔌 **Tableau de Bord Boîtier IoT & Protect Mode** :
   - Graphiques de tension temps réel (*Sparkline Painter*).
   - Jauge radiale de score de risque (*Risk Score Gauge*).
   - Jumelage réseau en direct via **WebSocket (`ws://<IP>:8080/ws`)** avec l'application Android physique/émulateur faisant office de boîtier matériel.
3. 🤖 **Assistant IA (Gemini 1.5 Flash)** :
   - Recommandations personnalisées sur les appareils électriques (réfrigérateurs, climatiseurs).
   - Support multilingue natif : **Français**, **English**, et **Pidgin / Camfranglais**.
4. 📢 **Signalement Citoyen & Réseau Social** : Publication et confirmation communautaire des coupures et instabilités de tension.
5. 🛡️ **Score GridTrust** : Algorithme de confiance basé sur le croisement des données IoT indépendantes et des signalements citoyens.

---

## 🏗️ Architecture Technique

```
┌─────────────────────────────────────────────────────────────┐
│                      VoltCam Mobile App                     │
│               (Flutter + Riverpod + GoRouter)              │
└──────────────┬──────────────────────────────┬───────────────┘
               │                              │
     WebSocket │ (Télémétrie 1.5s)   Rest API │ (Gemini AI & Firebase)
               ▼                              ▼
┌──────────────────────────────┐ ┌───────────────────────────┐
│     VoltCam Box Android      │ │     Google Gemini AI      │
│   (Simulateur Matériel IoT)  │ │   & Firebase Firestore    │
└──────────────────────────────┘ └───────────────────────────┘
```

- **Frontend** : Flutter 3.24.x (Dart), Flutter Riverpod 2.6, GoRouter 14.x, Google Maps Flutter.
- **IA** : Google Generative AI (`google_generative_ai`) avec Gemini 1.5 Flash.
- **IoT & Réseau** : WebSockets (`web_socket_channel`), BLE GATT Specs (UUID `4f4c5443-1000-8000-8000-00805f9b34fb`).
- **Backend & Persistence** : Firebase Cloud Functions, Cloud Firestore, Flutter Secure Storage (`encrypted_storage`).

---

## 🚀 Installation & Exécution Locale

### Prérequis
- [Flutter SDK](https://flutter.dev/docs/get-started/install) `>=3.0.0`
- [Android Studio](https://developer.android.com/studio) ou VS Code avec l'extension Flutter.

### Lancement
```bash
# 1. Cloner le dépôt
git clone https://github.com/arispacco/PowerVision.git
cd PowerVision/voltcam

# 2. Installer les dépendances
flutter pub get

# 3. Lancer l'application
flutter run
```

---

## 📦 CI/CD & Build Automatisé

Le projet est configuré avec un workflow **GitHub Actions** (`.github/workflows/build_apk.yml`) qui génère automatiquement l'APK de release Android à chaque commit sur la branche principale.

L'APK compilé est téléchargeable directement dans l'onglet **Actions** de GitHub (*voltcam-release-apk*).

---

## 📄 Licence & Crédits

Développé par l'équipe **VoltCam** pour le **GDG Hackathon 2026 (Build with AI)**.
Licence MIT.
