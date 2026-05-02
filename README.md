# Fuel

A native iOS calorie and nutrition tracker powered by AI. Log meals in plain English, scan barcodes, sync with HealthKit, and track macros with an Apple Watch companion and home screen widget.

---

## Features

- **AI Food Parsing** — Type what you ate in plain English and Claude parses it into calories, protein, carbs, and fat with confidence scores
- **Barcode Scanning** — Scan packaged foods for instant nutrition data
- **HealthKit Sync** — Reads and writes calorie and macro data to Apple Health
- **Apple Watch App** — View your daily totals and log quick entries from your wrist
- **Home Screen Widget** — See your calorie ring and macros at a glance
- **Offline Mode** — Local USDA food database works without internet
- **Daily Reminders** — Optional push notifications to keep you on track

---

## Tech Stack

- **Language:** Swift
- **UI:** SwiftUI
- **Data:** SwiftData
- **AI:** Claude (claude-haiku) via Anthropic API
- **Health:** HealthKit
- **Watch:** WatchConnectivity
- **Widget:** WidgetKit

---

## Project Structure

```
Fuel/
├── Fuel/                  # Main iOS app
│   ├── Features/          # Feature modules (food logging, dashboard, settings)
│   ├── ViewModels/        # Business logic
│   ├── Navigation/        # App navigation
│   ├── Components/        # Reusable UI components
│   ├── AppConfiguration.swift  # Centralized config
│   └── AppLogger.swift    # Logging system
├── FuelKit/               # Shared Swift package
├── FuelWatch/             # Apple Watch app
├── FuelWidgets/           # Home screen widgets
└── FuelTests/             # Unit tests
```

---

## Getting Started

### Requirements

- Xcode 15+
- iOS 17+
- Apple Developer account (for HealthKit and App Groups)
- Anthropic API key

### Setup

1. Clone the repo:
```bash
git clone https://github.com/ngoc-2/FUEL.git
cd FUEL
```

2. Copy the config templates:
```bash
cp Fuel/Info.plist.template Fuel/Info.plist
cp Fuel/Fuel.entitlements.template Fuel/Fuel.entitlements
```

3. Open `Fuel.xcodeproj` in Xcode

4. Update `AppConfiguration.swift` with your details:
   - Set your privacy policy, support, and terms URLs
   - Add your Anthropic API key in Settings at runtime

5. Register your App Group (`group.com.yourname.fuel`) in the Apple Developer Portal and update it in `AppConfiguration.swift`

6. Build and run on a real device (HealthKit does not work in the simulator)

---

## Configuration

Key settings are in `Fuel/AppConfiguration.swift`:

| Setting | Default | Description |
|--------|---------|-------------|
| `anthropicModel` | claude-haiku | AI model for food parsing |
| `healthKitEnabled` | true | HealthKit read/write |
| `barcodeScanningEnabled` | true | Camera barcode scanning |
| `offlineModeEnabled` | true | Local food database |
| `cloudKitEnabled` | false | iCloud sync |

---

## How to Use

1. **Log food** — Tap the + button and type what you ate, e.g. "2 scrambled eggs and toast with butter". The AI parses it instantly.
2. **Scan a barcode** — Tap the barcode icon to scan packaged food.
3. **Check your progress** — The dashboard shows your calorie ring and macro breakdown for the day.
4. **Apple Watch** — View your ring and log quick entries directly from your watch.
5. **Widget** — Add the Fuel widget to your home screen for an at-a-glance view.

---