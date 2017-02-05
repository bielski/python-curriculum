---
title: Pokedex
level: Python 2
language: pl
stylesheet: python
embeds: "*.png"
materials: ["Project Resources/*.*","Club Leader Resources/*.*"]
...

#Wstęp:  { .intro}

W tym projekcie nauczysz się jak stworzyć graficzny interfejs użytkownika (ang. _graphical user interface_, GUI), na przykładzie Pokedexu, czyli programu do wyszukiwania informacji o Pokemonach.

Tak będzie wyglądał Twój Pokedex:

![screenshot](gui-command.png)

## Informacje o Pokemonach { .challenge }
Informacje o Pokemonach, których użyjemy w tym projekcie są dostępne poprzez <a href="http://pokeapi.co/">pokeAPI</a>, którego autorem jest Paul Hallet.

#Step 1: Widżet! { .activity}
## Lista zadań { .check}

+ Graficzny interfejs użytkownika (GUI) może być łatwo stworzony poprzez użycie modułu 'tkinter'. GUI może zawierać dużo różnych elementów nazywany _widżetami_. Oto przykład:

    ```python
    from tkinter import *

    #stwórz nowe okno
    okno = Tk()
    okno.title("Okno")

    #etykietę
    etykieta = Label(okno,text="Etykieta")
    etykieta.pack()

    #pole tekstowe
    tekst = Entry(okno)
    tekst.pack()

    #przycisk
    przycisk = Button(okno,text="Przycisk")
    przycisk.pack()

    okno.mainloop()
    ```
    
    Jeśli uruchomisz ten program, zobaczysz okno, które ma etykietę, pole do wprowadzenia tekstu oraz przycisk.

    ![screenshot](gui-widgets.png)

    Każdy widżet jest stworzony i przechowywany za pomocą zmiennej, a następnie osadzony w głównym oknie. Zwróć uwagę, że podczas tworzenia widżetu należy podać w jakim oknie powinien się pojawić oraz jaki tekst ma wyświetlić, np.:

    ```python
    #etykieta
    etykieta = Label(okno,text="Etykieta")
    ```

+ Możesz teraz dodać więcej etykiet do swojego Pokedexa:

    ```python
    from tkinter import *

    #stwórz nowe okno GUI
    okno = Tk()
    okno.title("Pokedex")

    #etykietę zawierającą instrukcje
    etykietaInstrukcje = Label(okno,text="Wprowadź numer od 1 do 718:")
    etykietaInstrukcje.pack()

    #pole do wprowadzania tekstu aby móc wpisać numer pokemona
    tekstNumerPokemona = Entry(okno)
    tekstNumerPokemona.pack()

    #przycisk, za pomocą którego pobierzesz informacje o pokemonie
    przyciskPobierzDane = Button(okno,text="Pobierz informacje!")
    przyciskPobierzDane.pack()

    #etykietę dla nazwy pokemona
    etykietaNazwa = Label(okno,text="Nazwa:")
    etykietaNazwa.pack()
    etykietaNazwa = Label(okno,text="???")
    etykietaNazwa.pack()

    okno.mainloop()
    ```

    ![screenshot](gui-more-widgets.png)

    Jak widzisz, do programu zostało dodanych wiele pomocnych komentarzy, które przypominają czemu służy każda z etykiet. Nazwy zmiennych również zostały stworzone tak, aby program był łatwy do zrozumienia.

## Zapisz swój projekt {.save}

## Wyzwanie: Więcej widżetów { .challenge}
Dokończ swoj GUI do wyświetlania informacji o Pokemonach tak by wyglądało jak poniżej:

![screenshot](gui-pokedex-widgets.png)

Twój GUI potrzebuje jeszcze:
+ Pola tekstowego do wpisania którego Pokemona chcesz zobaczyć;
+ Przycisku, który wyszukuje informacje o Pokemonie;
+ Etykiety, które pokazują informacje o Pokemonie:
    + Nazwę;
    + Ilość obrażeń (ang. _Hit Points_, HP);
    + Zdolność do ataku;
    + Zdolność do obrony;
    + Szybkość;

Pamiętaj, że dodawanie komentarzy i używanie rozsądnych nazw zmiennych pomoże Ci w późniejszym zrozumieniu kodu!

## Zapisz swój projekt {.save}

#Step 2: Dostosuj swoje widżety { .activity}

Masz wiele różnych widżetów w swoim GUI, możesz teraz zmienić ich wygląd. 

## Lista aktywności { .check}

+ Spróbujmy zmienić kolory Twoich widżetów tak by wyglądały ciekawiej. Zmień kod, który odpowiada za wyświetlenie głównego okna w następujący sposób:  

    ```python
    #stwórz nowe okno GUI
    okno = Tk()
    okno(bg="#e0e0ff")
    okno("Pokedex")
    ```

    ![screenshot](gui-window-bg.png)

    Użycie `.config()` pozwala Ci _skonfigurować_ jak wyglądają poszczególne elementy. Jak być może się domyślasz, `bg` oznacza tło, a `"#e0e0ff"` to kod odpowiedzialny za kolor jasny fiolet. Możesz również zmienić sposób w jaki wyglądają widżety, np. etykiety, które wyświetlają nazwę Pokemona: 

    ```python
    #etykiety dla nazwy Pokemona
    etykietaNazwa = Label(okno,text="Nazwa:")
    etykietaNazwa.config(bg="#e0e0ff", fg="#111111")
    etykietaNazwa.pack()
    etykietaNazwaWartość = Label(okno,text="???")
    etykietaNazwaWartość.config(bg="#e0e0ff", fg="#111111")
    etykietaNazwaWartość.pack()
    ```

    ![screenshot](gui-colour.png)

    `fg` oznacza element wysunięty na pierwszy plan, pozwala ustawić kolor tekstu etykiety. 

+ Możesz też zmienić czcionkę każdego z widżetów. Jest to możliwe dzięki stworzeniu zmiennych, które będą zawierały informacje o różnych czcionkach. Dodaj poniższy kod do swojego programu zaraz po linii, która importuje moduł `tkinter`:

    ```python
    małaCzcionka= ["Helvetica" , 14]
    średniaCzcionka = ["Helvetica" , 18]
    dużaCzcionka = ["Helvetica" , 30]
    ```

    Możesz teraz wybrać czcionkę każdego z widżetów w poniższy sposób:

    ```python
    #etykiety dla nazwy Pokemona
    etykietaNazwa = Label(okno,text="Nazwa:")
    etykietaNazwa.config(bg="#e0e0ff", fg="#111111", font=średniaCzcionka)
    etykietaNazwa.pack()
    etykietaNazwaWartość = Label(okno,text="???")
    etykietaNazwaWartość.config(bg="#e0e0ff", fg="#111111", font=dużaCzcionka)
    etykietaNazwaWartość.pack()
    ```

    Dodaliśmy `font=średniaCzcionka` and `font=dużaCzcionka` do `.config()`.

    ![screenshot](gui-font.png)

## Zapisz swój projekt {.save}

## Wyzwanie: Upiększ swoje widżety { .challenge}
Dodaj czcionki i kolory do swojego Pokedexa tak, by wyglądał jeszcze atrakcyjniej. Poniżej przykład, jak może wyglądać upiększony Pokedex GUI:

![screenshot](gui-pokedex-style.png)

Twój Pokedex może wyglądać inaczej, niż ten przedstawiony powyżej. Możesz używać różnych czcionek, np. `Times`, `Courier` lub jakiejkolwiek innej czcionki, którą masz zainstalowaną na komputerze. Możesz również wybrać swój własny kolor <a href="https://www.tcl.tk/man/tcl8.6/TkCmd/colors.htm">colours</a> (włączając <a href="http://www.colorpicker.com/">hex colours</a>).

## Zapisz swój projekt {.save}

#Step 3: Dodawanie komend { .activity }

Twoje GUI wygląda świetnie, dodajmy teraz przycisk, który wyświetli informacje o Pokemonie!

## Lista aktywności { .check}

+ Najpierw upewnij się, że w tym samym folderze co Twój program Pokedex GUI masz zachowany plik `pokeapi.py`. Jeśli nie możesz znaleźć pliku, poproś o pomoc nauczyciela. Plik zawiera funkcję `getPokemonData()`, która pobiera wszystkie informacje o określonym Pokemonie. Aby wykorzystać tę funkcję, musisz tylko zaimportować funkcję z pliku `pokeapi.py`. Aby to zrobić umieść kod poniżej na początku swojego programu:

    ```python
    from pokeapi import *
    ```

+ Stwórzmy teraz nową funkcję `pokazDaneOPokemonie()`, która będzie używać zaimportowanej funkcji `getPokemonData()`. Funkcja będzie pobierać dane o Pokemonie z konkretnym numerem i wyświetli ją za pomocą etykiet. Umieść kod poniżej w swoim programie: 

    ```python
    #funkcja wyświetla informacje o Pokemonie z konkretnym numerem
    def pokazDaneOPokemonie():
    	#pobierz numer Pokemona wpisany w pole tekstowe
    	numerPokemona = tekstNumerPokemona.get()
    	
        #użyj funkcji z pliku 'pokeapi.py' aby pobrać informacje o Pokemonie
    	słownikPokemonów = pobierzInfoOPokemonie(numerPokemona)

    	#wyświetl dane dotyczące Pokemona za pomocą etykiet
    	etykietaNazwa.configure(text = słownikPokemonów["Nazwa"])
    	etykietaObrażeniaWartość.configure(text = słownikPokemonów["Ilość obrażeń"])
    ```

    Nie musisz przejmować się jak działa funkcja `pobierzInfoOPokemonie()`. Ważne jest by zrozumieć, że funkcja zwraca (ang. _return_) dane w postaci słownika. Jest on później użyty w celu wyświetlenia etykiet z nazwą i ilością obrażeń Pokemona. 

+ Masz wszystkie funkcje, których potrzebujesz do działania programu. Pozostaje dodanie odpowiedniej komendy do przycisku:

    ```python
    #przycisk za pomocą którego wyświetlane są informacje o Pokemonie
    przyciskPobierzDane = Button(okno,text="Pobierz informacje!", command=getPokemonData)
    ```
    Spróbuj teraz wpisać numer w pole tekstowe i zobacz co się stanie:

    ![screenshot](gui-command.png)

+ Możesz zmodyfikować bieżącą grę i stworzyć jej nową wersję, Top Pokemony. Wystarczy, że usuniesz pole do wprowadzania numeru Pokemona i pokażesz losowo wybrane stworzenie. Aby to uczynić, zmodyfikuj funkcję `showPokemonData()` w następujący sposób:

    ```python
    #funkcja wyświetla informacje o Pokemonie z konkretnym numerem
    def pokazDaneOPokemonie():
    	#wybierz losowy numer Pokemona
    	numerPokemona = randint(1,718) 

    	#(reszta funkcji pozostaje taka sama...)
    ```
        
    Zwróć uwagę, aby na górze programu zaimportować moduł `random` (`from random import *`). Teraz możesz zaprosić znajomych do gry i porównywać czyj Pokemon ma wyższe noty dla określonej cechy (np. szybkość, zdolność do ataku).

## Zapisz swój projekt {.save}

## Wyzwanie: Dokończ swój Pokedex { .challenge}
+ Dodaj kod do funkcji `showPokemonData()`, który wyświetli informacje o zdolności do ataku, obrony i szybkości Pokemona. Aby to uczynić, potrzebna będzie wiedza o wartości kluczy słownika:
	+ Atak - `słownikPokemonów["attack"])`
	+ Obrona - `słownikPokemonów["defense"])` (notice the American spelling!)
	+ Szybkość - `słownikPokemonów["speed"])`

+ Jeśli chcesz, możesz zmienić (lub dodać) informacje, które są wyświetlane o Pokemonie. Możesz wyświetlić `"happiness"`, `"height"`, `"weight"` czyli szczęście, wysokość czy wagę poszczególnego Pokemona. Aby wyświetlić wszystkie dostępne cechy Pokemonów, wejdż na stronę <a href="http://pokeapi.co/">this website</a>.  

![screenshot](gui-pokedex-finished.png)

## Zapisz swój projekt {.save}

#Step 4: (Dla chętnych) Dodawanie obrazka { .activity }

Możesz również wyświetlić obrazek wybranego z Pokedexa Pokemona!

![screenshot](67.png)

## Uwaga { .challenge }
Poniższy krok możesz wykonać gdy masz zainstalowany na swoim komputerze moduł 'pillow'. Jeśli nie jesteś pewien, spytaj swojego nauczyciela o pomoc.

## Lista aktywności { .check}

+ Dość trudno wyświetlić obrazek Pokemona w Twoim Pokedexie. Na pomoc przychodzi funkcja `getPokemonImage()` w pliku `pokeapi.py`, pomoże Ci w tym zadaniu! Funkcja ta pobiera obrazek Pokemona, które może zostać wyświetlone w etykiecie. Najpierw musimy utworzyć etykietę. Dodaj poniższy kod w swoim głównym programie, w miejscu gdzie definiowane są inne etykiety:

    ```python
    #etykieta dla obrazka Pokemona
    etykietaObraz = tkinter.Label(okno)
    etykietaObraz.config(bg="#e0e0ff", fg="#111111")
    etykietaObraz.pack()
    ```

+ Teraz możesz zmodyfikować funkcję `showPokemonData()` aby wyświetlała informacje o obrazku:

    ```python
    #funkcja wyświetla informacje o Pokemonie z konkretnym numerem
    def pokazDaneOPokemonie():
        #wybierz losowy numer Pokemona
        numerPokemona = randint(1,178)

        #użyj funkcji do pobrania informacji o Pokemonie i jego obrazka
        słownikPokemonów = getPokemonData(numerPokemona)
        pokemonImage = getPokemonImage(numerPokemona)

        #wyświetl dane dotyczące Pokemona za pomocą etykiet
        lblNameValue.configure(text = słownikPokemonów["name"])
        lblHPValue.configure(text = słownikPokemonów["hp"])
        lblAttackValue.configure(text = słownikPokemonów["attack"])
        lblDefenceValue.configure(text = słownikPokemonów["defense"])
        lblSpeedValue.configure(text = słownikPokemonów["speed"])
        
        #dodaj obrazek i jego etykietę
        etykietaObraz.pack.configure(image=pokemonImage)
        etykietaObraz.pack.image = pokemonImage
    ```

+ Kiedy uruchomisz swój program i klikniesz "Pobierz Pokemona!" powinieneś zobaczyć poniższy obrazek!

    ![screenshot](gui-pokedex-image.png)

## Zapisz swój projekt {.save}
