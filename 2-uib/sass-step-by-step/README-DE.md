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
npm start

```

# Nicht Vergessen, dein CSS zu verlinken

`<link rel="stylesheet" href="./styles/main.css" />`

# Wenn du dein Projekt pushen und veröffentlichen möchtest

# Erste

Du solltest dein Dokument zum `main` branch hinzufügen

```
git add . && git commit -m "your commit" && git push origin main
```

# Sekunde

Du musst dein `dist` dir auf `gh-pages` hochladen,
Keine Sorge, gh-pages Befehle kümmern sich darum.

Folge einfach

```
npm run build
npm run deploy
```

`build` : erstellt/aktualisiert dein `dist` dir
`deploy` : Pushe was in `dist` zu deinem `gh-pages` Zweig
ps: Es wird auch einen Link zu Github-Pages für dich erstellen (wenn du es zum ersten Mal ausführen)

Happy coding 🍀
