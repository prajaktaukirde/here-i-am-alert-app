# Here I Am - Emergency Alert & Safety App

**Here I Am** is a personal safety and emergency alert mobile application built with Flutter and Firebase. Designed primarily for women's safety and quick emergency response, the app allows users to instantly send SOS alerts containing their exact live location, street address, and a Google Maps link to their trusted emergency contacts via SMS.

---

## 🌟 Key Features

- **🚨 One-Tap SOS Alert**: A prominent, ripple-animated emergency button to instantly dispatch distress messages.
- **📳 Shake-to-Alert**: Automatically triggers emergency SMS dispatch when the phone is shaken vigorously (configured using hardware accelerometer via `flutter_shake_plugin`).
- **📍 Real-Time GPS & Address Resolution**: Uses device GPS coordinates (`location`) and reverse geocoding (`geocoder`) to determine the exact street address and generate a direct Google Maps pin link (`http://maps.google.com/?q=lat,long`).
- **📲 Automated SMS Dispatch**: Sends distress SMS messages with location details to all saved emergency contacts directly via the device's cellular network (`sms_maintained`).
- **👥 Emergency Contacts Manager**: Easily import and select emergency contacts from your device phonebook (`contacts_service`) and synchronize them to Firebase Realtime Database.
- **🔐 Phone Authentication**: Secure user login with Firebase Phone Number Authentication.
- **🎨 Interactive UI**: Custom 3D animated slide-out drawer, ripple-wave animations, onboarding guides (`fancy_on_boarding`), and Montserrat typography.

---

## 🏗️ Tech Stack & Dependencies

- **Framework**: Flutter (Dart)
- **Backend & Database**: Firebase Auth, Firebase Realtime Database
- **Geolocation & Mapping**: `location`, `geocoder`, `geolocator`
- **Telephony & Hardware**: `sms_maintained` (Direct SMS), `flutter_shake_plugin` (Accelerometer)
- **Device Integrations**: `contacts_service`, `permission_handler`
- **UI & Animations**: `fancy_on_boarding`, custom ripple wave painter, Montserrat fonts

---

## 📱 How It Works

1. **Sign In**: User signs in using their phone number through Firebase Phone Auth.
2. **Add Emergency Contacts**: Import trusted friends, family members, or emergency responders from your phonebook. Contacts are saved to Firebase under your account.
3. **Triggering an Alert**:
   - Tap the **Send Alert** button on the home screen, **OR**
   - Vigorously **shake the phone** if unable to reach the screen.
4. **Distress Delivery**:
   - The app instantly fetches the device's current latitude and longitude.
   - It performs reverse geocoding to retrieve the physical street address.
   - An SMS is composed in the format:
     ```text
     Help Me!
     [Physical Street Address]
     http://maps.google.com/?q=[Latitude],[Longitude]
     ```
   - The SMS is immediately dispatched to every contact in your emergency list.

---

## ⚙️ Getting Started

### Prerequisites
- Flutter SDK (`>=2.7.0 <3.0.0` or compatible Dart SDK)
- Android Studio / Xcode
- A Firebase project with Phone Authentication and Realtime Database enabled

### Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/prajaktaukirde/here-i-am-alert-app.git
   cd here-i-am-alert-app
   ```

2. **Install Flutter packages**:
   ```bash
   flutter pub get
   ```

3. **Configure Firebase**:
   - For Android: Place your `google-services.json` inside the `android/app/` directory.
   - For iOS: Place `GoogleService-Info.plist` inside `ios/Runner/`.

4. **Run the application**:
   ```bash
   flutter run
   ```

---

## 🔒 Required Device Permissions

To function effectively during emergencies, the app requests the following device permissions:
- **Location (Fine & Coarse)**: To capture current GPS coordinates and resolve the street address.
- **SMS**: To send background distress text messages.
- **Contacts**: To read and select emergency contacts from your phonebook.
- **Sensors / Accelerometer**: To detect shake motions for hands-free triggering.

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE.md](LICENSE.md) file for details.
