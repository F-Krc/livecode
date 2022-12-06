## Erster Schritt

```
npm init -y
```

# 2. Schritt

```
npm i sass gh-pages npm-run-all live-server
```

# 3. Schritt

```
mkdir src src/scss
touch src/index.html src/scss/main.scss
```

# 4. Schritt

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

# 5. Schritt

```
echo "node_modules" >> .gitignore
```

# letzter Schritt

starte deinen server und sass watch

```
npm run

```

# Nicht Vergessen, dein CSS zu verlinken

`<link rel="stylesheet" href="./styles/main.css" />`

# Wenn du din Projekt pushen und veröffentlichen möchten

# Erste

you need to add your work to `main` branch

```
git add . && git commit -m "your commit" && git push origin main
```

# Sekunde

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
