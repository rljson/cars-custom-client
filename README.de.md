<!--
@license
Copyright (c) rljson

Use of this source code is governed by terms that can be
found in the LICENSE file in the root of this package.
-->

# @rljson/cars-custom-client

[English](README.md) | Deutsch

[![CI](https://github.com/rljson/cars-custom-client/actions/workflows/quick_check.yaml/badge.svg)](https://github.com/rljson/cars-custom-client/actions/workflows/quick_check.yaml)

Client-Website der Seite custom der cars-Beispiel-App, wo freigegebene Kataloge für Kunden weiterbearbeitet werden.

## Motivation

- Die Seite custom der cars-Beispiel-App hat eine eigene Client-Website,
  wo freigegebene Kataloge für Kunden weiterbearbeitet werden
- Eine statische Seite, ausgeliefert von nginx; sie zeigt ihre eigene
  Hello-Zeile und die Zeilen, die der Master ihrer Seite auf `/api/hello`
  antwortet; nginx leitet dorthin an `MASTER_URL` weiter
- `GET /health` antwortet `ok`; sie läuft als Container App
  `ca-cars-custom-client-<stage>` in den Stufen `dev`, `test` und `prod`

## Installation

Das Package ist privat und nicht auf npm veröffentlicht. Hänge von einer
getaggten Version seines Git-Repos ab:

```bash
pnpm add git+ssh://git@github.com/rljson/cars-custom-client.git#semver:^0.0.1
```

## Verwendung

Die Hello-Zeilen in einem Element zeigen:

```ts
import { showHello } from '@rljson/cars-custom-client';

await showHello(document.getElementById('hello')!, (url) => fetch(url));
```

Die Seite zeigt `Hello from cars-custom-client` und die Zeilen des Masters.

### Container

Das Image in der Registry der Stufe `dev` bauen:

```bash
az acr build --registry crcarsdev --image cars-custom-client:<version>-<sha> .
```

## Grenzen

- Noch keine Synchronisierung und keine Electron-App, nur das Hello World

## Dokumentation

- Die Guides in [doc/guides](doc/guides)

## Stand

Vor 1.0 — die API kann sich zwischen Minor-Versionen ändern.

## Mitwirken

Siehe [doc/guides/develop-guide.md](doc/guides/develop-guide.md).

## Lizenz

MIT — siehe [LICENSE](LICENSE).
