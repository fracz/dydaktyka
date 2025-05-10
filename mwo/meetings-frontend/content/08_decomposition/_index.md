---
title: Dekompozycja aplikacji na komponenty
linkTitle: Dekompozycja
weight: 80
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

## Wydzielamy komponent z formularzem logowania

Komponent nazwiemy `LoginForm`. Jego odpowiedzialnością będzie zebranie danych
od użytkownika (adresu mailowego), a następnie przekazanie go do komponentu nadrzędnego,
gdy użytkownik zatwierdzi logowanie (kliknie przycisk).

Komponent dziecko może przyjąć od rodzica parametry, które z jednej strony mogą
doprecyzować jak komponent ma się renderować, a z drugiej - umożliwić na komunikację od dziecka do rodzica.

W React parametry komponentu nazywami _propertiesami_ lub _propsami_.

Komponent dziecko przyjmuje _propsy_ jako argument funkcji, która go definiuje.
Rodzic podaje wartości _propsów_ jako atrybuty HTMLowe przy tworzeniu instancji komponentu.

1. Stwórz nowy plik `src/LoginForm.js`.
   ```jsx
   export default function LoginForm(props) {
        const [email, setEmail] = useState('');
    
        return <div>
            <label>Zaloguj się e-mailem</label>
            <input type="text" value={email} onChange={(e) => setEmail(e.target.value)}/>
            <button type="button" onClick={() => props.onLogin(email)}>
                Wchodzę
            </button>
        </div>;
   }
   ```
   Zwróć uwagę, że komponent w wyniku kliknięcia przycisku woła funkcję `props.onLogin`.
   Komponent oczekuje, że zostanie ona przekazana od rodzica. Uzywamy też skróconego zapisu
   `export default function`.

1. Przejdź do `src/App.js` i zaimportuj stworzony przez siebie komponent.
   ```js
   import LoginForm from "./LoginForm";
   ```
1. Użyj komponentu w odpowiednim miejscu.
   ```html
   <LoginForm onLogin={login}/>
   ```

Zauważ, że komponent `App.js` nie musi już wiedzieć o tym, co jest wpisane w polu
formularza logowania. Interesuje go tylko to, kto jest "zalogowany". W ten sposób
ściągnęliśmy z głównego komponentu jedną odpowiedzialność.

## Wydziel komponent ze stanem aplikacji po zalogowaniu

Analogicznie do poprzednich działań, wydziel komponent zawierający informację o
aktualnie zalogowanym użytkowniku i który potrafi do komponentu `App` zgłosić
chęć wylogowania się.

Stworzenie obydwu komponentów powinno umożliwić znaczne uproszczenie szablonu
JSX w komponencie `App` za pomocą operatora _ternary_:

```jsx
return (
        <div>
           <h1>System do zapisów na zajęcia</h1>
           {
              loggedIn
                      ? <UserPanel username={loggedIn} onLogout={logout}/>
                      : <LoginForm onLogin={login}/>
           }
        </div>
);
```

{{% notice style="note" title="Pamiętaj!" icon="exclamation-circle" %}}
Zacommituj zmiany i wyślij je na GitHuba.
{{% /notice %}}
