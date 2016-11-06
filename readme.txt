https://github.com/kentcdodds/starwars-names

How to Write an Open Source JavaScript Library

#1 Introduction to How to Write an Open Source JavaScript Library
#2 Setting up GitHub

#3 Configuring npm and creating a package.json
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

#4 Creating the library and adding dependencies
npm install --save unique-random-array
(npm i -S)
node
    var lib = require('./src/index.js')
    lib.all
    lib.random()

#5 Publishing to GitHub
git status
.gitignore
git add -A
git status
git commit -m 'Adding a library'
git status
git push

#6 Publishing to npm
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

#7 Releasing a version to GitHub
git tag 1.0.0
git push --tags

https://github.com/Suteki/starwars-names/tree/1.0.0
Draft a new release (https://github.com/Suteki/starwars-names/releases/new)
add tag 1.0.0
Super Awesome Initial Release
This is the first one! (ctrl+cmd+space to insert emoji)
publish

#8 Releasing a new version to npm
version:
    major - major release - breaking changes of some kind (breaking change - API)
    minor - minor release - new features, but not breaking API changes
    patch release - bugfix

git status
git diff
git add -A
git status
git commit -m 'Updating starwars-names. Adding Shmi Sky walker'
git tag 1.1.0
git push
git push --tags
npm publish
npm info starwars-names

#9 Publishing a beta version
"version": "1.4.0-beta.0",

git diff
git add -A
git commit -am 'Adding Kent C. Dodds'
git tag 1.4.0-beta.0
git push
git push --tags
npm publish --tags beta
npm info

cd Desktop/
npm install starwars-names
npm install starwars-names@beta
npm install starwars-names@1.4.0-beta.0
npm info
