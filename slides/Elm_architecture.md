- title : The Elm Architecture
- description : Jednoduché představení architektury aplikací v jazyce Elm.
- author : Miroslav Veith
- theme : Blood
- transition : concave

***

## Architektura v Elmu
 
![alt Elm](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f3/Elm_logo.svg/256px-Elm_logo.svg.png "Elm")

###### [Miroslav Veith](https://twitter.com/miroveith)

***

### Elm?

---

### A Nightmare on *Elm* Street?

![alt Elm Street](https://media.giphy.com/media/3otPoPWetYFLGwDDQ4/giphy.gif "Elm Street")

---

### Jazyk Elm!

- [elm-lang.org](http://elm-lang.org/)
- _Nádherný jazyk pro spolehlivé webové aplikace_
- Funkcionální jazyk pro psaní webových aplikací, který se kompiluje do JS
- Developer-friendly přístup
- Výjimečné vlastnosti:
    - kompilátor, který pomáhá - [užitečné error message](http://elm-lang.org/blog/compilers-as-assistants)
    - architektura, kterou Elm vynucuje

***

### Elm architektura

![alt Architektura](https://pbs.twimg.com/media/DYImH4mW4AA0SHe.jpg "Architektura") 

---

### Elm architektura
 - Model
 - Update
 - View

---

### Elm architektura

#### Model

    [lang=elm]
    type alias Model = { ... }
    
 - Objekt, který reprezentuje celý stav aplikace

---

### Elm architektura

#### Update
    [lang=elm]
    type Msg = Reset | ...

    update : Msg -> Model -> Model
    update msg model =
    case msg of
        Reset -> ...
        ...

 - Funkce přebírající **Message** a aktuální stav
 - Výstupem funkce je nový stav aplikace
 
---

### Elm architektura

#### View
    [lang=elm]
    view : Model -> Html Msg
    view model =
    ...

 - Funkce přebírající aktuální stav
 - Výstupem funkce je Html, tedy výstup pro aktuální stav aplikace
 - Uživatel ve výstupu může vygenerovat **Message**

---

### Elm architektura

![alt Architektura](https://pbs.twimg.com/media/DYImH4mW4AA0SHe.jpg "Architektura") 

***

### Workflow
1. Výchozí stav aplikace
2. Vykreslení view pro výchozí stav
3. Uživatel např. stiskne tlačítko => vygeneruje se Message
4. Update přebere Message a aktualizuje stav
5. View se překreslí pro nový stav
6. atd. 
 
***

### Návrh aplikace
 - Model - popíšeme si, jak bude vypadat stav aplikace
 - Messages - nadefinujeme si možné akce, které mohou stav změnit
 - Update - definujeme si, jaký vliv bude mít která akce
 - View - popíšeme, co uživatel uvidí pro jaký stav
 
***

### Proč?
 - Udržitelnost aplikací
 - Jednodušší vývoj - např. debugging = procházení zpráv včetně historie atd.
 - Myšlenky přenositelné do ostatních jazyků - viz např. Redux v JS
 
***

### Děkuji za pozornost
***