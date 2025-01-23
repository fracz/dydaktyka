---
title: "Zmiany w aplikacjach"
date: 2023-04-20T09:19:49+02:00
weight: 20
---

Na poprzednich zajęciach stworzyliśmy dwie aplikacje - backendową, która udostępnia REST API
oraz frontendową, która udaje, że z niego korzysta.

Na początek zajęć udostępniam projekt, który połączył te dwa światy w jeden.
Aplikacja w Fast API znalazla się w katalogu `api`.
Kod frontendu natomiast został umieszczony w katalogu `ui`.

Oto lista zmian w stosunku do stanu aplikacji z poprzednich zajęć:

1. W pliku `ui/package.json` dodałem konfigurację
   [proxy dla dev-servera](https://create-react-app.dev/docs/proxying-api-requests-in-development/).
   aby komunikacja frontendu i backendu działała w trybie deweloperskim.
1. Gdy aplikacja będzie zdeployowana (frontend będzie zbudowany), Fast API zajmie się
   serwowaniem aplikacji frontendowej za pomocą konfiguracji:
   ```py
   app.mount("/static", StaticFiles(directory="../ui/build/static", check_dir=False), name="static")
   ```
1. Ponado, na stronie głównej zostanie wyrenderowany plik `index.html`, który uruchomi
   Reactową aplikację.
   ```py
   @app.get("/")
   def serve_react_app():
      return FileResponse("../ui/build/index.html")
   ```

Jeśli chcesz użyć kodu swoich dotychczasowych aplikacji (np. w domu) wykonaj
powyższe kroki i powinno działać.
