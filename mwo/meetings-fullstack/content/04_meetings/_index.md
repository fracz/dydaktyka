---
title: "Dodawanie spotkań"
weight: 40
---

Dodaj komunikację aplikacji frontendowej i backendowej przy dodawaniu spotkań.

{{% notice style="info" title="Uruchom serwer frontendu" icon="wrench" %}}
Pamiętaj o uruchomieniu dev-servera przy pisaniu frontendu -
komenda `npm start` wykonana w katalogu `src/main/frontend`.
{{% /notice %}}

1. Znajdź komponent, który reaguje na dodanie nowego spotkania.
1. Zanim dodasz spotkanie do listy, wyślij odpowiednie żądanie na backend. Pokaż użytkownikowi,
   że spotkanie się dodało, dopiero gdy backend potwierdzi wykonanie operacji.
   ```jsx
   async function handleNewMeeting(meeting) {
    const response = await fetch('/api/meetings', {
        method: 'POST',
        body: JSON.stringify(meeting),
        headers: { 'Content-Type': 'application/json' }
    });
    if (response.ok) {
        const nextMeetings = [...meetings, meeting];
        setMeetings(nextMeetings);
        setAddingNewMeeting(false);
    }
   }
   ```
   O tym kodzie porozmawiamy sporo na zajęciach :-)
1. Sprawdź działanie aplikacji. Podglądnij asynchroniczne żądania w karcie *Network* w narzędziach
   deweloperskich.
2. Sprawdź, czy spotkanie rzeczywiście się dodaje - zobacz w przegląðarce odpowiedź z endpointa
   `/api/meetings`.
