<<<<<<< HEAD
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
=======
This is a new [**React Native**](https://reactnative.dev) project, bootstrapped using [`@react-native-community/cli`](https://github.com/react-native-community/cli).

# Getting Started

>**Note**: Make sure you have completed the [React Native - Environment Setup](https://reactnative.dev/docs/environment-setup) instructions till "Creating a new application" step, before proceeding.

## Step 1: Start the Metro Server

First, you will need to start **Metro**, the JavaScript _bundler_ that ships _with_ React Native.

To start Metro, run the following command from the _root_ of your React Native project:

```bash
# using npm
npm start

# OR using Yarn
yarn start
```

## Step 2: Start your Application

Let Metro Bundler run in its _own_ terminal. Open a _new_ terminal from the _root_ of your React Native project. Run the following command to start your _Android_ or _iOS_ app:

### For Android

```bash
# using npm
npm run android

# OR using Yarn
yarn android
```

### For iOS

```bash
# using npm
npm run ios

# OR using Yarn
yarn ios
```

If everything is set up _correctly_, you should see your new app running in your _Android Emulator_ or _iOS Simulator_ shortly provided you have set up your emulator/simulator correctly.

This is one way to run your app — you can also run it directly from within Android Studio and Xcode respectively.

## Step 3: Modifying your App

Now that you have successfully run the app, let's modify it.

1. Open `App.tsx` in your text editor of choice and edit some lines.
2. For **Android**: Press the <kbd>R</kbd> key twice or select **"Reload"** from the **Developer Menu** (<kbd>Ctrl</kbd> + <kbd>M</kbd> (on Window and Linux) or <kbd>Cmd ⌘</kbd> + <kbd>M</kbd> (on macOS)) to see your changes!

   For **iOS**: Hit <kbd>Cmd ⌘</kbd> + <kbd>R</kbd> in your iOS Simulator to reload the app and see your changes!

## Congratulations! :tada:

You've successfully run and modified your React Native App. :partying_face:

### Now what?

- If you want to add this new React Native code to an existing application, check out the [Integration guide](https://reactnative.dev/docs/integration-with-existing-apps).
- If you're curious to learn more about React Native, check out the [Introduction to React Native](https://reactnative.dev/docs/getting-started).

# Troubleshooting

If you can't get this to work, see the [Troubleshooting](https://reactnative.dev/docs/troubleshooting) page.

# Learn More

To learn more about React Native, take a look at the following resources:

- [React Native Website](https://reactnative.dev) - learn more about React Native.
- [Getting Started](https://reactnative.dev/docs/environment-setup) - an **overview** of React Native and how setup your environment.
- [Learn the Basics](https://reactnative.dev/docs/getting-started) - a **guided tour** of the React Native **basics**.
- [Blog](https://reactnative.dev/blog) - read the latest official React Native **Blog** posts.
- [`@facebook/react-native`](https://github.com/facebook/react-native) - the Open Source; GitHub **repository** for React Native.
>>>>>>> 00e88d4 (Initial commit)
