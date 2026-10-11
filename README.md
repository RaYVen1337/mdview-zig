# mdview-win

Windows-only Fork von [nathannncurtis/mdview-zig](https://github.com/nathannncurtis/mdview-zig) — schneller, nativer Markdown-Viewer in Zig. Kleine portable `.exe` (~290 KB), keine Laufzeit-Abhängigkeiten (DirectWrite/Direct2D aus dem System).

## Änderungen gegenüber Upstream

- **GFM-Tabellen**: echtes Grid statt Pipe-Fließtext — fetter Header mit Hintergrund, Zebra-Zeilen, Gitterlinien, Spaltenbreiten per DirectWrite-Messung, Textumbruch bei Überbreite.
- **Normales Fenster**: Standard-Titelleiste mit Minimieren/Maximieren/Schließen, Ziehen an der Leiste (Alt+Ziehen von überall geht weiterhin). Fixt außerdem den Bug, dass bloßes Hovern über das gemalte X das Fenster sofort schloss (`PostQuitMessage` in `WM_NCHITTEST`).
- **Dateiname im Fenstertitel** (`mdview - foo.md`), aktualisiert sich auch bei Drag & Drop.
- **Pos1/Ende**: springt nach ganz oben/unten.
- **Nur Windows**: Linux-Backend (X11/Cairo/Pango) und macOS-Backend (Cocoa/CoreText) entfernt — weniger Code, ein Ziel.

## Install

Aus dem [neuesten Release](https://github.com/RaYVen1337/mdview-zig/releases/latest) `mdview.exe` laden, z. B. nach `%USERPROFILE%\.local\bin` (liegt im `PATH`), dann als Standard-Viewer registrieren:

```
mdview --register
```

## Benutzung

```
mdview README.md
```

Oder eine `.md`-Datei aufs Fenster ziehen. Das Fenster lädt neu, wenn sich die Datei ändert, und merkt sich die Scrollposition.

## Tasten

| Taste     | Aktion              |
| --------- | ------------------- |
| Strg+Q    | Beenden             |
| Pos1/Ende | Nach oben/unten     |
| Alt+Ziehen| Fenster verschieben |
| Scrollen  | Scrollen            |

## Aus dem Quellcode bauen

[Zig 0.14.1](https://ziglang.org/download/0.14.1/zig-x86_64-windows-0.14.1.zip) genügt, keine weiteren Abhängigkeiten:

```
zig build -Doptimize=ReleaseSmall
```

Die `.exe` liegt danach in `zig-out/bin/`.

## Lizenz

[GPL-3.0](LICENSE), wie Upstream. Dank an [nathannncurtis](https://github.com/nathannncurtis) für das Original.
