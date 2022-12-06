# SASS-Projekt

### Von vorne anfangen

## initialisiere npm in deinem Projekt

```bash
npm init -y
```

## install some Dev-Dependencies

```bash
npm i --save-dev gh-pages sass npm-run-all live-server
```

## add some scripts to your `package.json`

```bash
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

Note:
`run-p` : ein CLI-Befehl, um bestimmte npm-Skripte parallel auszuführen.
`run-s` : ein CLI-Befehl zum sequenziellen Ausführen bestimmter npm-Skripte.
`rsync` : ist ein Dienstprogramm zum effizienten Übertragen und Synchronisieren von Dateien zwischen einem Computer und einem Speicherlaufwerk und über vernetzte Computer hinweg, indem die Änderungszeiten und -größen von Dateien verglichen werden.

## Projektstruktur

Jedes Projekt, das mit diesem Boilerplate erstellt wird, folgt der folgenden Struktur:

```
Project
│   README.md
│   .gitignore
│   package.json
|   package-lock.json
└───src
│   │   index.html
│   └───styles
|   └───scss
|   |   |  _var.scss
|   |   |  _header.scss
|   |   └───main.scss
│   └───scripts
│   |   └───index.js
|   └───img
|   └───fonts
└───dist
```

### `README.md`

Die README sollte eine kurze Beschreibung des Projekts enthalten, du kannst diese Anleitung gerne löschen oder umbenennen, um eine eigene Beschreibung hinzuzufügen.

### `.gitignore`

Diese Datei hilft beim Aufheben der Verfolgung (Dateien, Verzeichnisse). Du kannst dies tun, indem du einfach die Datei/Ordner in die Textdatei `.gitignore` einfügst.

### `package.json` & `package-lock.json`

Diese Dateien enthalten verschiedene Informationen über dein Projekt und die Projektabhängigkeiten sowie nützliche Skripte, die du beim Entwicklungsprozess verwendest. Bitte bearbeite diese Dateien vorerst nicht, außer wenn du dazu aufgefordert wirst. In Zukunft erfährst du mehr über Projektabhängigkeiten.

### `src` & `index.html`

Der Ordner `src` enthält alle Dateien, die du deiner Website hinzufügen möchtest, bevor sie verarbeitet werden. **Dies ist der Hauptordner, in dem du arbeiten würdest**.

`index.html` ist die Hauptseite für deine Website, an der du arbeiten wirst. Fühl dich frei, neue `html`-Seiten, die du erstellst, direkt im `src`-Ordner hinzuzufügen.

### `scss` & `main.scss`

Der Ordner `scss` enthält alle `scss`. Um zusätzliche Stile in deinem Projekt einzubinden, musst du diese in `main.scss` importieren.

`main.scss` ist dein Stil _**Einstiegspunkt**_. Jedes andere `scss`, das in diese Datei importiert wird, kann verwendet werden, und alle Stile, die direkt in diese Datei geschrieben werden, werden angewendet.

### `scripts` & `index.js`

Der Ordner `scripts` enthält alle `js` Dateien, die du deiner Website hinzufügst. `index.js` ist die _**Haupt**_-Skriptdatei dein Projekts. Fühl dich frei, diese Datei zu verwenden, um JavaScript hinzuzufügen, mit dem du experimentieren möchtest. Mehr zu JavaScript im Browser erfährst du schon bald 😉.

### `images` and `fonts`

Aus Gründen der Organisation und guten Projektstrukturpraktiken verwendest du bitte diese Ordner, um deine Bilder bzw. Schriftarten aufzubewahren.

### `dist`

Der Ordner `dist` wird automatisch generiert, wenn du das Build-Skript ausführen:

```bash
npm run build
```

Dieser Ordner enthält das erstellte Projekt, das online bereitgestellt werden kann. Es ist vom `git` Tracking ausgeschlossen, da es nicht üblich ist, kompilierten Code in ein Entwicklungsprojekt einzubinden.
