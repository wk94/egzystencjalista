---
{"dg-publish":true,"permalink":"/2-obowiazki/blog/obsidian-jak-stworzyc-baze-filmow-seriali-gier/","dgHomeLink":true,"dgPassFrontmatter":false}
---


# Obsidian - jak stworzyć bazę filmów, seriali, gier

[[- 4 - Archiwum/Kalendarz/2022/06-czerwiec/2022-06-27|2022-06-27]]

**Obsidian** posiada funkcje, które pozwalają stworzyć bazę obejrzanych filmów i seriali, ulubionej muzyki czy nawet posiadanych gier. Poniżej jest szczegółowa instrukcja jak to zrobić.

### Wymagania
- Minimal Theme (opcjonalnie)
- Templates - Szablony (core plugins)
- Dataview (community plugins)
- Media DB (community plugins)

*Przeczytaj [[- 2 - Obowiązki/Blog/Obsidian - poradnik dla początkujących 2022|Obsidian - poradnik dla początkujących 2022]] jeśli nie wiesz jak instalować motywy lub wtyczki.*

### Wstępna konfiguracja
1. Pobierz te [szablony](https://github.com/mProjectsCode/obsidian-media-db-templates) klikając na zielony przycisk *Code* i wybierając opcję *Download ZIP*;
2. Rozpakuj pobrane szablony do folderu i przenieś je do swojego sejfu w Obsidian;
3. Otwórz *Ustawienia* > *Opcje wtyczek* > *Dataview*;
4. Włącz *Enable JavaScript Queries* i *Enable Inline JavaScript Queries*;
5. Otwórz *Ustawienia* > *Opcje wtyczek* > *Media DB Plugin*;
6. *New File Location* > folder na notatki;
7. Wpisz twój klucz do *[OMDb API](https://www.omdbapi.com/apikey.aspx?__EVENTTARGET=freeAcct&__EVENTARGUMENT=&__LASTFOCUS=&__VIEWSTATE=%2FwEPDwUKLTIwNDY4MTIzNQ9kFgYCAQ9kFgICBw8WAh4HVmlzaWJsZWhkAgIPFgIfAGhkAgMPFgIfAGhkGAEFHl9fQ29udHJvbHNSZXF1aXJlUG9zdEJhY2tLZXlfXxYDBQtwYXRyZW9uQWNjdAUIZnJlZUFjY3QFCGZyZWVBY2N0oCxKYG7xaZwy2ktIrVmWGdWzxj%2FDhHQaAqqFYTiRTDE%3D&__VIEWSTATEGENERATOR=5E550F58&__EVENTVALIDATION=%2FwEdAAU%2BO86JjTqdg0yhuGR2tBukmSzhXfnlWWVdWIamVouVTzfZJuQDpLVS6HZFWq5fYpioiDjxFjSdCQfbG0SWduXFd8BcWGH1ot0k0SO7CfuulHLL4j%2B3qCcW3ReXhfb4KKsSs3zlQ%2B48KY6Qzm7wzZbR&at=freeAcct&Email=)*;
8. *Template Settings* > wybierz pobrane wcześniej szablony;

### Tworzenie notatek
- Aby stworzyć nową notatkę na temat filmu, serialu lub gry należy wybrać *Add new Media DB entry* na pasku z lewej strony lub za pomocą panelu komend *CMD+P*/*CTRL+P*.
- Następnie określamy jakiego rodzaju notatkę tworzymy wybierając odpowiednie API.
- Jeśli kliknęliśmy na ikonkę z lewej strony, wpisujemy tytuł szukanej przez nas rzeczy. Jeśli natomiast korzystamy z panelu komend możemy określić czy wyszukujemy po *tytule* czy *id*.
- Pojawi się lista, z której wybieramy interesującą nas rzecz. Notatka utworzy się z szablonu w określonym wcześniej folderze.

**UWAGA!** Aby utworzyć notatki z filmów lub seriali musimy mieć swój indywidualny klucz, który można uzyskać za darmo [tutaj](https://www.omdbapi.com/apikey.aspx?__EVENTTARGET=freeAcct&__EVENTARGUMENT=&__LASTFOCUS=&__VIEWSTATE=%2FwEPDwUKLTIwNDY4MTIzNQ9kFgYCAQ9kFgICBw8WAh4HVmlzaWJsZWhkAgIPFgIfAGhkAgMPFgIfAGhkGAEFHl9fQ29udHJvbHNSZXF1aXJlUG9zdEJhY2tLZXlfXxYDBQtwYXRyZW9uQWNjdAUIZnJlZUFjY3QFCGZyZWVBY2N0oCxKYG7xaZwy2ktIrVmWGdWzxj%2FDhHQaAqqFYTiRTDE%3D&__VIEWSTATEGENERATOR=5E550F58&__EVENTVALIDATION=%2FwEdAAU%2BO86JjTqdg0yhuGR2tBukmSzhXfnlWWVdWIamVouVTzfZJuQDpLVS6HZFWq5fYpioiDjxFjSdCQfbG0SWduXFd8BcWGH1ot0k0SO7CfuulHLL4j%2B3qCcW3ReXhfb4KKsSs3zlQ%2B48KY6Qzm7wzZbR&at=freeAcct&Email=)! Tytuł należy wpisywać w języku angielskim, a w przypadku anime najlepiej oryginalny.

### Tworzenie bazy danych
Aby utworzyć bazę obejrzanych filmów i seriali czy posiadanych gier będziemy korzystać z **Dataview**.

1. Utwórz nową notatkę, nazwij ją np. *filmy*;
2. Na samej górze umieść:
```
---
cssClasses: cards, cards-cover, table-max
---
```
3. Utwórz tabelę za pomocą **Dataview** w następujący sposób:
```
"```dataview
table without id 
	("![](" + image + ")") as Poster,
	file.link as Title,
	"⭐ " + onlineRating as "⭐"
from #mediaDB/tv 
where image != null
```"
```
4. Możesz dodać swoje pola, które są zdefiniowane w notatce na samej górze:
```
---
type: "movie"
title: "Doctor Strange in the Multiverse of Madness"
englishTitle: "Doctor Strange in the Multiverse of Madness"
year: "2022"
dataSource: "OMDbAPI"
url: "https://www.imdb.com/title/tt9419884/"
id: "tt9419884"
genres: 
  - "Action"
  - "Adventure"
  - "Fantasy"
producer: "Sam Raimi"
duration: "126 min"
onlineRating: 7.3
image: "https://m.media-amazon.com/images/M/MV5BNWM0ZGJlMzMtZmYwMi00NzI3LTgzMzMtNjMzNjliNDRmZmFlXkEyXkFqcGdeQXVyMTM1MTE1NDMx._V1_SX300.jpg"
released: true
premiere: "6.05.2022"
watched: true
lastWatched: "[[2022-06-22|2022-06-22]]"
personalRating: 0
tags: "#mediaDB/tv/movie"
---
```

**Brawo!** Właśnie stworzyłeś/aś swoją bazę filmów, seriali, gier, czy co tam jeszcze chcesz śledzić. Mogłoby się wydawać, że to trudne, ale wystarczy zrozumieć podstawowe zasady działania wtyczki *Dataview*, aby tworzyć jeszcze bardziej skomplikowane bazy danych.