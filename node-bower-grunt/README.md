# node-bower-grunt Docker development environment

## Features
* `node`
* `npm`
* `grunt`
* `bower`

## Usage
Derive your Dockerfile from this image and on build we'll
1. Copy `package.json`, `bower.json` to `/usr/src/app`.
2. If `bowerrc.json` exists, we'll copy it to /root/.bowerrc, and modify
   it to allow root to use bower.
3. Copy all contents of your build folder to /usr/src/app.
4. Remove `node_modules` and `bower_components` from `/usr/src/app` if
   you have been developing locally.
5. Run `npm install`, `bower install` and finally, `grunt build`.
