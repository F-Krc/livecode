## First step

```
npm init -y
```

# 2nd step

```
npm i sass gh-pages npm-run-all live-server
```

# 3rd step

```
mkdir src src/scss
touch src/index.html src/scss/main.scss
```

# 4th step

in `package.json`

```
"scripts": {
    "start": "run-p watch watch:styles",
    "build": "run-s clean clean:styles build:styles copy",
    "deploy": "run-s build publish",
    "build:styles": "sass src/scss:src/styles",
    "watch": "live-server src",
    "watch:styles": "sass src/scss:src/styles --watch",
    "clean": "rm -rf dist",
    "clean:styles": "rm -rf src/styles",
    "copy": "mkdir dist && rsync -avr --exclude=\"/scss\" src/ dist",
    "publish": "gh-pages -d dist"
  },
```

# 5th step

```
echo "node_modules" >> .gitignore
```

# last step

start your server and sass watch

```
npm run

```

# don't forget to link your css

`<link rel="stylesheet" href="./styles/main.css" />`

# if you want to push & publish your project

# first

you need to add your work to `main` branch

```
git add . && git commit -m "your commit" && git push origin main
```

# secund

you need to upload your `dist` dir to `gh-pages`,
Don't worry gh-pages commands will take care of that.

to do so just follow

```
npm run build
npm run deploy
```

`build` : creates/update your `dist`dir
`deploy` : push what in `dist` to your `gh-pages` branch
ps: It will also create github pages link for you (on the first time your run it)

Happy coding 🍀
