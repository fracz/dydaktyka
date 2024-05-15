---
title: "React - struktura aplikacji"
linkTitle: Struktura aplikacji
date: 2023-04-20T09:19:49+02:00
weight: 30
---

## Struktura aplikacji

* `package.json`
  * zawiera definicje zależności do bibliotek potrzebnych
    do działania aplikacji (`dependencies`)
  * zawiera skrypty, m.in. pozwalające na uruchomienie i rozwój aplikacji (`start`) oraz skrypt przygotowujący
    nasz kod do wydania (`build`).
  * zawiera nazwę, wersję projektu
  * można powiedzieć, że `package.json` dla NPM jest tym co `pom.xml` dla Mavena
* `src/App.js` zawiera kod wygenerowanego komponentu React, który reprezentuje stronę
  wejściową do tworzonej aplikacji.
* `src/index.css` zawiera definicję stylów globalnych, a `src/App.css` - sytlów dla komponentu `App`
* `src/index.js` zawiera kod uruchamiany przy starcie aplikacji; zauważ, że importowany jest
  tu framework React. Zaimportowany
  jest również wygenerowany komponent strony głównej `App`. Kod który widzisz mówi, że
  w elemencie `#root` przy starcie aplikacji ma być wyrenderowany komponent `App`.
* `public/index.html` zawiera główny szablon strony. Zauważ, że nie ma tu nic więcej oprócz
  standardowego szablonu strony HTML, elementu do którego odwołuje się kod w `index.js` -
  `<div id="root"></div>` i informacji o tym, że zbudowana aplikacja zostanie do niego dołączona.
