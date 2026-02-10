# AmazonX (Flutter + Node + MongoDB)

A full stack E commerce app built with **Flutter** (BLoC) + **Node/Express** + **MongoDB**.  
Includes user shopping flows (browse/search/cart/orders) and an in-app **Admin** area for managing products and offers.

---

## Tech stack

- **Frontend:** Flutter (BLoC, Hydrated BLoC)
- **Backend:** Node.js + Express
- **Database:** MongoDB Atlas (Mongoose)
- **Media:** Cloudinary (for Admin image uploads)

---

## Setup & Run

> The project uses **one shared** `config.env` file at the repo root:
> - **Backend** reads it from `server/index.js`
> - **Flutter** loads it from `lib/main.dart`

---

1) Install prerequisites
 - Flutter SDK (project uses Dart SDK >= 3.1.5)
 - Node.js + npm
 - A MongoDB Atlas database user (username/password)
 - (Optional) Cloudinary account for Admin uploads

2) Create config.env (shared by backend + Flutter)
    IMPORTANT:
 - Android emulator uses 10.0.2.2 to reach your host machine
 - iOS simulator can usually use localhost
 - Real device must use your LAN IP (e.g. 192.168.x.x)
   
cat > config.env <<'EOF'

 ---------- Backend ----------
 
PORT=3000
DB_USERNAME=YOUR_MONGODB_USERNAME
DB_PASSWORD=YOUR_MONGODB_PASSWORD

 ---------- Flutter ----------
 
 Base URL of the backend (must be reachable from your device/emulator)
URI=http://10.0.2.2:3000

---------- Cloudinary (optional, Admin image uploads) ----------

CLOUDINARY_CLOUDNAME=YOUR_CLOUD_NAME
CLOUDINARY_UPLOADPRESET=YOUR_UNSIGNED_UPLOAD_PRESET
EOF

3) Start the backend server
cd server
npm install
npm run dev
Health check: open http://localhost:3000/amazonx (returns "Welcome to AmazonX!")

4) Run the Flutter app
cd ..
flutter pub get
flutter run

