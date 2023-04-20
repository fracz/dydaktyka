---
title: "Rejestracja użytkowników"
date: 2023-04-20T12:31:01+02:00
weight: 40
---

Twoja aplikacja (frontend) nie pozwala na tworzenie kont użytkowników.

Dodaj taką funkcjonalność.

{{% notice style="info" title="Uruchom serwer frontendu" icon="wrench" %}}
Pamiętaj o uruchomieniu dev-servera przy pisaniu frontendu -
komenda `npm run serve` wykonana w katalogu `src/main/frontend`.
{{% /notice %}}

1. Stwórz komponent pozwalający na rejestrację użytkownika.
1. Na stronie głównej aplikacji dodaj przycisk "zarejestruj", który pokaże formularz rejestracji.
1. Dodaj do projektu bibliotekę [`axios`](https://github.com/axios/axios).
   Dostarcza ona wygodną obsługę asynchronicznych żądań HTTP.
1. Do obsługi rejestracji użytkownika po wysłaniu formularza możesz użyć poniższego kodu:
   ```js
   register(user) {
     axios.post('participants', user)
         .then(response => {
             // udało się
         })
         .catch(response => {
             // nie udało sie     
         });
   }
   ```
1. Sprawdź działanie aplikacji. Podglądnij asynchroniczne żądania w karcie *Network* w narzędziach
   deweloperskich.
   ![](devtools.png?ligtbox=false)
2. Co się dzieje, gdy spróbujesz dodać dwa razy użytkownika z taką samą nazwą? Powiadom użytkownika w GUI
   o tym problemie.
