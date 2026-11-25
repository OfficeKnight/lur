# lur

Passwortgeschützter Entwurf einer Webseite (Deutsch, Russisch, Ukrainisch).

- `index.html` ist die mit [StatiCrypt](https://github.com/robinmoisson/staticrypt) verschlüsselte Seite (AES-256). Ohne Passwort ist der Inhalt nicht lesbar.
- `quelle.tar.gz.gpg` enthält den unverschlüsselten Quelltext samt Build-Skripten, symmetrisch mit GnuPG (AES-256) und demselben Passwort verschlüsselt.
- `robots.txt` und ein `noindex` halten Suchmaschinen fern.

## Quelle entpacken und neu bauen

```
gpg -d quelle.tar.gz.gpg | tar -xz
cd quelle
STATICRYPT_PASSWORD='…' ./verschluesseln.sh
cp dist/index.html ../index.html
```

Wichtig: Unverschlüsselte Dateien aus `quelle/` nie in dieses öffentliche Repository committen. Der Ordner steht deshalb in `.gitignore`.
