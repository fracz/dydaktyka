---
title: "React - uruchomienie aplikacji"
linkTitle: Uruchomienie aplikacji
weight: 20
---

## Uruchomienie aplikacji

1. Wykonaj fork i sklonuj repozytorium [react-lab](https://github.com/fracz/react-lab) **do katalogu `/mnt/workspaces/private`**, jeśli pracjesz na komputerze w sali.

   ```
   cd /mnt/workspaces/private
   git clone ADRES_TWOJEGO_FORKA
   cd react-lab
   npm install --cache ../cache
   ```

   Wejdź do katalogu projektu. Zaimportuj projekt do IDE.

   {{% notice style="info" title="Skąd wziął się ten kod?" icon="question-circle" %}}
   Kod w tym repozytorium jest wygenerowany komendą `npx create-react-app react-lab`. NIE wykonuj jej :)
   {{% /notice %}}

2. Pobierz zależności zdefiniowane w pliku `package.json` za pomocą komendy
   `npm install`. Może to potrwać dłuższą chwilę. To normalne, że na tym etapie
   otrzymujesz informacje o _deprecations_ oraz ostrzeżenia o naruszeniach
   bezpieczeństwa. Witamy w świecie frameworków JS :-)

3. Uruchom aplikację za pomocą komendy `npm start`. Ten tryb nazywamy
   _developer mode_. Uruchomiony serwer na bieżąco będzie obserwować
   pisany przez Ciebie kod i nanosić zmiany do działającej w przeglądarce aplikacji.
   Aplikacja powinna być dostępna pod adresem
   [http://localhost:3000](http://localhost:3000).

4. Przy aplikacjach webowych najlepiej pracuje się mając dwa monitory (a najlepiej mieć
   jeszcze smartfon na podstawce pod jednym z nich :-)). Na zajęciach możesz zasymulować
   to umieszczając na jednej połowie ekranu Twoje IDE a na drugiej - przeglądarkę z uruchomioną
   aplikacją (przydany skrót: Win+Strzałka w prawo lub w lewo umieści aktywne okno odpowiednio
   na prawej lub lewej połowie ekranu).

   Gdy już masz takie ułożenie okien, spróbuj zmienić coś w komponencie  
   `src/App.js`. Po zapisaniu zmian powinny być one natychmiast widoczne w przeglądarce.
   Takie automatyczne aplikowanie zmian do przeglądarki nazywamy *Hot Reloadem*.

   ![hot](react-hot.png?lightbox=false)
