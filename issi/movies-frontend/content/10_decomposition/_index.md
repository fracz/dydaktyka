---
title: Dekompozycja aplikacji na komponenty
linkTitle: Dekompozycja
weight: 100
---

Powiedzieliśmy na początku, że aplikacja frontendowa składa się z komponentów, tymczasem
obecnie mamy tylko jeden komponent z całą logiką `src/App.js`. Najwyższy czas to zmienić.

Naszym najwyższym komponentem jest i zostanie `App.js` i wszystkie komponenty, które
pojawią się wewnątrz niego - będą "pod" nim. Przypominam obrazek:

![](intro-components.png)

Pierwszy blok od góry to `App.js`. Pod nim będą teraz komponenty, które będziemy tworzyć.

Mówimy, że komponent, który pojawia się pierwszy w hierarchii, jest komponentem nadrzędnym
lub komponentem rodzicem. Te, które są pod nim to komponenty podrzędne lub
komponenty-dzieci.

## Wydziel komponent z formularzem dodawania filmu

Komponent nazwiemy `MovieForm`. Jego odpowiedzialnością będzie zebranie danych
od użytkownika (tytułu, roku nagrania), a następnie przekazanie ich do komponentu nadrzędnego,
gdy użytkownik zatwierdzi formularz (kliknie przycisk).

Komponent dziecko może przyjąć od rodzica parametry, które z jednej strony mogą
doprecyzować jak komponent ma się renderować, a z drugiej - umożliwić na komunikację od dziecka do rodzica.

W React parametry komponentu nazywami _propertiesami_ lub _propsami_.

Komponent dziecko przyjmuje _propsy_ jako argument funkcji, która go definiuje.
Rodzic podaje wartości _propsów_ jako atrybuty HTMLowe przy tworzeniu instancji komponentu.

1. Stwórz nowy plik `src/MovieForm.js`.
   ```jsx
   import {useState} from "react";
   
   export default function MovieForm(props) {
       const [title, setTitle] = useState('');
       const [year, setYear] = useState('');
   
       function addMovie(event) {
           event.preventDefault();
           if (title.length < 5) {
               return alert('Tytuł jest za krótki');
           }
           props.onMovieSubmit({title, year});
           setTitle('');
           setYear('');
       }
   
       return <form onSubmit={addMovie}>
           <h2>Add movie</h2>
           <div>
               <label>Tytuł</label>
               <input type="text" value={title} onChange={(event) => setTitle(event.target.value)}/>
           </div>
           <div>
               <label>Rok nagrania</label>
               <input type="text" value={year} onChange={(event) => setYear(event.target.value)}/>
           </div>
           <button>Add a movie</button>
       </form>;
   }
   ```
   Zwróć uwagę, że komponent w wyniku kliknięcia przycisku woła funkcję `props.onMovieSubmit`.
   Komponent oczekuje, że zostanie ona przekazana od rodzica. Używamy też skróconego zapisu
   `export default function`.

1. Przejdź do `src/App.js` i zaimportuj stworzony przez siebie komponent.
   ```js
   import MovieForm from "./MovieForm";
   ```
1. Użyj komponentu w odpowiednim miejscu.
   ```html
   <MovieForm onMovieSubmit={(movie) => setMovies([...movies, movie])}/>
   ```

Zauważ, że komponent `App.js` nie musi już wiedzieć o tym, co jest wpisane w polu
formularza logowania. Interesuje go tylko to, jakie finalnie dane wpisał użytkownik. W ten sposób
ściągnęliśmy z głównego komponentu jedną odpowiedzialność.

## Wydziel komponent wyświetlający listę filmów i pojedynczy film

Analogicznie do poprzednich działań, wydziel komponent zawierający renderujący
listę filmów do wyświetlenia. Wewnątrz niego, każdy film także powinien być wyświetlany
przez swój komponent. Dzięki temu poprawnie rozłożymy odpowiedzialności w aplikacji.

```jsx
function App() {
   const [movies, setMovies] = useState([]);

   return (
        <div>
           <h1>My favourite movies to watch</h1>
           <MoviesList movies={movies}/>
           <MovieForm onMovieSubmit={(movie) => setMovies([...movies, movie])}/>
        </div>
   );
}
```

{{% notice style="note" title="Pamiętaj!" icon="exclamation-circle" %}}
Zacommituj zmiany i wyślij je na GitHuba.
{{% /notice %}}
