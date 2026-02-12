# AmazonX

A full stack Amazon style **E-commerce clone** built with **Flutter** (client) + **Node/Express** (server) + **MongoDB**.  
This is a **learning/demo project** — great for practicing real app flows like auth, product browsing, cart, orders, and an admin panel.

---

## ✨ What’s inside
- Auth (email/password), persisted login (Hydrated Bloc)
- Home (carousel + deals + dynamic offers)
- Category-wise products + search
- Product details + ratings (only for ordered products)
- Cart + Save for Later + recommendations
- Orders + order details + browsing history + wishlists
- Admin panel (add/delete products, offers, analytics graph, manage orders)
- Cloudinary image upload (admin)
- Google Pay / Buy Now flow (test-mode friendly)

---

## 🚀 Quick Start (clone + run)

~~~bash
set -euo pipefail
cd "/Users/alok/Desktop"
git clone https://github.com/alokpriyadarshii/AmazonX.git
cd "AmazonX"
flutter doctor
flutter pub get
flutter run
~~~

> The app needs a `config.env` file (next section). Create it before `flutter run` if you haven’t.

---

## 🔐 Create `config.env` (required)

Create a file named **`config.env`** in the **project root** (`AmazonX/config.env`).  
This single file is used by **both**:
- Flutter app (loaded via `flutter_dotenv`)
- Node server (loaded via `dotenv`)

Example:

~~~bash
set -euo pipefail
cd "/Users/alok/Desktop/AmazonX"
cat > config.env <<'EOF'
PORT=3000
DB_USERNAME=your_mongodb_username
DB_PASSWORD=your_mongodb_password

# Flutter base URL (see note below)
URI=http://localhost:3000

# Cloudinary (admin uploads)
CLOUDINARY_CLOUDNAME=your_cloud_name
CLOUDINARY_UPLOADPRESET=your_upload_preset
EOF
~~~

**URI note (important):**
- iOS simulator / desktop: `http://localhost:3000`
- Android emulator: `http://10.0.2.2:3000`
- Physical phone: `http://<your-lan-ip>:3000` (example `http://192.168.1.10:3000`)

---

## 🧩 Start Backend Server (required for API)

Open a second terminal:

~~~bash
set -euo pipefail
cd "/Users/alok/Desktop/AmazonX/server"
npm i
npm run dev
~~~

---

## 🧹 If build issues (optional)

~~~bash
set -euo pipefail
cd "/Users/alok/Desktop/AmazonX"
flutter clean
flutter pub get
dart format .
flutter analyze
flutter test
~~~

---

## 📦 Release build (optional)

~~~bash
set -euo pipefail
cd "/Users/alok/Desktop/AmazonX"
flutter build apk --release
flutter build ios --release
~~~

---

## 📁 Project structure (high level)

~~~text
AmazonX/
  android/
  ios/
  linux/
  macos/
  windows/
  web/
  assets/
    images/
    fonts/
    gpay.json
    applepay.json
  lib/
    main.dart
    src/
      config/
      data/
      logic/
      presentation/
      utils/
  server/
    index.js
    routes/
    model/
    middlewares/
    package.json
  pubspec.yaml
  pubspec.lock
  README.md
  config.env
~~~

---

## 🛠 Customize
- **API base URL**: `config.env` → `URI=...`
- **Theme / constants**: `lib/src/utils/constants/`
- **Routes / navigation**: `lib/src/config/router/`
- **State management (Bloc/HydratedBloc)**: `lib/src/logic/`
- **Admin Cloudinary upload**: `config.env` → `CLOUDINARY_*` (used in `lib/src/data/repositories/admin_repository.dart`)
- **Backend entry**: `server/index.js`

> Folder name is **AmazonX**. Flutter package name in `pubspec.yaml` is **flutter_amazon_clone_bloc** — you can rename it if you want, but it’s not required.

---

## 🧪 Test Credentials
- **User**
  - Email: `user@email.com`
  - Password: `123456`
- **Admin**
  - Email: `admin@email.com`
  - Password: `123456`

---

## 📝 Note
If you test ordering with Google Pay, you may need Google Pay test mode setup (allowlist / test cards) depending on device/account setup.
