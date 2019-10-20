# React Native - Minesweeper Game

**LAST UPDATE:** 10/2019

Follow me: https://www.linkedin.com/in/vitor-cordeiro-921a5697/

### 1. Introduction

A study about React Native technology. The goal was to build the famous Minesweeper game.

### 2. Tecnologies

- React 16.6.3;
- React Native 0.57.8;

### 3. Installation

1. Instalar o git e o clip

```
$ sudo apt-get install git
$ sudo apt install xclip
```

2. Installing Node.js and NPM:

```
sudo apt-get update
sudo apt-get install nodejs
sudo apt-get install npm
```

3. Installing React Native CLI:

```
sudo npm install -g react-native-cli
sudo npm install -g react-native-run-android
```

4. Installing Android Studio:

- [Download link](https://developer.android.com/studio/);
- Extract folder of your choice and run or installer "./bin/studio.sh";
- Select the option to open an existing project;

![Android Studio Menu](https://raw.githubusercontent.com/vitorfmc/react-native-minesweeper-game/master/src/images/image_android_studio.png)

- Open or create a Project just to load the Android Studio interface;

### 4. Executing the application

1. Execute the emulator;
2. If you is running the firs time, or added a new lib, run: 

```
rm -rf node_modules && npm install"
```

3. In the project folder: 

```
$ npm start -- --reset-cache
```

4. In another terminal, execute in the project: 

```
$ react-native run-android
```

5. In the emulator, enabled hot deploy by pressing "ctrl + m";

### 5. Generation APK

1. Genetate a keystore:

```
$ keytool -genkey -v -keystore my-release-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000
```

2. Add the keystore in project folder: "android/app"
3. Add the follow lines in the file: "android/gradle.properties":

```
MYAPP_RELEASE_STORE_FILE=my-release-key.keystore
MYAPP_RELEASE_KEY_ALIAS=my-key-alias
MYAPP_RELEASE_STORE_PASSWORD=*****
MYAPP_RELEASE_KEY_PASSWORD=*****
```

4. Modify the file "android/app/build.gradle" by adding:

```
android {
    ...
    defaultConfig { ... }
    signingConfigs {
        release {
            if (project.hasProperty('MYAPP_RELEASE_STORE_FILE')) {
                storeFile file(MYAPP_RELEASE_STORE_FILE)
                storePassword MYAPP_RELEASE_STORE_PASSWORD
                keyAlias MYAPP_RELEASE_KEY_ALIAS
                keyPassword MYAPP_RELEASE_KEY_PASSWORD
            }
        }
    }
    buildTypes {
        release {
            ...
            signingConfig signingConfigs.release
        }
    }
}
...
```

5. In the "android" project subfolder run the command:

```
$ ./gradlew assembleRelease -x verifyReleaseResources  (Se for o Alpha)
$ ./gradlew assembleRelease (Demais projetos)
```

6. Pegar o arquivo "app-release" gerado na subpasta do projeto: "/android/app/build/outputs/apk"


**Obs:** Para o passo-a-passo detalhado, [clique aqui](https://facebook.github.io/react-native/docs/signed-apk-android).
