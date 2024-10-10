# Setting Up React Native on Ubuntu without Android Studio

This guide will walk you through setting up React Native development on Ubuntu without Android Studio. We will manually install the Android SDK and set up the necessary tools for building and running React Native applications.

## 1. **Installing ADB and Node.js**

First, ensure your system is up-to-date and install ADB and Node.js:

```bash
sudo apt update
curl -sL https://deb.nodesource.com/setup_21.x | sudo -E bash -
sudo apt install -y adb
sudo apt install -y nodejs
```

## 2. **Check Node.js and npm Versions**

Verify that Node.js and npm were installed correctly by checking their versions:

```bash
node -v
npm -v
```

## 3. **Install JDK**

React Native requires Java Development Kit (JDK) to be installed. We will install **OpenJDK 17**:

```bash
sudo apt install openjdk-17-jdk
java -version
```

## 4. **Install Android SDK (Without Android Studio)**

Instead of installing **Android Studio**, we will install the **Android SDK** manually:

1. **Download Android Command Line Tools**:
   - Download the tools from [this link](https://github.com/1xrohit/Setup-ReactNative-on-Ubuntu-without-Android-Studio/releases/download/AndroidSDK/Android.zip).

2. **Extract the downloaded archive** to a suitable location on your system (e.g., `~/Android/`):

```bash
unzip Android.zip -d ~/Android
```

## 5. **Configure Java and Android SDK in `.bashrc`**

Add the necessary environment variables to your `.bashrc` file to make the Android SDK and Java available globally:

1. Open `.bashrc` using `nano`:

```bash
nano ~/.bashrc
```

2. Add the following lines to the end of the file:

```bash
# Android SDK
export ANDROID_HOME=$HOME/Android/Sdk
export PATH=$PATH:$ANDROID_HOME/emulator
export PATH=$PATH:$ANDROID_HOME/platform-tools
export PATH=$PATH:$ANDROID_HOME/cmdline-tools/latest/bin

# Java configuration
export JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64
export PATH=$PATH:$JAVA_HOME/bin
```

Make sure to replace `/home/user/Android` with the actual path where you extracted the Android SDK.

3. After editing, save the file and exit (`Ctrl + X`, `Y`, `Enter`).

4. Reload your `.bashrc` for the changes to take effect:

```bash
source ~/.bashrc
```

## 6. **Creating a New React Native Application**

### a) **Uninstall old global React Native CLI**

If you have the older `react-native-cli` installed globally, uninstall it first:

```bash
npm uninstall -g react-native-cli @react-native-community/cli
```

### b) **Initialize a New React Native Project**

You can now create a new React Native project using the latest version of the CLI:

```bash
npx @react-native-community/cli@latest init AwesomeProject
```

### c) **Start Metro Bundler**

Once the project is created, navigate into your project directory and start the Metro bundler:

```bash
cd AwesomeProject
npm start
```

### d) **Run the Application on Android**

Finally, run the application on your Android device or emulator:

```bash
npm run android
```

## 7. **Troubleshooting**

### **Check Connected Devices**

To make sure your Android device is connected, run:

```bash
adb devices
```

If no devices show up, try the following steps.

### **Connecting Your Phone to the Computer**

1. **Use a good USB cable** to connect your phone to your computer.
2. After connecting, a pop-up should appear on your phone asking whether you want to allow USB debugging. **Allow it** and check the "Always allow from this computer" option to prevent this prompt from appearing in the future.
3. After allowing, check again:

```bash
adb devices
```

### **If the Device is Still Not Recognized**

- Restart the ADB server by running:
  
  ```bash
  adb kill-server
  adb start-server
  ```

- Ensure that your device is set to **File Transfer (MTP)** mode, not just charging, by checking the notification panel when the device is connected.

Once the device appears in the `adb devices` list, you can run `npm run android` again to start the app on your phone.

---

### **Congratulations!**
You have successfully set up React Native on Ubuntu and are able to create and run your projects on an Android device without Android Studio.
