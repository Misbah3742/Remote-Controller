# 📱 iOS Installation Guide

Complete guide to installing Remote Controller on your iPhone or iPad.

## Table of Contents
- [Method 1: Xcode (Recommended for Developers)](#method-1-xcode)
- [Method 2: AltStore (Easiest for Non-Developers)](#method-2-altstore)
- [Method 3: Sideloadly (Alternative)](#method-3-sideloadly)
- [Method 4: TestFlight (Coming Soon)](#method-4-testflight)

---

## Method 1: Xcode

**Requirements:**
- Mac computer with macOS 12.0+
- Xcode 14.0+
- Apple ID (free account works)
- iPhone/iPad with iOS 12.0+
- USB cable

### Step 1: Install Prerequisites

1. **Install Xcode** from the Mac App Store
2. **Install Flutter:**
   ```bash
   # Download Flutter SDK
   cd ~/development
   git clone https://github.com/flutter/flutter.git -b stable
   
   # Add to PATH (add to ~/.zshrc or ~/.bash_profile)
   export PATH="$PATH:$HOME/development/flutter/bin"
   
   # Verify installation
   flutter doctor
   ```

3. **Install CocoaPods:**
   ```bash
   sudo gem install cocoapods
   ```

### Step 2: Clone and Setup Project

```bash
# Clone the repository
git clone https://github.com/Misbah3742/Remote-Controller.git
cd Remote-Controller/app

# Get Flutter dependencies
flutter pub get

# Install iOS dependencies
cd ios
pod install
cd ..
```

### Step 3: Configure Signing

1. Open Xcode:
   ```bash
   open ios/Runner.xcworkspace
   ```

2. Select the **Runner** project in the left sidebar
3. Go to **Signing & Capabilities** tab
4. **Uncheck** "Automatically manage signing" if you see errors
5. **Check** "Automatically manage signing" again
6. Select your **Team** (your Apple ID)
7. Xcode will create a provisioning profile automatically

**If you see errors:**
- Make sure you're signed in: Xcode → Settings → Accounts
- Add your Apple ID if not present
- Change the **Bundle Identifier** to something unique (e.g., `com.yourname.remotecontroller`)

### Step 4: Deploy to Device

1. Connect your iPhone/iPad via USB
2. **Trust your computer** on the device when prompted
3. Select your device in Xcode (top toolbar)
4. Run the app:
   ```bash
   flutter run -d YOUR_DEVICE_NAME
   ```

### Step 5: Trust Developer Certificate

1. On your iOS device, go to:
   **Settings → General → VPN & Device Management**
2. Find your developer certificate
3. Tap it and select **Trust**

**Done!** The app is now installed and running.

---

## Method 2: AltStore

**AltStore** allows you to sideload apps without Xcode. Free developer accounts can install up to 3 apps, valid for 7 days (needs weekly refresh).

**Requirements:**
- Windows PC or Mac
- iPhone/iPad with iOS 12.4+
- iTunes and iCloud installed (Windows)
- Same WiFi network for PC and device

### Step 1: Install AltStore on Computer

1. **Download AltStore:**
   - Windows: https://altstore.io/
   - Mac: https://altstore.io/

2. **Install Prerequisites (Windows only):**
   - Install [iTunes](https://www.apple.com/itunes/) (Desktop version, NOT Microsoft Store)
   - Install [iCloud](https://support.apple.com/en-us/HT204283) (Desktop version)

3. **Install AltServer:**
   - Extract the downloaded ZIP
   - Run the installer
   - Launch AltServer (runs in system tray)

### Step 2: Install AltStore on iPhone/iPad

1. Connect your device via USB
2. Click the **AltServer icon** in system tray (Windows) or menu bar (Mac)
3. Select **Install AltStore → [Your Device]**
4. Enter your **Apple ID** and password
   - This is only used locally, never sent to third parties
   - Use an app-specific password if you have 2FA enabled

5. On your device:
   - Go to **Settings → General → VPN & Device Management**
   - Trust your Apple ID

6. **Enable WiFi Sync:**
   - Open iTunes/Finder
   - Select your device
   - Check "Sync with this iPhone over Wi-Fi"

### Step 3: Build the IPA

**Option A: Use Pre-built IPA (If Available)**
- Check the [Releases page](https://github.com/Misbah3742/Remote-Controller/releases)
- Download `remote-controller.ipa`

**Option B: Build from Source (Requires Mac + Flutter)**
```bash
cd Remote-Controller/app

# Build IPA
flutter build ipa --release

# The IPA is located at:
# build/ios/ipa/remote_controller.ipa
```

**Option C: Request Someone to Build**
- Ask in the GitHub Issues if you need a build

### Step 4: Install IPA via AltStore

1. Transfer the IPA to your iPhone/iPad:
   - AirDrop, iCloud Drive, or any file sharing method

2. On your iPhone/iPad:
   - Open **AltStore** app
   - Tap **My Apps**
   - Tap the **+** button
   - Navigate to the IPA file
   - Select it to install

3. AltStore will install the app (takes 1-2 minutes)

### Step 5: Refresh Apps Weekly

**Important:** Apps sideloaded with a free account expire after 7 days.

**To refresh:**
1. Make sure your device and computer are on the same WiFi
2. AltServer must be running on your computer
3. Open AltStore on your device
4. Tap **Refresh All**

**Enable automatic refresh:**
- AltStore → Settings → Enable "Background Refresh"
- This refreshes apps automatically when possible

---

## Method 3: Sideloadly

**Sideloadly** is an alternative to AltStore with a simpler interface.

**Requirements:**
- Windows or Mac
- iPhone/iPad with iOS 7+
- iTunes installed

### Step 1: Install Sideloadly

1. Download from: https://sideloadly.io/
2. Install and launch Sideloadly

### Step 2: Get the IPA

Follow the same IPA building steps as AltStore (Method 2, Step 3)

### Step 3: Sideload the App

1. Connect your iPhone/iPad via USB
2. In Sideloadly:
   - **IPA file:** Browse and select `remote_controller.ipa`
   - **Apple Account:** Enter your Apple ID
   - **Device:** Select your device from dropdown
3. Click **Start**
4. Enter your Apple ID password when prompted
5. Wait for installation to complete

### Step 4: Trust Developer

1. On your device: **Settings → General → VPN & Device Management**
2. Trust your Apple ID certificate

---

## Method 4: TestFlight

**Status:** Coming Soon

TestFlight is the official Apple beta testing platform. No computer needed!

We're working on making Remote Controller available via TestFlight. This will be the easiest installation method:

1. Install TestFlight from the App Store
2. Click the invitation link (will be posted in README)
3. Install the app

**Advantages:**
- ✅ No computer required
- ✅ No 7-day expiration
- ✅ Easy updates
- ✅ No certificate trust needed

Follow the project for updates!

---

## Troubleshooting

### "Untrusted Developer" Error
**Solution:** Settings → General → VPN & Device Management → Trust the certificate

### "Unable to Install"
**Possible causes:**
- Device storage full
- Bundle ID conflict (delete old version first)
- Provisioning profile expired

**Solution:** Delete the app if installed, restart device, try again

### Xcode: "Failed to create provisioning profile"
**Solution:**
- Check you're signed in: Xcode → Settings → Accounts
- Change Bundle Identifier to something unique
- Try: Product → Clean Build Folder, then rebuild

### AltStore: "Could not find AltServer"
**Solution:**
- Make sure AltServer is running in system tray/menu bar
- Verify both devices are on the same WiFi
- Restart AltServer
- Turn off VPN if running

### Sideloadly: "Application already installed"
**Solution:**
- Delete the existing app from your device
- Or change the Bundle ID in Sideloadly settings

### App Crashes on Launch
**Solution:**
- Make sure iOS version is 12.0 or higher
- Try: Delete app, restart device, reinstall
- Check Xcode console for error messages if debugging

### "This app cannot be installed because its integrity could not be verified"
**Solution:**
- Delete the app
- Restart your device
- Reinstall using the same method

### Weekly Refresh Not Working (AltStore)
**Solution:**
- Enable WiFi and ensure same network
- AltServer must be running
- Try manual refresh: AltStore → Refresh All
- Check Settings → AltStore → Background Refresh is ON

---

## Additional Resources

- **Flutter iOS Setup:** https://docs.flutter.dev/get-started/install/macos#ios-setup
- **AltStore FAQ:** https://altstore.io/faq/
- **Sideloadly Guide:** https://sideloadly.io/#howto
- **Apple Developer:** https://developer.apple.com/

---

## Need Help?

- **GitHub Issues:** https://github.com/Misbah3742/Remote-Controller/issues
- **Discussions:** https://github.com/Misbah3742/Remote-Controller/discussions

If you successfully install the app, consider leaving feedback or contributing to the documentation!

---

**Note:** Sideloading apps is permitted by Apple for personal use and development. This project is open source and free.