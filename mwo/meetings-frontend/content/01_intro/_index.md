---
title: "React - wprowadzenie"
menuTitle: Wprowadzenie
date: 2023-04-20T09:19:49+02:00
weight: 1
---

## React - wprowadzenie

Aplikacja w React zbudowana jest z komponentów podobnie jak system obiektowy
składa się z obiektów. Każdy komponent powinien realizować jedną odpowiedzialność
(Single Responsibility Principle). Komponenty definiuje się jako funkcje
w plikach `.js` z wykorzystaniem składni `JSX`, która pozwala w prosty sposób
na opisanie jaka struktura HTML powinna być wyrenderowana przy użyciu
komponentu.

### Przykładowy komponent React

```jsx
function MyComponent() {
    const greeting = "world";
    return <p className="mail">Hello {greeting}!</p>;
}
```

Na podstawie powyższego przykładu możesz zauważyć, że zadaniem komponentu
jest wyrenderowanie fragmentu funkcjonalności / widoku aplikacji.

W jaki sposób używać komponentów? Tak, jakby były nowymi tagami HTML,
tyle że pisanymi wielką literą.

```jsx
function App() {
    return <MyComponent/>;
}
```

W ten sposób można wybudować całą aplikację, wskazując tylko Reactowi
jeden główny komponent, od którego renderowanie ma się rozpocząć.

![Components](intro-components.png?lightbox=false)

