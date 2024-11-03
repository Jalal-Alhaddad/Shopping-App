# `useContext`

> In **React**, `useContext` is a **hook** that allows you to access data stored in a React context directly within a functional component.
>
>**Context** is used to pass data through a component tree without having to pass props down manually at each level.

## Purpose of `useContext`

The main purpose of useContext is to enable sharing of global data (such as theme settings, user authentication status, language preferences, or any data you want to access across many components) in a way that's easy to maintain and avoids "prop drilling."

## Usage of `useContext`

- **Create a Context**: First, create a context using `React.createContext` with a default value, if necessary.
- **Provide the Context**: Use the context provider (e.g., `<ThemeContext.Provider>`) to wrap the part of the component tree where you want the context data accessible.
- **Consume the Context with useContext**: Inside a child component, call useContext with the context you created.

Create a new file ThemeContext.js

```javascript
import React, { createContext, useState, useContext } from "react";
import lightTheme from "../themes/lightTheme.json";
import darkTheme from "../themes/darkTheme.json";

const ThemeContext = createContext();

export const ThemeProvider = ({ children }) => {
  const [isDarkTheme, setIsDarkTheme] = useState(false);

  const toggleTheme = () => {
    setIsDarkTheme((prev) => !prev);
  };

  const theme = isDarkTheme ? darkTheme : lightTheme;

  return (
    <ThemeContext.Provider value={{ theme, isDarkTheme, toggleTheme }}>
      {children}
    </ThemeContext.Provider>
  );
};

export const useTheme = () => useContext(ThemeContext);
```

Provide the Context

```javascript
import React from "react";
import { Provider as PaperProvider } from "react-native-paper";
import { ThemeProvider, useTheme } from "./components/ThemeContext";

export default function App() {

  return (
    <SafeAreaProvider>
      <ThemeProvider>
        <Main />
      </ThemeProvider>
    </SafeAreaProvider>
  );
}

function Main() {

  const { theme } = useTheme(); // Accessing the theme from context

  return (
    <PaperProvider theme={theme}>
      <NavigationContainer>
        <RootNavigator />
      </NavigationContainer>
      <StatusBar style="auto" />
    </PaperProvider>
  );
}
```

Access Theme

```javascript
import React from 'react'
import { StyleSheet, View } from "react-native";
import { Surface, Text, Switch } from "react-native-paper";
import { useTheme } from "../components/ThemeContext";

export default function HelpScreen(props) {

  const { isDarkTheme, toggleTheme } = useTheme();

    return (
      <Surface style={styles.container}>
        <Text variant="displaySmall" style={styles.title}>
          Help Screen
        </Text>
        <View style={styles.switchContainer}>
          <Text variant="titleSmall" style={styles.subtitle}>
            Current Theme: {isDarkTheme ? "Dark" : "Light"}
          </Text>
          <Switch value={isDarkTheme} onValueChange={toggleTheme} />
        </View>
      </Surface>
    );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
  },
  title: {
    margin: 20,
  },
  subtitle: {
    marginBottom: 16,
    fontSize: 16,
  },
  switchContainer: {
    flexDirection: "row",
    alignItems: "center",
    justifyContent: "space-between",
    marginBottom: 5,
    paddingHorizontal: 30,
  },
  switchLabel: {
    fontSize: 16,
  },
});
```
