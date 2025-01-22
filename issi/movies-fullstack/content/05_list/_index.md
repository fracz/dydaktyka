---
title: "Pobieranie spotkań"
weight: 50
---

Po dodaniu spotkań są one publikowane w endpoincie `/api/meetings`. Skorzystajmy z niego,
aby wyświetlić użytkownikowi listę istniejących spotkań po wejściu do aplikacji.

W tym celu przy pierwszym wyrenderowaniu komponentu konieczne jest skomunikowanie się z API
i ustalenie stanu komponentu na podstawie uzyskanej odpowiedzi. W tym celu skorzystamy
z nieznanego nam jeszcze hooka - [`useEffect`](https://react.dev/reference/react/useEffect).
Jak dowiesz się z dokumentacji, hook ten pozwala na synchronizację stanu komponentu
z zewnętrznym systemem.

Hook przyjmuje funkcję, która zostanie wykonana podczas pierwszego renderowania
komponentu (_setup code_). Drugi argument funkcji to tablica stanów, których zmiana
powinna spowodować ponowne wykonanie tego kodu (np. ponowne pobranie danych). W naszym
przypadku ta tablica jest pusta, ponieważ zawsze chcemy pobrać listę wszystkich spotkań
i chcemy zrobić to tylko raz. `useEffect` nie może także przyjąć funkcji asynchronicznej,
dlatego definiujemy ją wewnątrz zwykłej funkcji strzałkowej.

Całość wygląda tak:

```jsx
useEffect(() => {
    const fetchMeetings = async () => {
        const response = await fetch(`/api/meetings`);
        if (response.ok) {
            const meetings = await response.json();
            setMeetings(meetings);
        }
    };
    fetchMeetings();
}, []);
```

Sprawdź, czy po wejściu w aplikację na liście pojawiają się dodane do bazy danych spotkania.

{{% notice style="info" title="Pamiętaj!" icon="question-circle" %}}
W narzędziach deweloperskich możesz zwrócić uwagę na fakt, że żądanie do
`/api/meetings` jest wykonywane dwukrotnie. Dzieje się tak przez mechanizm
wykrywający potencjalne problemy z komponentami. W trybie deweloperskim
React renderuje komponenty dwukrotnie i upewnia się, że efekt jest taki sam.
Pozwala to wykryć niektóre problemy w trakcie pracy nad aplikacją. Mechanizm ten
nazywa się _double-invoking_ i przeczytasz o nim więcej w
[dokumentacji](https://legacy.reactjs.org/docs/strict-mode.html#detecting-unexpected-side-effects)
{{% /notice %}}

{{% notice style="note" title="Pamiętaj!" icon="exclamation-circle" %}}
Zacommituj zmiany i wyślij je na GitHuba.
{{% /notice %}}
