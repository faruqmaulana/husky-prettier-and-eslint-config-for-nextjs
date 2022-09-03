## Husky, Prettier and Eslint for your nextjs project setup

#### I usually use husky, prettier and eslint for my project setup, but I often have problems when I setup my nextjs project. So I decided to make cheetsheat configuration and you can use it for personal or commercial usage. Thank you hopefully it will help save your time in project setup and increase your productivity. happy coding ✨✨<img src="https://media.giphy.com/media/WUlplcMpOCEmTGBtBW/giphy.gif" width="30"> 



```bash
yarn add husky -D -W
yarn add prettier -D -W
yarn add eslint -D -W
yarn add eslint-config-next -D -W
md .husky
npx husky add .husky/pre-commit "yarn format"
npx husky add .husky/pre-commit "yarn lint"
npx husky add .husky/pre-push "yarn build"
npm set-script prepare "husky install"
npm set-script format "prettier --write ."
npm set-script lint "eslint . --fix"
yarn prepare
yarn add -D -W @commitlint/{config-conventional,cli}
echo "module.exports = {extends: ['@commitlint/config-conventional']}" > commitlint.config.js
yarn husky install
npx husky add .husky/commit-msg 'npx --no-install commitlint --edit "$1"'
```
