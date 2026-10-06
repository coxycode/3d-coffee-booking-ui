<div align="center">

  <img src="assets/app_icon.png" alt="Swirlo App Icon" width="128" height="128" style="border-radius: 28px; box-shadow: 0 10px 30px rgba(0,0,0,0.5);" />

  # ☕ SWIRLO
  ### 3D Food & Coffee E-Commerce Mobile App UI

  [![Flutter](https://img.shields.io/badge/Flutter-3.0+-02569B?style=for-the-badge&logo=flutter&logoColor=white)](https://flutter.dev)
  [![Dart](https://img.shields.io/badge/Dart-3.0+-0175C2?style=for-the-badge&logo=dart&logoColor=white)](https://dart.dev)
  [![Dependencies](https://img.shields.io/badge/Dependencies-0%20(Pure%20SDK)-2ea44f?style=for-the-badge)](pubspec.yaml)
  [![Platforms](https://img.shields.io/badge/Platforms-Android%20%7C%20iOS%20%7C%20Web%20%7C%20Desktop-orange?style=for-the-badge)]()
  [![License](https://img.shields.io/badge/License-Permissive%20Commercial%20+%20No--Sue-yellow?style=for-the-badge)](LICENSE)

  <p align="center">
    <b>A photorealistic, 3D interactive iced coffee & beverage e-commerce mobile application crafted in Flutter.</b><br>
    Features full 360° drag-to-rotate drink viewing, autoplay video-like intro, custom size pricing, reactive cart, and full demo checkout.
  </p>

</div>

---

## ✨ Features

- 🌀 **Interactive 360° 3D Drink Viewer**: Drag your finger or cursor left and right across the product view to spin and inspect the beverage smoothly across high-definition frames. Includes an auto-spin toggle and one-tap angle reset.
- 🎬 **Cinematic Autoplay Intro**: Video-style 90-frame animated sequence showcasing the milk and chocolate pour into iced cold brew. Tap anywhere to skip straight to the menu.
- 🎨 **Boutique Dark Roast Aesthetic**: Curated color palette featuring deep roasted espresso tones (`#12100E`), velvet card surfaces (`#1B1714`), warm caramel highlights (`#C9925C`), and silky typography.
- 📱 **Complete E-Commerce Flow**:
  - **Menu Showcase**: Dynamic drink listings with custom price tags, tasting notes, and frame-synced imagery.
  - **Product Customization**: Sizing choice chips (Regular / Large with dynamic upcharges) and live quantity adjustments.
  - **Reactive Shopping Cart**: Add to cart with SnackBar notifications, increment/decrement counts, and swipe-to-dismiss items.
  - **Multi-Method Checkout**: Demo payment gateway supporting UPI ID, Credit/Debit cards (with simulated card approval/decline testing), and Cash on Delivery (COD).
  - **Order Confirmation**: Celebratory order summary screen featuring live order ID generation and drink badges.
- ⚡ **Zero Third-Party Dependencies**: Built **100% with pure Flutter SDK widgets** (`MaterialApp`, `InheritedNotifier`, `AnimationController`, `CustomPainter`, `Image.asset`). No external packages from `pub.dev` required — lightning-fast builds with zero dependency rot.
- 📱 **Fully Configured App Icons**: Custom-tailored high-resolution app icons pre-configured across Android (hdpi to xxxhdpi), iOS (AppIcon xcassets), Web (favicon & PWA icons), macOS, and Windows (.ico).

---

## 📸 3D Sequence & Asset System

The app utilizes a continuous sequence of 90 high-definition photorealistic frames stored in [`assets/swirlo_frames/`](file:///c:/Users/acer/Downloads/swirlo_app%20%281%29/assets/swirlo_frames):

| Frame Range | Visual Stage | Used In |
|---|---|---|
| `frame_001.jpg` | Crystal clear cold brew over ice | Midnight Cold Brew Art, Intro Start |
| `frame_045.jpg` | First milk and cocoa ribbons meeting | Cocoa Cloud Art, 360° Scrubbing |
| `frame_070.jpg` | Hand-marbled espresso and dark chocolate swirl | Marble Mocha Art, 360° Scrubbing |
| `frame_085.jpg` | Finished signature pour with ice condensation | **Official App Icon**, Marketing Art |
| `frame_090.jpg` | Complete signature swirl latte | Swirl Latte Art, Order Success Screen |

---

## 🚀 Getting Started

### Prerequisites
- [Flutter SDK](https://docs.flutter.dev/get-started/install) (version 3.0.0 or higher)
- Android Studio / Xcode / Chrome / VS Code

### Installation & Run

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/swirlo.git
   cd swirlo
   ```

2. **Fetch packages (Flutter SDK only):**
   ```bash
   flutter pub get
   ```

3. **Run on your connected device or emulator:**
   ```bash
   # Run on default connected device (Android / iOS / Desktop)
   flutter run

   # Or run in Chrome (Web)
   flutter run -d chrome

   # Or run on Windows Desktop
   flutter run -d windows
   ```

4. **Verify tests & analyzer:**
   ```bash
   flutter analyze
   flutter test
   ```

---

## 💳 Payment Gateway Integration

The project includes an extensible [`PaymentGateway`](file:///c:/Users/acer/Downloads/swirlo_app%20%281%29/lib/core/payment_gateway.dart) interface with an offline `DemoPaymentGateway` for rapid UI development:

- **Test Card (Success)**: `4242 4242 4242 4242` (Any future MM/YY and 3-digit CVV)
- **Test Card (Decline Simulation)**: `4000 0000 0000 0002`

To connect to a production provider (Stripe, Razorpay, Square, PayPal):
1. Implement the `PaymentGateway` interface in `lib/core/payment_gateway.dart`.
2. Connect your live API/SDK token and verification endpoint.
3. Supply your live gateway to `PaymentScreen(gateway: LivePaymentGateway())`.

---

## 📂 Project Architecture

```text
swirlo/
├── android/                 # Android native build files & mipmap launcher icons
├── ios/                     # iOS native build files & AppIcon xcassets
├── web/                     # Web build files, favicon, and PWA icons
├── windows/                 # Windows desktop build files & app_icon.ico
├── macos/                   # macOS native runner & assets
├── assets/
│   ├── app_icon.png         # Master 1024x1024 high-res app icon
│   └── swirlo_frames/       # 90 sequential 3D beverage frames (001 - 090)
├── lib/
│   ├── main.dart            # App entrypoint and CartScope provider
│   ├── core/
│   │   ├── cart_state.dart  # CartModel & CartScope state management
│   │   ├── frames.dart      # Frame paths, constants & indexing utilities
│   │   ├── models.dart      # Drink models, size upcharges & menu catalog
│   │   ├── payment_gateway.dart # Abstract gateway interface & mock implementation
│   │   └── theme.dart       # AppColors, typography & Material3 dark theme
│   └── features/
│       ├── intro/           # Autoplay video-like animated intro with skip
│       ├── menu/            # Drink catalog cards and navigation
│       ├── product/         # Product detail with interactive 360° 3D viewer
│       ├── cart/            # Line items, quantity modifiers, dismissal
│       └── payment/         # Checkout form, validation & order success
├── test/
│   └── widget_test.dart     # Smoke test suite
├── LICENSE                  # Permissive commercial license & covenant not to sue
├── pubspec.yaml             # Flutter assets and configuration
└── README.md                # Project documentation
```

---

## 📜 Permissive Commercial License & Legal Terms

This project is released under a **Permissive Commercial License with an Ironclad Covenant Not to Sue and Complete Limitation of Liability**.

### Summary of Rights & Restrictions

| Action | Allowed? | Notes |
|---|:---:|---|
| **Edit, Modify & Fork** | ✅ YES | You can modify any code, frame, or UI element. |
| **Use for Personal Projects** | ✅ YES | Free for learning, showcases, and personal apps. |
| **Commercial Use** | ✅ YES | You can use it in commercial apps, stores, and businesses. |
| **Sell Products & Apps Built With This** | ✅ YES | You can sell apps, templates, or client projects derived from this. |
| **White-Label & Re-Brand** | ✅ YES | You can re-skin, re-brand, and distribute under your own brand. |
| **File Legal Claims / Lawsuits Against Author** | ❌ **STRICTLY PROHIBITED** | **You expressly agree never to bring any lawsuit, legal case, arbitration, or dispute against the original author/creator.** |

### 🛡️ Disclaimer of Warranties & Covenant Not to Sue

> **THE SOFTWARE AND ALL ASSETS ARE PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, TITLE, AND NONINFRINGEMENT.**
>
> **IN NO EVENT SHALL THE ORIGINAL AUTHOR(S), CREATOR(S), OR COPYRIGHT HOLDER(S) BE LIABLE FOR ANY CLAIM, DAMAGES, LOSSES, LIABILITIES, COSTS, OR INJURIES (WHETHER DIRECT, INDIRECT, INCIDENTAL, SPECIAL, OR CONSEQUENTIAL), REGARDLESS OF THE CAUSE OF ACTION.**
>
> **BY DOWNLOADING, COPYING, MODIFYING, RUNNING, DISTRIBUTING, OR SELLING THIS SOFTWARE OR ANY ASSOCIATED MEDIA, YOU EXPRESSLY WAIVE ANY AND ALL RIGHTS TO COMMENCE, PROSECUTE, OR PARTICIPATE IN ANY LAWSUIT, ARBITRATION, OR LEGAL ACTION AGAINST THE AUTHOR(S). ALL COMMERCIAL RISKS, COMPLIANCE REQUIREMENTS (INCLUDING PCI-DSS, PAYMENT PROCESSING, TAXES, AND CONSUMER LAWS), AND OPERATIONAL RESPONSIBILITIES REST ENTIRELY WITH YOU.**

For full legal terms, see the [LICENSE](LICENSE) file.

---

<div align="center">
  <sub>Crafted with passion for premium 3D mobile experiences. Enjoy your swirl! ☕</sub>
</div>
