# Shopping Application

## 1. Create Expo application

1. Create react-native application using [Expo](https://docs.expo.dev/get-started/create-a-project/)
2. Use **Blank** template [`--template`]
3. Install additional libraries to run in web mode

```bash
npx create-expo-app@latest --template

npx expo install react-native-web react-dom @expo/metro-runtime
```

## 2. Install Additional Packages

1. Install [Expo Vector Icons](https://docs.expo.dev/guides/icons/)
2. Install [React Native Paper](https://reactnativepaper.com/)
3. Visit [icons.expo.fyi](https://icons.expo.fyi/Index) to browse `@expo/vector-icons` icons set
4. Install `@react-native-async-storage/async-storage` to manage local storage in the application
5. Install `react-native-paper-dropdown` to use Dropdown component in the application

```bash
npx expo install `
@expo/vector-icons `
react-native-paper `
@react-native-async-storage/async-storage `
react-native-paper-dropdown
```

## 3. Install React Navigator

- Visit [React Navigator](https://reactnavigation.org/) to learn how to install React Navigator
- Install [Tabs Navigator](https://reactnavigation.org/docs/tab-based-navigation)
- Install [Stack Navigator](https://reactnavigation.org/docs/stack-navigator)
- Install dependencies into an Expo managed project

```bash
npx expo install `
@react-navigation/native `
@react-navigation/bottom-tabs `
@react-navigation/stack `
react-native-screens `
react-native-safe-area-context
```

## 4. Start the app

- Use the following command to test your application.

```bash
npm run web
```

- Then stop the application using `Ctrl+C`

## 6. Project Folder Structure

### Create folders

```bash
|- components
|- navigation
|- screens
|- themes
|- utils
```

### Create files

```bash
|- components
    |- ThemeContext.js

|- navigation
    |- RootNavigator.js
    |- MainNavigator.js
    |- ShopNavigator.js

|- screens
    |- HomeScreen.js
    |- HelpScreen.js
    |- NotFoundScreen.js
    |- ShopViewScreen.js
    |- ProductViewScreen.js
    |- ProductEditScreen.js

|- server
    |- api

|- themes
    |- darkTheme.json
    |- lightTheme.json

|- utils
    |- api.js
```

## 7. Configure the server

1. Download [server](./assets/server.zip) zip file into the project folder
2. Extract it, so you should find a `server` folder into your project folder
3. This folder contain the api code to be used in your mobile app
4. Install `concurrently` package to help run the api with the mobile app

```bash
npm install concurrently --save-dev
```

5. Update `package.json` by adding the following lines to **scripts**

```json
  "scripts": {

    "seed": "cd server && npm i && npm run seed",
    "start:server": "cd server && npm start",
    "dev": "concurrently \"npm run web\" \"npm run start:server\""
  },
```

6. Run `npm run seed` to install server' packages and seed the database
7. Run `npm run dev` to test your application, at this moment you have 2 running projects, the server and your app
8. You can use `shop-api.http` from the `server` folder to test the API

## 8. File Naming

- **PascalCase** for screens, components, and navigators
- **lowercase** for folders
- Use **Screen** suffix for screens like `LoginScreen`
- Use **Navigator** suffix for navigators like `RootNavigator`

## 9. Package.JSON

- You should have `package.json` like this in your project folder

```javascript
{
  "name": "shop-mobile-sky24",
  "version": "1.0.0",
  "main": "expo/AppEntry.js",
  "scripts": {
    "start": "expo start",
    "android": "expo start --android",
    "ios": "expo start --ios",
    "web": "expo start --web",
    "seed": "cd server && npm i && npm run seed",
    "start:server": "cd server && npm start",
    "dev": "concurrently \"npm run web\" \"npm run start:server\""
  },
  "dependencies": {
    "@expo/metro-runtime": "~3.2.3",
    "@expo/vector-icons": "^14.0.3",
    "@react-native-async-storage/async-storage": "1.23.1",
    "@react-navigation/bottom-tabs": "^6.6.1",
    "@react-navigation/native": "^6.1.18",
    "@react-navigation/stack": "^6.4.1",
    "expo": "~51.0.28",
    "expo-status-bar": "~1.12.1",
    "react": "18.2.0",
    "react-dom": "18.2.0",
    "react-native": "0.74.5",
    "react-native-paper": "^5.12.5",
    "react-native-paper-dropdown": "^2.3.1",
    "react-native-safe-area-context": "4.10.5",
    "react-native-screens": "3.31.1",
    "react-native-web": "~0.19.10"
  },
  "devDependencies": {
    "@babel/core": "^7.20.0",
    "concurrently": "^9.0.1"
  },
  "private": true
}
```

## 10 Create Screen & Navigators

- Create all screens, and navigators
- Add `screenOptions={{ headerShown: false }}` to `Stack.Navigator` component in `RootNavigator`
- Add `options={{ title: "View Shop" }}` to all `Stack.Screen` components in `ShopNavigator`, change names accordantly

## 11 Theming

> [Design System](./Design%20System.md) for more information about Design System

- [Material Design](https://m3.material.io/)
- [react native paper](https://reactnativepaper.com/)
- [Material 3 Design Kit](https://www.figma.com/community/file/1035203688168086460/material-3-design-kit)
- [Material Theme Builder](https://www.figma.com/community/plugin/1034969338659738588/material-theme-builder)

### Why need UI library

Design systems make it easier for developers and designers to ensure a cohesive look and feel and streamline collaboration.
