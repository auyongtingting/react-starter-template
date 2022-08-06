# react-starter-template

## Create a new react project

```
npm create vite@latest
-> enter project_name
-> choose react
-> choose react-ts (Typescript)
cd project_name 
npm install 
git init (if you want to initialise git)
npm run dev (if you want to run the project)
```

##  Install CSS framework to enable effective, efficient and accurate styling (Tailwind CSS)

```
npm install -D tailwindcss postcss autoprefixer daisyui
npx tailwindcss init -p
```

- Edit tailwing.config.cjs

```
/** @type {import('tailwindcss').Config} */ 
module.exports = {
  content: [
    "./index.html",
    "./src/**/*.{vue,js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [require("daisyui")],
}
```

- Edit index.css

```
@tailwind base;
@tailwind components;
@tailwind utilities;

//everything else remains
```

## Introduce router and redesign file structure

```
npm install -D vite-plugin-pages
npm install react-router react-router-dom
```

- Edit vite.config.ts

```
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'
import Pages from 'vite-plugin-pages'

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [react(), Pages(),]
})
```

- Create folders and move App.tsx to src/pages

```
mkdir src/pages
mkdir src/components
mkdir src/redux 
mkdir src/hooks 
mkdir src/utils
mv src/App.tsx src/pages
```

- Edit App.tsx import paths

```
import reactLogo from '../assets/react.svg'
import '../App.css'
```

- Edit main.tsx 

```
import App from './pages/App'
```

##  Install ESLint and allow linting

```
npm install eslint -D
npm init @eslint/config
-> (y)
-> To check syntax, find problems, and enforce code style
-> JavaScript modules (import/export)
-> React
-> TypeScript Yes
-> Browser
-> Answer Question
-> JavaScript
-> Spaces
-> Single
-> Unix
-> No Semicolon
-> yes to install
-> Choose how to install
```

- Add more rules to ESLint by modifying .eslintrc.cjs

```
module.exports = {
	'ignorePatterns': ['**/*.cjs'],
	'env': {
		'browser': true,
		'node': true,
		'es2021': true
	},
	'extends': [
		'eslint:recommended',
		'plugin:react/recommended',
		'plugin:react/jsx-runtime'
	],
	'parserOptions': {
		'ecmaFeatures': {
			'jsx': true
		},
		'ecmaVersion': 'latest',
		'sourceType': 'module'
	},
	'plugins': [
		'react'
	],
	'rules': {
		'indent': ['error', 2],
		'linebreak-style': ['error', 'unix'],
		'quotes': ['error', 'single'],
		'jsx-quotes': ['error', 'prefer-single'],
		'semi': ['error', 'never'],
		'no-unused-vars': [2, { 'args': 'none' }],
		'comma-dangle': ['error']
	}
}
```

##  Start coding and run your project
```
npm run dev 
``` 
