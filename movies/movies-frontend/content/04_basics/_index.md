---
title: "React - komponenty"
linkTitle: Komponenty / JSX
weight: 40
---

W pliku `App.js` wyczyść treść wygenerowanego komponentu, tak byśmy
zaczynali "od zera".

```jsx
function App() {
    return (
        <div>
            <h1>System do zapisów na zajęcia</h1>
        </div>
    );
}

export default App;
```

Nie omówiliśmy modułów w JS (odsyłam: [Modules](https://javascript.info/modules-intro)),
ale potraktuj `export default App` na końcu pliku jako "udostępnij z tego pliku następującą implementację komponentu".

## Zmienne w JSX

Jeśli wewnątrz definicji bloku JSX chcesz "uciec" z powrotem do języka JS -
musisz użyć klamerek `{}`. Dzięki nim możesz w dowolne miejsce wstawić wartość
zmiennej z komponentu.

```jsx
function App() {
    let email = 'fracz@agh.edu.pl';

    return (
        <div>
            <h1>System do zapisów na zajęcia</h1>
            <h2>Twój e-mail to {email}</h2>
        </div>
    );
}
```

## Obsługa zdarzeń

Jeśli chcemy od użytkownika zebrać jakieś informacje - potrzebujemy formularza
oraz możliwości reagowania na zdarzenia generowane przez użytkownika. Dodaj
do komponentu pole tekstowe i wypisz na konsolę jego wartość przy każdej zmianie.

```jsx
function App() {
    let email = 'fracz@agh.edu.pl';

    function handleChange(event) {
        console.log(event.target.value);
    }

    return (
        <div>
            <h1>System do zapisów na zajęcia</h1>
            <h2>Twój e-mail to {email}.</h2>
            <input type="text" onChange={handleChange}/>
        </div>
    );
}
```

Zwróć uwagę, w jaki sposób zdefiniowaliśmy funkcję wewnątrz komponentu
oraz jak wywołujemy ją w reakcji na zdarzenie generowane z pola tekstowego.

{{% notice style="note" title="Pamiętaj!" icon="exclamation-circle" %}}
Zacommituj zmiany i wyślij je na GitHuba.
{{% /notice %}}
