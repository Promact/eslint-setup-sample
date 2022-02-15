This repository shows how you can configure Eslint for your Angular project easily. Also install eslint plugin for vscode from extension marketplace in vscode.

**Step 1** : First Install All required pakages

```shell
npm install --save-dev eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin eslint-plugin-import eslint-plugin-eslint-comments eslint-plugin-promise eslint-plugin-jasmine eslint-config-prettier eslint-plugin-prettier prettier
```

`eslint` The base package
`@typescript-eslint/parser` Helps eslint understand typescript
`@typescript-eslint/eslint-plugin` Helps eslint load typescript plugins
`eslint-plugin-import` Import/export conventions best practices as per ES2015+
`eslint-plugin-eslint-comments` ESLint comment restrictions
`eslint-plugin-promise` ESlint Best practices for using JavaScript Promise
`eslint-config-prettier eslint-plugin-prettier prettier` To configure prettier styling
`eslint-plugin-jasmine` Supports rules for Jasmine tests

**Step 2** : Add `.eslintrc.js` copy it from the file in repo or use the following content


```javascript
/* eslint-disable no-undef */
module.exports = {
    env: {
        browser: true,
        es2021: true,
        jasmine: true,
    },
    extends: [
        "eslint:recommended",
        "plugin:@typescript-eslint/eslint-recommended",
        "plugin:@typescript-eslint/recommended",
        "plugin:prettier/recommended",
        "plugin:jasmine/recommended",
        "eslint-plugin-import",
        "eslint-plugin-eslint-comments",
        "eslint-plugin-promise"
    ],
    parser: "@typescript-eslint/parser",
    parserOptions: {
        ecmaVersion: "latest",
        sourceType: "module",
    },
    plugins: ["@typescript-eslint", "prettier"],
    rules: {},
    overrides: [
        {
            files: ["*.spec.ts"],
            plugins: ["jasmine"],
            rules: {
                "@typescript-eslint/unbound-method": "off",
                MicrosoftEdge: "off",
                "axe/forms": "off",
            },
        },
    ],
};
```

**Step 3** : Add following command in your `package.json`

```json
{
    "scripts": {
        "lint" : "eslint <name of the folder with source code> --ext .ts,.json --fix --cache"
    }    
}
```