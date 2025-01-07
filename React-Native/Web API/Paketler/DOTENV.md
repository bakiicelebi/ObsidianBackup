https://www.npmjs.com/package/react-native-dotenv

https://www.npmjs.com/package/react-native-config

https://dev.to/dallington256/using-env-file-in-react-native-application-3961


babel.config.js

module.exports = {
  presets: ['module:@react-native/babel-preset'],
  plugins: [
    ['react-native-reanimated/plugin'],
    ["module:react-native-dotenv", {
      "envName": "APP_ENV",
      "moduleName": "@env",
      "path": ".env",
      "safe": false,
      "allowUndefined": true,
      "verbose": false
    }]
  ],
  env: {
    production: {
      plugins: ['react-native-paper/babel'],
    },
  },
};




