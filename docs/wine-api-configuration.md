# Wine API Configuration

The Wine API is a nodejs typescript application using express. The code is hosted on a [Github repository](https://github.com/blazarlabs-io/wine-api).

## Typescript

```js
{
  "compilerOptions": {
    "target": "es6",
    "lib": ["es5", "es6", "dom"],
    "experimentalDecorators": true,
    "emitDecoratorMetadata": true,
    "module": "commonjs",
    "moduleResolution": "node",
    "baseUrl": "src/",
    "typeRoots": ["./src/types", "./node_modules/@types"],
    "resolveJsonModule": true,
    "outDir": "./dist",
    "removeComments": true,
    "allowSyntheticDefaultImports": true,
    "esModuleInterop": true,
    "forceConsistentCasingInFileNames": true,
    "strict": true,
    "noImplicitReturns": true,
    "noFallthroughCasesInSwitch": true,
    "skipLibCheck": true
  },
  "include": ["./src/**/*.tsx", "./src/**/*.ts", "./src/**/*.json", "./src/**/*.pem"],
  "exclude": ["node_modules", "test/**/*.ts"]
}
```

## EsLint

```js
{
  "parser": "@typescript-eslint/parser",
  "extends": ["plugin:@typescript-eslint/recommended", "prettier"],
  "plugins": ["prettier"],
  "parserOptions": {
    "ecmaVersion": 2018,
    "sourceType": "module"
  },
  "rules": {
    "prettier/prettier": "error",
    "@typescript-eslint/no-extra-semi": "on",
    "no-console": "error"
  }
}
```

## NPM Scripts

```js
"scripts": {
    "build": "npx tsc",
    "dev": "TZ='UTC' nodemon src/index.ts",
    "prod": "TZ='UTC' npm build && npm start",
    "lint": "eslint src/**/*.ts",
    "format": "eslint src/**/*.ts --fix",
    "start": "npm run build && forever start dist/index.js",
    "stop": "forever stop dist/index.js"
  },
```
