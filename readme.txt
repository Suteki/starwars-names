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

#10 Setting up Unit Testing with Mocha and Chai
npm install mocha chai --save-dev
npm i -D mocha chai

create 1 test only just to cheak that test libraries work as we expect
"test": "mocha src/index.test.js -w" - add tests runner with watcher

#11 Unit Testing with Mocha and Chai
npm t
(short for run tests)
expect(starWars.all).to.satisfy(isArrayOfStrings);
expect(starWars.all).to.not.satisfy(isArrayOfStrings);
expect(starWars.all).to.include('Luke Skywalker');

#12 Automating Release with semantic-release

WARNING FIRSTLY Register https://travis-ci.org/
or https://circleci.com/ (instead of Travis CI)

npm install -g semantic-release-cli
semantic-release-cli setup
N
Travis CI (or snap, or code cheap)
single node version

change version to (add)
  "version": "0.0.0-semantically-released",

travis add:
    script:
        - npm run test

#13 Writing conventional commits with commitizen
http://github.com/angular/angular.js/blob/master/CONTRIBUTING.md#commit

npm install -D commitizen cz-conventional-changelog

  "scripts": {
    "commit": "git-cz",

instead of (will be deprecated in v3):

  "czConfig": {
    "path": "node_modules/cz-conventional-changelog"
  },

write:

  "config": {
    "commitizen": {
      "path": "node_modules/cz-conventional-changelog"
    }
  }

git status
git add package.json
git status
npm run commit

chore
releasing
Add travis config, conventional commit, and semantic-release

closes #1 (create issue before closing - Simplify releases - With semantic-release and commitizen)
git log

#14 Commiting a new feature with commitizen
create issue
    Get specified number of starwars names
    Would be super to get an array back if I call: starWarsNames.random(3)

git status
git add .
npm run commit

feat
random
Add ability to get an array of starwars names
If you pass a number to the random function, you will receive an array with that number of random items
closes #2

we could make (closes #2 BREAKING CHANGE) to notify that commit has new change

#15 Automatically Releasing with TravisCI

"test:single": "mocha src/index.test.js",

script:
  - npm run test:single

git status
git add .

npm run commit
chore
build
Add test:single for travis
We don't want travis to watch the tests

git push

#16 Automatically running tests before commits with ghooks
npm i -D ghooks

  "config": {
    "ghooks": {
      "pre-commit": "npm run test:single"
    }
  }

chore
ghooks
Add ghooks
Protect ourselves from commiting code that breaks the tests

git push

#17 Adding code coverage recording with Istanbul
npm install -D istanbul

"test:single": "istanbul cover -x */*.test.js _mocha -- -R spec src/index.test.js",

npm run test:single
