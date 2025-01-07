webdeki dosya böyle şu anda bu arada

module.exports = {

  root:true,

  ignorePatterns: ['/*', '!/src', '*.json', '*.css', '*.svg', '/src/fonts'],

  settings: {

    'import/resolver': {

      alias: {

        map: [['@','./src']],

        extensions: ['.js', '.jsx', '.ts', '.d.ts', '.tsx'],

      },

      node: {

        paths: ['src'],

        extensions: ['.js', '.jsx', '.ts', '.tsx'],

      },

    },

    react: { version: '18.2' }

  },

  env: {

    browser: true,

    node: true,

    es2021: true,

  },

  extends: [

    'eslint:recommended',

    'plugin:react/recommended',

    'plugin:react-hooks/recommended',

    'plugin:jsx-a11y/recommended',

    'plugin:prettier/recommended',

    'plugin:import/recommended',

  ],

  overrides: [

    {

      files: ['*.test.js', '*.test.jsx'],

      env: {

        jest: true,

      },

      rules: {},

    },

  ],

  parserOptions: {

    ecmaVersion: 'latest',

    sourceType: 'module',

  },

  plugins: ['react-refresh', 'import', 'jsx-a11y', 'react-hooks', 'prettier',],

  rules: {

    'prettier/prettier': 'error',

    'import/order': [

      1,

      {

        groups: ['external', 'builtin', 'internal', 'sibling', 'parent', 'index'],

      },

    ],

    'react/react-in-jsx-scope': 'off',

    'import/prefer-default-export': 'off',

    'react/prop-types': 'off',

    'react-hooks/exhaustive-deps': 'off',

    'no-console': 'warn',

    'no-undefined':'error'

    _// 'prefer-arrow-callback': 'warn',_

  },

}