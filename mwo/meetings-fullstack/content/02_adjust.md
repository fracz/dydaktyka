---
title: "Zmiany w aplikacjach"
date: 2023-04-20T09:19:49+02:00
weight: 2
---

Na poprzednich zajęciach stworzyliśmy dwie aplikacje - backendową, która udostępnia REST API
oraz frontendową, która udaje, że z niego korzysta.

Na początek zajęć udostępniam projekt, który połączył te dwa światy w jeden.
Aplikacja w Spring Boot od razu serwuje zbudowane pliki frontendu.
Kod frontendu znalazł się w katalogu `src/main/frontend`.
Po wejściu na stronę główną uruchomionej aplikacji
zobaczysz aplikację frontendową.

Stworzone endpointy backendowe dostępne są po prefixie `/api`.

Oto lista zmian w stosunku do stanu aplikacji z poprzednich zajęć:

1. Utworzyłem katalog `src/main/frontend` i wrzuciłem do niego całą zawartość projektu
   frontendowego z ostatnich zajęć. Aplikacja jest w takim stanie, w jakim powinna
   być po zrealizowaniu całości materiału z poprzednich zajęć. Dodałem pole pozwalające na podanie hasła
   w formularzu logowania.
1. W pliku `pom.xml` dodałem dwa pluginy (szczegóły znajdziesz właśnie tam):
    1. [`frontend-maven-plugin`](https://github.com/eirslett/frontend-maven-plugin) odpowiedzialny za pobranie Node JS
       do projektu, pobranie
       zależności z NPM podczas `mvn install` i zbudowanie aplikacji za pomocą komendy
       `npm run build` przy budowaniu archiwum war aplikacji.
    1. [`maven-resources-plugin`](https://maven.apache.org/plugins/maven-resources-plugin/) odpowiedzialny za
       skopiowanie zbudowanej aplikacji frontendowej
       do katalogu `src/main/resources/public`, czyli katalogu skąd [Spring Boot domyślnie
       serwuje statyczne pliki](https://spring.io/blog/2013/12/19/serving-static-web-content-with-spring-boot).
1. W pliku `src/main/frontend/vue.config.js` dodałem konfigurację dev-servera zmieniającą
   port z `8080` na `9000` oraz konfigurację proxy, która kieruje wszystkie żądania wykonane
   na adres `localhost:9000/api` do serwera ze Spring Boot `localhost:8080/api`. Umożliwia
   to uruchomienie dev serwera tak jak wcześniej (wsparcie live reload).
1. W klasach kontrolerów dopisałem do adnotacji `@RequestMapping` prefixy endpointów tak,
   że teraz mapują one odpowiednio na `@RequestMapping("/api/meetings")` oraz
   `@RequestMapping("/api/participants")`. Jednolity prefix do endpointów restowych
   umożliwia łatwe odróżnienie części frontendowej aplikacji od części backendowej,
   gdy używamy aplikacyjnych adresów URL.
1. Usunąłem `enroller.db`, dodałem jego ścieżkę do `.gitignore` oraz w pliku
   `src/main/resources/` dodałem [jeszcze jeden parametr](https://stackoverflow.com/a/28671036/878514)
   dzięki któremu schemat bazy danych generuje się sam.
   ```xml
   <property name="hibernate.hbm2ddl.auto">create</property>
   ```

Jeśli chcesz użyć kodu swoich dotychczasowych aplikacji (np. w domu) wykonaj
powyższe kroki i "ma działać".
