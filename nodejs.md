# NodeJS

## Instalar

### Debian
```bash
curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
sudo apt install -y nodejs
sudo apt install -y npm
```

### Fedora
```bash
sudo dnf install nodejs
```

## Typescript
```bash
sudo npm install -g typescript
sudo npm install -g ts-node
```

## Yarn
```bash
sudo npm install -g yarn
```

## React
```bash
sudo npm install -g create-react-app
```

## Vue
```bash
sudo npm install -g @vue/cli
sudo npm install -g @vue/cli-init
```

## NativeScript

```bash
sudo npm install -g nativescript
```

```bash
sudo dnf install java-latest-openjdk
sudo alternatives --config javac
dnf install java-devel
```

```bash
export JAVA_HOME=$(update-alternatives --query javac | sed -n -e 's/Best: *\(.*\)\/bin\/javac/\1/p')
export ANDROID_HOME="/home/ezeroldan/Android/Sdk"
export PATH="${PATH}:${ANDROID_HOME}/emulator:${ANDROID_HOME}/tools/:${ANDROID_HOME}/platform-tools/"
```

```bash
vue init nativescript-vue/vue-cli-template <project-name>
npm i

emulator -avd Pixel_3a_XL_API_30 
tns run android --emulator 

```

[NativeScript-Vue With TypeScript](https://nativescript.org/blog/nativescript-vue-with-class-components/)
