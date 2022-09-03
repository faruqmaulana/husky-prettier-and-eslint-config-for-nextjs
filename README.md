## Husky, Prettier, Eslint and Commitlint for your nextjs project setup

#### I usually use husky, prettier and eslint for my project setup, but I often have problems when I setup my nextjs project. So I decided to make cheetsheat configuration and you can use it for personal or commercial usage. Thank you hopefully it will help save your time in project setup and increase your productivity. happy coding ✨✨<img src="https://media.giphy.com/media/WUlplcMpOCEmTGBtBW/giphy.gif" width="30"> 



```bash
yarn add husky -D -W
yarn add prettier -D -W
yarn add eslint -D -W
yarn add eslint-config-next -D -W
yarn add -D -W @commitlint/{config-conventional,cli}
md .husky
touch .prettierignore
touch .prettierrc
touch .eslintrc.json
touch commitlint.config.js
npx husky add .husky/pre-commit "yarn format"
npx husky add .husky/pre-commit "yarn lint"
npx husky add .husky/pre-push "yarn build"
npx husky add .husky/commit-msg 'npx --no-install commitlint --edit "$1"'
npm set-script prepare "husky install"
npm set-script format "prettier --write ."
npm set-script lint "eslint . --fix"
yarn prepare
yarn husky install
```

copy to your `.prettierignore` file
```bash
.next
dist
node_modules
```
copy to your `.prettierrc` file
```bash
{
  "trailingComma": "es5",
  "tabWidth": 2,
  "semi": true,
  "singleQuote": true
}
```
copy to your `.eslintrc.json` file
```bash
{
  "extends": ["next", "next/core-web-vitals", "eslint:recommended"],
  "globals": {
    "React": "readonly"
  },
  "rules": {
    "no-unused-vars": [1, { "args": "after-used", "argsIgnorePattern": "^_" }]
  }
}
```
copy to your `commitlint.config.js` file
```bash
// build: Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)
// ci: Changes to our CI configuration files and scripts (example scopes: Travis, Circle, BrowserStack, SauceLabs)
// docs: Documentation only changes
// feat: A new feature
// fix: A bug fix
// perf: A code change that improves performance
// refactor: A code change that neither fixes a bug nor adds a feature
// style: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)
// test: Adding missing tests or correcting existing tests

module.exports = {
  extends: ['@commitlint/config-conventional'],
  rules: {
    'body-leading-blank': [1, 'always'],
    'body-max-line-length': [2, 'always', 100],
    'footer-leading-blank': [1, 'always'],
    'footer-max-line-length': [2, 'always', 100],
    'header-max-length': [2, 'always', 100],
    'scope-case': [2, 'always', 'lower-case'],
    'subject-case': [
      2,
      'never',
      ['sentence-case', 'start-case', 'pascal-case', 'upper-case'],
    ],
    'subject-empty': [2, 'never'],
    'subject-full-stop': [2, 'never', '.'],
    'type-case': [2, 'always', 'lower-case'],
    'type-empty': [2, 'never'],
    'type-enum': [
      2,
      'always',
      [
        'build',
        'chore',
        'ci',
        'docs',
        'feat',
        'fix',
        'perf',
        'refactor',
        'revert',
        'style',
        'test',
        'translation',
        'security',
        'changeset',
      ],
    ],
  },
};

```

