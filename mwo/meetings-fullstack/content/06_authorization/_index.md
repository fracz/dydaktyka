---
title: "Autoryzacja"
date: 2023-04-20T12:31:01+02:00
weight: 6
---

1. Po zalogowaniu przejmij token i skonfiguruj `axios` tak, by przy każdym następnym
   requeście wysyłał nagłówek `Authorization` z wartością `Bearer TOKEN`. W ten sposób
   aplikacja będzie przedstawiać się za pomocą wystawionego tokenu w kolejnych żądaniach.
   [Dokumentacja](https://axios-http.com/docs/config_defaults)
   ```js
   const token = response.data.token;
   axios.defaults.headers.common['Authorization'] = 'Bearer ' + token;
   ```
1. Po powyższej zmianie sprawdź, czy od razu po zalogowaniu możesz pobrać listę spotkań:
   ```js
   axios.get('meetings').then(response => console.log(response.data));
   ```
   Podglądnij w narzędziach developerskich żądania, odpowiedzi i ich nagłówki,
   które zostały wymienione.
1. Przy wylogowaniu się wyczyść zapamiętany token.
   ```js
   delete axios.defaults.headers.common.Authorization;
   ```
1. Wykorzystaj [`localStorage`](https://developer.mozilla.org/pl/docs/Web/API/Window/localStorage)
   by zapamiętać token i login zalogowanego użytkownika pomiędzy odświeżeniami strony.
   Do przywrócenia stanu przyda Ci się zdarzenie [`mounted`](https://v2.vuejs.org/v2/api/#mounted)
   komponentu.

