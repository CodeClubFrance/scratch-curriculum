---
title: Głodna ryba
level: Poziom 2
language: pl-PL
stylesheet: scratch
embeds: "*.png"
materials: "*.sb"
note: "Informacje dla prowadzacych zajecia.md"
...

# Wstęp {.intro}

Zrobimy grę w karmienie ryb! Będziesz kierować dużą głodną rybą pływającą po morzu, aby udało jej się zjeść wszystkie krewetki.

# Krok 1: Stwórz duszka, który zmienia kostiumy {.activity}
__Dodajmy rybę, która pływa po morzu!__

1. Zacznij nowy projekt w Scratchu.
2. Zaznacz Scenę, a następnie przejdź do karty z ustawieniami tła. Zaimportuj tło "underwater" z katalogu Nature. Usuń tło1.
3. Zmień nazwę duszka z Duszek1 na Głodna Ryba.
4. Zaimportuj oba kostiumy Głodnej Ryby z katalogu Zasoby i skasuj istniejący kostium1 i kostium2.
5. Upewnij się, że duszek może obracać się tylko w prawo i lewo.
6. Dodaj skrypt, który każe rybie podążać za kursorem myszy:

```scratch

	kiedy kliknięto FLAGĘ
	zawsze
		ustaw w stronę wskaźnik myszy
		przesuń o 3 kroków
	(koniec zawsze)
```

##Przetestuj swój projekt {.flag}
__Wciśnij zieloną flagę.__
Poruszaj kursorem myszy po morzu. Czy ryba pływa za nim?
Co się dzieje, jeżeli nie ruszasz kursorem i ryba go łapie? Jak to wygląda? Dlaczego tak się dzieje?

7. Możesz zapobiec takiemu motaniu się ryby, jeżeli każesz jej ruszać się tylko wtedy, kiedy nie jest za blisko kursora (w sekcji Czujniki znajdziesz blok _odległość do_).

```scratch

	kiedy kliknięto FLAGĘ
	zawsze, jeżeli odległość do wskaźnik myszy > 10
		ustaw w stronę wskaźnik myszy
		przesuń o 3 kroków
	(koniec zawsze)
```


##Przetestuj swój projekt {.flag}

## Zapisz swój projekt. {.save}

##Rzeczy do spróbowania
Jeżeli chcesz, możesz zmienić liczby w skrypcie. W jaki sposób zmienia to sposób poruszania się Głodnej Ryby? Zmień odległość na jakiąś dużą liczbę (np. 100) albo jakąś bardzo małą (np. 1). Zmień ilość kroków na coś dużego (np. 20) lub małego (np. 1 lub nawet 0). Co się dzieje?


# Krok 2: Dodaj krewetkę {.activity}

1. Stwórz nowego duszka korzystając z kostiumu lobster1 z katalogu Animals.
2. Zmniejsz nowego duszka (narzędzie do zmniejszania znajduje się nad Sceną).
3. Dodaj skrypt, który kieruje pływającą krewetką. Chcemy, aby ruszała się losowo, więc byłoby dobrze, aby najpierw ruszała się trochę do przodu, a potem skręciła albo w lewo, albo w prawo, a potem zaczęła się ruszać od nowa.

```scratch

	kiedy kliknięto FLAGĘ
	zawsze
		przesuń o 2 kroków
		obróć o losuj liczbę pomiędzy -20 a 20 stopni
		jeżeli na brzegu, odbij się
	(koniec zawsze)
```

##Przetestuj swój projekt {.flag}
__Wciśnij zieloną flagę__ i popatrz, jak krewetka porusza się po ekranie. Czy pływa tak jak trzeba? Czy wygląda to realistycznie?

__Obecnie ryba i krewetka nie interesują się sobą. Zajmiemy się tym w następnym kroku.__

## Zapisz swój projekt {.save}

##Rzeczy do spróbowania

* Zmień liczby w bloku __losuj liczbę pomiędzy__ oraz odległość, o jaką porusza się krewetka. W jaki sposób te zmiany wpływają na sposób poruszania się?
* Co robi blok __jeżeli na brzegu, odbij się__? Co się stanie, jak go nie będzie? Usuń go i sprawdź.

# Krok 3: Głodna ryba łapie krewetkę {.activity}

__Chcemy, aby ryba zjadła swoją ofiarę!__ Jak tylko ryba złapie żyjątko, dwie rzeczy muszą mieć miejsce:
* Ryba musi zamknąć paszczę z głośnym "mlask!"
* Krewetka musi zniknąć i pojawić się chwilę później gdzie indziej

1. Na początek sprawmy, aby krewetka znikała po dotknięciu ryby i po 3 sekundach pojawiała się gdzie indziej. Użyjemy bloku __dotyka__, aby sprawdzić, czy krewetka jest w kontakcie z rybą.

```scratch

	kiedy kliknięto FLAGĘ
	zawsze
		przesuń o 2 kroków
		obróć o losuj liczbę pomiędzy -20 a 20 stopni
		jeżeli na brzegu, odbij się
		jeżeli dotyka Głodna Ryba
			ukryj
			czekaj 3 s
			pokaż
		(koniec jeżeli)
	(koniec zawsze)
```

##Przetestuj swój projekt {.flag}
__Spróbuj złapać krewetkę – czy widzisz jakieś problemy?__ Zauważ, że krewetka znika bez względu na to, z której strony dotknie rybę. Poza tym, jeżeli ryba się nie rusza, to po 3 sekundach może od razu zjeść krewetkę – to jest trochę niefajne!

2. Co możemy zrobić, aby upewnić się, że krewetka znika tylko wtedy, gdy ryba dotknie jej paszczą? Możemy skorzystać z czujnika koloru i sprawdzać, czy krewetka dotyka niebieskich zębów ryby! Aby to zrobić, zamień blok 'dotyka Głodna Ryba' na 'dotyka koloru', kliknij kwadracik z kolorem, a gdy kursor myszy się zmieni, kliknij na zębach ryby.
3. Następnie możemy sprawić, aby krewetka przesuwała się w losowe miejsce na ekranie przed ponownym pojawieniem. Możemy użyć do tego bloku 'idź do' i użyć losowych wartości dla x i y.

```scratch

	kiedy kliknięto FLAGĘ
	zawsze
		przesuń o 2 kroków
		obróć o losuj liczbę pomiędzy -20 a 20 stopni
		jeżeli na brzegu, odbij się
		jeżeli dotyka koloru []
			ukryj
			czekaj 3 s
			idź do x: losuj liczbę pomiędzy -220 a 220 y: losuj liczbę pomiędzy -170 a 170
			pokaż
		(koniec jeżeli)
	(koniec zawsze)

```
##Przetestuj swój projekt {.flag}
Spróbuj złapać krewetkę jeszcze raz – czy znika ona tylko wtedy, kiedy dotknie zębów ryby? I czy pojawia się w losowym miejscu na ekranie zamiast od razu tam, gdzie została zjedzona?

4. Ryba musi wiedzieć, kiedy zjadła krewetkę, aby mogła wydać dźwięk i zmienić kostium. Aby to zrobić, musimy najpierw nadać sygnał, że krewetka została zjedzona.

```scratch

	kiedy kliknięto FLAGĘ
	zawsze
		przesuń o 2 kroków
		obróć o losuj liczbę pomiędzy -20 a 20 stopni
		jeżeli na brzegu, odbij się
		jeżeli dotyka koloru []
			nadaj masz mnie
			ukryj
			czekaj 3 s
			idź do x: losuj liczbę pomiędzy -220 a 220 y: losuj liczbę pomiędzy -170 a 170
			pokaż
		(koniec jeżeli)
	(koniec zawsze)

```

__Teraz chcemy, aby ryba odpowiedziała na to głośnym zamknięciem paszczy.__

5. Upewnij się, że Głodna Ryba ma dodane oba kostiumy i dodaj plik z dźwiękiem z katalogu Zasoby (ewentualnie możesz nagrać swój własny dźwięk lub użyć Slurp z katalogu Human).
6. Następnie dodaj skrypt do Głodnej Ryby, który odpowiada na wiadomość nadaną przez jej ofiarę. Skrypt powinien zagrać odgłos jedzenia i zamienić kostium ryby na ten z zamkniętą paszczą, a następnie poczekać chwilę i wrócić do pierwszego kostiumu.

```scratch

	kiedy otrzymam masz mnie
	zagraj dźwięk Slurp
	powtórz 2 razy
		zamień kostium na ryba-paszcza-zamknieta
		czekaj 0.5 s
		zamień kostium na ryba-paszcza-otwarta
	(koniec powtórz)

```

__Skoro nasza Głodna Ryba jest gotowa jeść, wypełnijmy ocean jedzeniem. Kliknij na krewetce prawym przyciskiem myszy i zduplikuj ją kilka razy.__

##Przetestuj swój projekt {.flag}
Kliknij zieloną flagę.
Czy Głodna Ryba zjada swoje ofiary? Czy potrafi zjeść każdą krewetkę?

## Zapisz swój projekt. {.save}

##Rzeczy do przemyślenia
Dlaczego musimy dodać blok 'pokaż' na początku skryptu każdej krewetki? Pomyśl, co by się stało, gdyby gra została zatrzymana zanim zjedzona krewetka ponownie pojawi się na ekranie. Co by się stało po uruchomieniu gry?

__Brawo! Udało Ci się skończyć podstawową wersję gry. Jest jeszcze kilka rzeczy, które możesz zmienić w grze. Pora na wyzwania!__

#Wyzwanie 1: Spraw, aby krewetki poruszały się inaczej

Póki co wszystkie krewetki poruszają się tak samo.

__Spróbuj zmienić sposób w jaki porusza się jedna z krewetek.__

__Podpowiedź:__ Postaraj się nie spędzić na tym zadaniu zbyt dużo czasu. Warto również spojrzeć na inne wyzwania!

__Wybierz jedną krewetkę, nad którą będziesz pracować.__
Jeżeli ma ona ten sam kostium co inne, zmień jego kolor używając bloku __ustaw efekt kolor na__. W ten sposób będziesz łatwo widzieć, nad którą krewetką pracujesz.

Spraw, aby ta krewetka poruszała się wolniej od innych.

__Podpowiedź:__ Spójrz na blok `przesuń o 2 kroków'.

##Przetestuj swój projekt {.flag}
Czy krewetka porusza się wolniej? Czy gra jest teraz lepsza?
Jeżeli udało ci się to zrobić, __wybierz inną krewetkę i spraw, aby poruszała się szybciej od innych.__

Czy krewetki poruszają się naturalnie? Czy gra jest jeszcze lepsza po tych zmianach?

__Podpowiedź__ Jeżeli krewetki pływają w kółko, zmień wartości z bloku 'losuj liczbę pomiędzy'.

A może spróbujesz zmienić zachowanie krewetek, tak aby każda poruszała się inaczej? Wykorzystaj wprowadzone poprzednio zmiany.

Czy te zmiany sprawiły, że gra jest jeszcze lepsza? Czy gra podoba ci się bardziej, jest trudniejsza czy łatwiejsza? Może któraś konkretna zmiana podoba ci się najbardziej?

## Zapisz swój projekt {.save}

#Wyzwanie 2: Spraw, aby krewetki unikały głodnej ryby.

Krewetki w tej grze nie zachowują się zbyt mądrze: po prostu pływają w kółko i dają się zjeść rybie. Prawdziwa krewetka na pewno próbowała by uciec od drapieżnika!

__Spróbujmy sprawić, aby jedna z krewetek uciekała przed Głodną Rybą__

W Scratchu nie ma bloku, który powiedziałby ci, w którym kierunku porusza się inny duszek. Ale możesz sprawić, aby duszek zwrócił się w kierunku innego duszka, a potem odwrócił się od niego plecami. Bloki, których będziesz potrzebować, znajdują się w palecie __Ruch__.

Wykorzystując ten pomysł, __spraw, aby jedna z krewetek zawsze była odwrócona do Głodnej Ryby plecami__. Może spróbujesz sprawić, aby się trzęsła jak będzie uciekać?

##Przetestuj swój projekt {.flag}
Czy teraz trudniej jest złapać krewetkę? Czy gra jest teraz lepsza?

## Zapisz swój projekt {.save}

#Wyzwanie 3: Dodaj punkty

Ale zjadanie krewetek to nie wszystko. Skąd będziesz wiedzieć, czy umiesz grać w tę grę lepiej niż inni gracze?
__Potrzebujesz w jakiś sposób liczyć ile krewetek udało Ci się zjeść__. Już robiliśmy coś podobnego wcześniej.

Gdzie należy dodać blok, który będzie zmieniał ilość punktów?

Upewnij się, żeby punkty przestawiały się na zero przy rozpoczęciu nowej gry. Gdzie trzeba dodać ten blok?

##Przetestuj swój projekt {.flag}
Czy jak zaczynasz nową grę, to ilość punktów jest równa zero? Czy dostajesz punkt za każdą zjedzoną krewetkę?

## Zapisz swój projekt. {.save}

#Wyzwanie 4: Dodaj zegar

__Ograniczmy czas, w którym możesz zjadać krewetki.__ Jak wiele krewetek uda ci się zjeść w ciągu 30 sekund?

Jeżeli nie masz pomysłu, jak to zrobić, poproś osobę prowadzącą zajęcia o kartę __Zegar__ (Timer). Na początek niech gra trwa 30 sekund.

##Przetestuj swój projekt {.flag}
Czy jak zaczynasz grę, zegar wskazuje 30?

Czy zegar poprawnie odlicza czas?

Czy udaje Ci się zjeść jakieś krewetki w tym czasie?

Czy gra się zatrzymuje po upływie czasu?

## Zapisz swój projekt. {.save}

#Wyzwanie 5: Zdobądź dodatkowe punkty
Zdobywaj dodatkowe punkty, jeżeli uda Ci się zjeść 3 krewetki na raz! W jaki sposób możesz sprawdzić, ile krewetek udało Ci się zjeść?

__Podpowiedź:__ Jeden ze sposobów, w jaki możesz to zrobić, to __użyć zmiennej, która policzy jak wiele krewetek pływa wokoło ryby__.

## Zapisz swój projekt. {.save}

#Wyzwanie 6: Zmień cel gry: krewetka musi przeżyć!
Czasami super pomysły przychodzą do głowy, jeżeli spróbujesz zrobić coś na odwrót.

__Zmień grę w ten sposób, żeby zamiast sterować Głodną Rybą, która próbuje zjeść krewetki, sterowało się krewetką otoczoną wieloma Głodnymi Rybami__. Jak długo uda jej się przetrwać, zanim zostanie zjedzona?

## Zapisz swój projekt. {.save}

__Brawo! To by było na tyle, teraz możesz się cieszyć swoją grą!__
Nie zapomnij, że możesz podzielić się swoją grą ze swoimi przyjaciółmi i rodziną. Żeby to zrobić, kliknij menu __Udostępnij__.
