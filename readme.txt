https://github.com/kentcdodds/starwars-names

#3
http://nodejs.org
npm --version
http://docs.npmjs.com -> config

npm set init-author-name 'Sergey Borachuk'
npm set init-author-email 'sergeyborachuk@gmail.com'
npm set init-author-url ''
npm set init-license 'MIT'
cat ~/.npmrc
npm set save-exact true

http://www.npmjs.com -> (sigh in / sign up account)
npm adduser
user:
pass:
email:
(token will be created)

npm init
name:
version:
description: Get random Star Wars names
// entry point: require('starwars-names');
entry point: src/index.js
test command:
git-repository:
keywords: random star wars
licence:

#4
npm install --save unique-random-array
(npm i -S)
node
    var lib = require('./src/index.js')
    lib.all
    lib.random()

#5
git status
.gitignore
git add -A
git status
git commit -m 'Adding a library'
git status
git push

#6
npm publish
npm info starwars-names
cd Desktop/
npm install starwars-names

vim index.js
var starWarsNames = require('starwars-names');
console.log(starWarsNames.all);
console.log(starWarsNames.random());
console.log(starWarsNames.random());
console.log(starWarsNames.random());
console.log(starWarsNames.random());
console.log(starWarsNames.random());

node index.js
node index.js

http://npm.im/starwars-names


