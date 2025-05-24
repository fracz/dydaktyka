---
title: "Rozwój aplikacji"
weight: 80
---

Kilka pomysłów na rozbudowę naszej aplikacji.
* **Dodaj obsługę błędów** - w przypadku błędnej odpowiedzi serwera poinformuj o tym użytkownika. Może [ta biblioteka](https://fkhadra.github.io/react-toastify/introduction/) Ci się przyda?
* **Dodaj animacje ładowania**, gdy frontend czeka na odpowiedź serwera. Przykłady: [https://loading.io/css/](https://loading.io/css/).
* Pobaw się [**animacjami w React**](https://github.com/pmndrs/react-spring) by ożywić
  interfejs Twojej aplikacji.
* Dodaj do spotkania **datę**.
* Pozwól na **edycję spotkań** (nazwy i opisu).
* **Dodaj autentykację użytkowników.** Jeśli w trakcie laboratorium backendowego udało Ci się zaimplementować wystawianie
  tokenów
  JWT i autoryzację o nie opartą, dlaczego by nie przenieść tego teraz także do aplikacji
  frontendowej? Dodaj formularz zakładania konta i logowania i pokaż listę spotkań
  tylko użytkownikom, którzy zalogują się do aplikacji.
* Zapamiętuj zalogowanego użytkownika
  w [`localStorage`](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage)
  tak, aby odświeżenie strony nie powodowało konieczności ponownego wpisywania nazwy użytkownika
* [Wyślij maila potwierdzającego przy zapisaniu się na spotkanie](http://www.baeldung.com/spring-email).
  Powinien zawierać datę zapisania się, nazwę, opis oraz datę spotkania.
