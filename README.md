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

Check out this <a href="https://icons.expo.fyi/Index" target="_blank">icons.expo.fyi</a>.

```bash
npx expo install `
@expo/vector-icons `
react-native-paper
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

```
