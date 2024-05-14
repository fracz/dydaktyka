---
title: "Rejestracja użytkowników"
date: 2023-04-20T12:31:01+02:00
weight: 40
---

Twoja aplikacja (frontend) nie pozwala na tworzenie kont użytkowników.

Dodaj taką funkcjonalność.

{{% notice style="info" title="Uruchom serwer frontendu" icon="wrench" %}}
Pamiętaj o uruchomieniu dev-servera przy pisaniu frontendu -
komenda `npm start` wykonana w katalogu `src/main/frontend`.
{{% /notice %}}

1. Znajdź komponent, który reaguje na dodanie nowego spotkania.
1. Zanim dodasz spotkanie do listy, wyślij odpowiednie żądanie na backend. Pokaż użytkownikowi,
   że spotkanie się dodało dopiero gdy backend potwierdzi wykonanie operacji.
   ```js
   register(user) {
     axios.post('/api/participants', user)
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
