# 🎮 Remote Controller

Transform your iPhone, iPad, or Android device into a wireless game controller for your PC!

![Platform](https://img.shields.io/badge/platform-iOS%20%7C%20Android-blue)
![Flutter](https://img.shields.io/badge/Flutter-3.0%2B-02569B?logo=flutter)
![License](https://img.shields.io/badge/license-MIT-green)

## ✨ Features

- 🎮 **Full Xbox 360 Controller Emulation** - Works with any PC game that supports controllers
- 📱 **Cross-Platform** - Single codebase for iOS and Android
- 🌐 **Low Latency WiFi Connection** - ~16ms response time at 60Hz
- 🎯 **Dual Analog Sticks** - Precise joystick control with visual feedback
- 🔘 **All Standard Buttons** - A, B, X, Y, bumpers, triggers, D-pad, and more
- 🎨 **Modern UI** - Clean, intuitive landscape interface
- 🔌 **Easy Setup** - Connect with just your PC's IP address

## 📱 Screenshots

```
┌─────────────────────────────────┐
│    Remote Controller Connected  │
│  ws://192.168.1.10:8080/ws ✓    │
├─────────────────────────────────┤
│                                 │
│    ◎              ◎             │
│   Left           Right          │
│  Stick           Stick          │
│                                 │
│  LB  [====] LT  RT [====]  RB  │
│                                 │
│         Ⓨ                       │
│      Ⓧ    Ⓑ                    │
│         Ⓐ                       │
│                                 │
│    ☰ Start    Back ☰            │
│                                 │
│         ↑                       │
│       ←   →                     │
│         ↓                       │
└─────────────────────────────────┘
```

## 🚀 Quick Start

### PC Server Setup (Windows)

#### Prerequisites
- Windows 10/11
- [.NET 8 SDK](https://dotnet.microsoft.com/download)
- [ViGEmBus Driver](https://github.com/ViGEm/ViGEmBus/releases) - Download and install `ViGEmBusSetup_x64.msi`

#### Installation
1. Install ViGEmBus driver (run as Administrator)
2. Clone this repository:
   ```bash
   git clone https://github.com/Misbah3742/Remote-Controller.git
   cd Remote-Controller/server
   ```
3. Run the server:
   ```bash
   dotnet restore
   dotnet run
   ```
4. Note your PC's local IP address (shown in console, e.g., `192.168.1.10`)

### Mobile App Setup

#### For iPhone/iPad

**Option 1: Install via Xcode (Requires Mac)**
1. Install [Flutter](https://docs.flutter.dev/get-started/install)
2. Clone the repository and navigate to app folder:
   ```bash
   cd Remote-Controller/app
   flutter pub get
   cd ios && pod install && cd ..
   ```
3. Connect your iPhone/iPad via USB
4. Run:
   ```bash
   flutter run -d ios
   ```

**Option 2: Build IPA for Sideloading**
1. Build the IPA:
   ```bash
   flutter build ipa --release
   ```
2. The IPA will be at: `build/ios/ipa/remote_controller.ipa`
3. Use [AltStore](https://altstore.io/) or [Sideloadly](https://sideloadly.io/) to install on your device

**Detailed iOS setup guide:** See `docs/IOS_INSTALLATION.md`

#### For Android

**Option 1: Install APK directly**
1. Build the APK:
   ```bash
   cd Remote-Controller/app
   flutter build apk --release
   ```
2. Transfer `build/app/outputs/flutter-apk/app-release.apk` to your Android device
3. Enable "Install from Unknown Sources" in Settings
4. Install the APK

**Option 2: Install via USB**
```bash
flutter run -d android
```

## 🎯 How to Use

1. **Start the PC Server**
   - Run `dotnet run` in the `server` folder
   - Windows Firewall may prompt - allow access on Private networks
   - Note the IP address shown (e.g., `192.168.1.10`)

2. **Connect from Mobile**
   - Ensure your phone/tablet is on the same WiFi as your PC
   - Open the Remote Controller app
   - Tap the settings icon ⚙️
   - Enter `ws://YOUR_PC_IP:8080/ws` (e.g., `ws://192.168.1.10:8080/ws`)
   - Tap "Connect"

3. **Start Gaming!**
   - Your PC will now see an Xbox 360 controller
   - Open any game and configure the controller
   - Enjoy wireless gaming!

## 📁 Project Structure

```
Remote-Controller/
├── app/                    # Flutter mobile app
│   ├── lib/
│   │   ├── main.dart
│   │   ├── screens/
│   │   │   ├── home_screen.dart
│   │   │   └── controller_screen.dart
│   │   ├── widgets/
│   │   │   ├── joystick.dart
│   │   │   ├── button.dart
│   │   │   └── dpad.dart
│   │   ├── models/
│   │   │   └── controller_state.dart
│   │   └── services/
│   │       └── websocket_service.dart
│   ├── pubspec.yaml
│   └── README.md
├── server/                 # .NET PC server
│   ├── Program.cs
│   ├── ControllerServer.csproj
│   └── README.md
├── docs/                   # Documentation
│   └── IOS_INSTALLATION.md
└── README.md
```

## 🔧 Troubleshooting

**Connection fails:**
- Verify both devices are on the same WiFi network
- Check Windows Firewall isn't blocking port 8080
- Ping your PC from mobile to verify network connectivity
- Make sure server is running (`dotnet run`)

**Controller not detected in games:**
- Ensure ViGEmBus is properly installed
- Check Device Manager for "Virtual Xbox 360 Controller"
- Restart the server and reconnect

**High latency:**
- Use 5GHz WiFi if available
- Reduce distance between device and router
- Close background apps on mobile device
- Check WiFi signal strength

**App crashes on iOS:**
- Ensure you're running iOS 12.0 or later
- Check for error messages in Xcode console
- Try rebuilding: `flutter clean && flutter pub get`

**App won't install on iPhone/iPad:**
- See detailed guide: `docs/IOS_INSTALLATION.md`
- Make sure your Apple ID is configured in Xcode
- Trust the developer certificate in Settings > General > VPN & Device Management

## 🛠️ Development

### Requirements
- Flutter 3.0+
- Dart 3.0+
- .NET 8 SDK
- Xcode 14+ (for iOS)
- Android Studio (for Android)

### Building from Source

```bash
# Get Flutter dependencies
cd app
flutter pub get

# Run in debug mode
flutter run

# Build for production
flutter build apk --release  # Android
flutter build ipa --release  # iOS
```

### Server Development

```bash
cd server
dotnet restore
dotnet run --configuration Release
```

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [ViGEmBus](https://github.com/ViGEm/ViGEmBus) - Virtual Gamepad Emulation Framework
- [Flutter](https://flutter.dev) - UI Framework
- [ASP.NET Core](https://dotnet.microsoft.com) - Server Framework

## 📮 Support

Having issues? Please [open an issue](https://github.com/Misbah3742/Remote-Controller/issues) on GitHub.

---

Made with ❤️ by [Misbah3742](https://github.com/Misbah3742)