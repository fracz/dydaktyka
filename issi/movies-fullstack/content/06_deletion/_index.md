---
title: "Usuwanie filmów"
weight: 60
---

Spróbuj dodać funkcjonalność usuwania filmów na podstawie dotychczasowych informacji.

{{% expand title="Spróbuj napisać **samodzielnie**, zanim klikniesz :-)" %}}

```jsx
async function handleDeleteMovie(movie) {
    const response = await fetch(`/movies/${movie.id}`, {
        method: 'DELETE',
    });
    if (response.ok) {
        const nextMovies = movies.filter(m => m !== movie);
        setMovies(nextMovies);
    }
}
```

{{% /expand %}}

Upewnij się, że da się usunąć film, który przed chwilą został dodany. Jeśli
zidentyfikujesz tutaj jakiś problem, spróbuj go naprawić.

{{% notice style="note" title="Pamiętaj!" icon="exclamation-circle" %}}
Zacommituj zmiany i wyślij je na GitHuba.
{{% /notice %}}
