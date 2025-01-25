---
title: "Dodawanie filmów"
weight: 40
---

Dodaj komunikację aplikacji frontendowej i backendowej przy dodawaniu spotkań.

{{% notice style="info" title="Uruchom serwer frontendu" icon="wrench" %}}
Pamiętaj o uruchomieniu dev-servera przy pisaniu frontendu -
komenda `npm start` wykonana w katalogu `ui`.
{{% /notice %}}

{{% notice style="info" title="Uruchom serwer frontendu" icon="wrench" %}}
Pamiętaj o uruchomieniu backendu -
komenda `uvicorn main:app --reload` wykonana w katalogu `api`.
{{% /notice %}}

1. Znajdź komponent, który reaguje na dodanie nowego filmu.
1. Zanim dodasz film do listy, wyślij odpowiednie żądanie na backend. Pokaż użytkownikowi,
   że film się dodał, dopiero gdy backend potwierdzi wykonanie operacji.
   ```jsx
   async function handleAddMovie(movie) {
     const response = await fetch('/movies', {
       method: 'POST',
       body: JSON.stringify(movie),
       headers: { 'Content-Type': 'application/json' }
     });
     if (response.ok) {
       setMovies([...movies, movie]);
       setAddingMovie(false);
     }
   }
   ```
   O tym kodzie porozmawiamy sporo na zajęciach :-)
1. Sprawdź działanie aplikacji. Podglądnij asynchroniczne żądania w karcie *Network* w narzędziach
   deweloperskich.
2. Sprawdź, czy film rzeczywiście się dodaje - zobacz w przeglądarce odpowiedź z endpointa
   `/movies`. Powinna ona być dostępna lokalnie pod adresem
   [localhost:8000/movies](http://localhost:8000/movies).

{{% notice style="note" title="Pamiętaj!" icon="exclamation-circle" %}}
Zacommituj zmiany i wyślij je na GitHuba.
{{% /notice %}}
