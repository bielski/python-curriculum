---
title: Pokedex
level: Python 2
language: pl
stylesheet: python
embeds: "*.png"
materials: ["Project Resources/*.*","Club Leader Resources/*.*"]
...

#Wstęp:  { .intro}

W tym projekcie nauczysz się jak stworzyć graficzny interfejs użytkownika (ang. _graphical user interface_, GUI), poprzez stworzenie Pokedexu (programu, za pomocą którego wyszukasz informacje o Pokemonach).

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

    Każdy widżet jest stworzony i przechowywany za pomocą zmiennej, a następnie osadzony w głównym oknie. Zwróć uwagę, że podczas tworzenia widżetu, należy podać w jakim oknie powinien się pojawić oraz jaki tekst ma wyświetlić, np.:

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
    przyciskPobierzInfo = Button(okno,text="Pobierz informacje!")
    przyciskPobierzInfo.pack()

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

Twoje GUI potrebuje jeszcze:
+ Pole tekstowe do wpisania którego Pokemona chcesz zobaczyć;
+ Przycisk, który wyszukuje informacje o Pokemonie;
+ Etykiety, które pokazują informacje o Pokemonie:
    + Nazwa;
    + Ilość obrażeń (ang. _Hit Points_, HP);
    + Atak;
    + Obrona;
    + Szybkość;

Pamiętaj, że dodawanie komentarzy i używanie rozsądnych nazw zmiennych pomoże Ci w późniejszym zrozumieniu kodu!

## Zapisz swój projekt {.save}

#Step 2: Dostosuj swoje widżety { .activity}

Masz teraz wiele różnych widżetów w swoim GUI, możesz teraz zmienić ich wygląd. 

## Lista aktywności { .check}

+ Najpierw, spróbujmy zmienić kolory Twoich widżetów by wyglądały ciekawiej. Zmień kod, który odpowiada za wyświetlenie głównego okna w następujący sposób:  

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
    lblNameValue = Label(okno,text="???")
    lblNameValue.config(bg="#e0e0ff", fg="#111111")
    lblNameValue.pack()
    ```

    ![screenshot](gui-colour.png)

    `fg` oznacza element wysunięty na pierwszy plan, pozwala ustawić kolor tekstu etykiety. 

+ Możesz też zmienić czcionkę każdego z widżetów. Jest to możliwe dzięki stworzeniu zmiennych, które będą zawierały informacje o różnych czcionkach. Dodaj poniższy kod do swojego programu zaraz po lini, która importuje moduł `tkinter`:

    ```python
    małaCzcionke = ["Helvetica" , 14]
    średniaCzcionka = ["Helvetica" , 18]
    dużaCzcionka = ["Helvetica" , 30]
    ```

    Możesz teraz wybrać czcionkę każdego z widżetów w poniższy sposób:

    ```python
    #etykiety dla nazwy Pokemona
    etykietaNazwa = Label(okno,text="Nazwa:")
    etykietaNazwa.config(bg="#e0e0ff", fg="#111111", font=średniaCzcionka)
    etykietaNazwa.pack()
    lblNameValue = Label(okno,text="???")
    lblNameValue.config(bg="#e0e0ff", fg="#111111", font=dużaCzcionka)
    lblNameValue.pack()
    ```

    Dodaliśmy `font=średniaCzcionka` and `font=dużaCzcionka` do `.config()`.

    ![screenshot](gui-font.png)

## Zapisz swój projekt {.save}

## Wyzwanie: Upiększ swoje widżety { .challenge}
Dodaj czcionki i kolory do swojego Pokedexa tak by wyglądał jeszcze atrakcyjniej. Poniżej przykład, jak może wyglądać upiększony Pokedex GUI:

![screenshot](gui-pokedex-style.png)

Twój Pokedex może wyglądać inaczej, niż ten przedstawiony powyżej. Możesz używać różnych czcionek, np. `Times`, `Courier` lub jakiejkolwiek innej czcionki, którą masz zainstalowaną na komputerze. Możesz również wybrać swoją własną <a href="https://www.tcl.tk/man/tcl8.6/TkCmd/colors.htm">colours</a> (including <a href="http://www.colorpicker.com/">hex colours</a>).

## Zapisz swój projekt {.save}

#Step 3: Dodawanie komend { .activity }

Twój GUI wygląda świetnie, dodajmy teraz przycisk, który wyświetli informacje o Pokemonie!

## Lista aktywności { .check}

+ Najpierw upewnij się, że w tym samym folderze co Twój program Pokedex GUI masz zachowany plik `pokeapi.py`. Jeśli nie możesz znaleźć pliku, poproś o pomoc nauczyciela. Plik zawiera funkcję `pobierzInfoOPokemonie()`, która pobiera wszystkie informacje o określonym Pokemonie. Aby wykorzystać tę funkcję, musisz tylko zaimportować funkcję z pliku `pokeapi.py`. Aby to zrobić umieść kod poniżej na początku swojego programu:

    ```python
    from pokeapi import *
    ```

+ Stwórzmy teraz nową funkcję `pokażInfoOPokemonie()`, która będzie używać zaimportowanej funkcji `pobierzInfoOPokemonie()`. Funkcja będzie pobierać dane o Pokemonie z konkretnym numerem i wyświetli ją za pomocą etykiet. Umieść kod poniżej w swoim programie: 

    ```python
    #funkcja wyświetla informacje o Pokemonie z konretnym numerem
    def pokażInfoOPokemonie():
    	#pobierz numer Pokemona wpisany w pole tekstowe
    	numerPokemona = tekstNumerPokemona.get()
    	
        #użyj funkcji z pliku 'pokeapi.py' aby pobrać informacje o Pokemonie
    	słownikPokemon = pobierzInfoOPokemonie(numerPokemona)

    	#wyświetl dane dotyczące Pokemona za pomocą etykiet
    	etykietaNazwa.configure(text = słownikPokemon["Nazwa"])
    	lblHPValue.configure(text = słownikPokemon["Ilość obrażeń"])
    ```

    Nie musisz przejmować się jak działa funkcja `pobierzInfoOPokemonie()`. Ważne jest by zrozumieć, że funkcja zwraca (ang. _return_) dane w postaci słownika. Jest on później użyty w celu wyświetlenia etykiet z nazwą i ilością obrażeń Pokemona. 

+ Masz wszystkie funkcje, które potrzebujesz do działania programu. Pozostaje dodanie odpowiedniej komendy do przycisku:

    ```python
    #przycisk za pomocą którego wyświetlane są informacje o Pokemonie
    przyciskPobierzInfo = Button(okno,text="Pobierz informacje!", command=pokażInfoOPokemonie)
    ```
    Spróbuj teraz wpisać numer w pole tekstowe i zobacz co się stanie:

    ![screenshot](gui-command.png)

+ You could even make a Pokemon Top Trumps game, by removing the text entry widget, and instead getting a random Pokemon to show each time. Just change the `showPokemonData()` function to:

    ```python
    #function to display data for a pokemon number
    def showPokemonData():
    	#get a random pokemon number
    	pokemonNumber = randint(1,718)

    	#(the rest of the function stays the same...)
    ```

    Remember to import the `random` module at the top of your program (`from random import *`). You can then score points against a friend, by seeing who has the highest number for a particular skill.

## Zapisz swój projekt {.save}

## Challenge: Dokończ swój Pokedex { .challenge}
+ Add code to your `showPokemonData()` function to display the attack, defence and speed of a Pokemon. You'll need to know that the dictionary keys are:
	+ Attack - `pokemonDictionary["attack"])`
	+ Defence - `pokemonDictionary["defense"])` (notice the American spelling!)
	+ Speed - `pokemonDictionary["speed"])`

+ Jeśli chcesz, możesz zmienić (lub dodać) informacje, które są wyświetlane o Pokemonie. Możesz wyświetlić `"happiness"`, `"height"`, `"weight"` czyli szczęście, wysokość czy wagę poszczególnego Pokemona. Aby wyświetlić wszystkie dostępne cechy Pokemonów, wejdż na stronę <a href="http://pokeapi.co/">this website</a>.  

![screenshot](gui-pokedex-finished.png)

## Zapisz swój projekt {.save}

#Step 4: (Optional) Dodawanie obrazka { .activity }

Możesz również wyświetlić obrazek wybranego z Pokedexa Pokemona!

![screenshot](67.png)

## Note { .challenge }
Poniższy krok możesz wykonać gdy masz zainstalowany na swoim komputerze moduł 'pillow'. Jeśli nie jesteś pewien, spytaj swojego nauczyciela o pomoc.

## Lista aktywności { .check}

+ It's quite hard to display a Pokemon image in your Pokedex, but don't worry - there's a `getPokemonImage()` function in the `pokeapi.py` file to do the hard work for you! This function gets the Pokemon image, which can be displayed in a label. First, let's create a label to display the image in. Add this code somewhere in your main program, with the other labels:

    ```python
    #label for the pokemon image
    lblImage = tkinter.Label(window)
    lblImage.config(bg="#e0e0ff", fg="#111111")
    lblImage.pack()
    ```

+ You can now modify the `showPokemonData()` function to also show the image:

    ```python
    #function to display data for a pokemon number
    def showPokemonData():
        #get the number typed into the entry box
        pokemonNumber = randint(1,178)

        #use the function above to get the pokemon data and the image
        pokemonDictionary = getPokemonData(pokemonNumber)
        pokemonImage = getPokemonImage(pokemonNumber)

        #get the data from the dictionary and add it to the labels
        lblNameValue.configure(text = pokemonDictionary["name"])
        lblHPValue.configure(text = pokemonDictionary["hp"])
        lblAttackValue.configure(text = pokemonDictionary["attack"])
        lblDefenceValue.configure(text = pokemonDictionary["defense"])
        lblSpeedValue.configure(text = pokemonDictionary["speed"])
        
        #add the image and add it to a label
        lblImage.configure(image=pokemonImage)
        lblImage.image = pokemonImage
    ```

+ Kiedy uruchomisz swój program i klikniesz "Pobierz Pokemona!" powinieneś zobaczyć obrazek!

    ![screenshot](gui-pokedex-image.png)

## Zapisz swój projekt {.save}
