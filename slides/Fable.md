- title : Fable - client-side webové aplikace v F#
- description : Dají se v F# psát client-side webové aplikace? Ano, samozřejmě dají. A v této přednášce si ukážeme, jak na to pomocí Fable. Také se pokusíme odpovědět na pár otázek, které si v souvislosti s F# na webu můžete položit.
- author : Miroslav Veith
- theme : Blood
- transition : concave

***

## Fable
#### Client-side webové aplikace v F#
 
![alt FSharping](../images/fsharping_logo.png "FSharping")

###### [Miroslav Veith](https://twitter.com/miroveith)

***

### Web k volbám 2017

- [Volební model a predikce voleb MEDIAN](http://showme.median.cz/volby-2017/)
- Původně vytvořeno jako Shiny aplikace v jazyce R
    - problém už při desítkách uživatelů
- Předěláno na React aplikaci kompletně napsanou v F#, díky Fable
- Live predikce - FTP |> Azure Funkce |> F# kód |> Aktualizace webu

***

### Fable
#### F# |> BABEL

- F# kompilátor do JS 
- Hybrid .NET Core a node.js aplikace
- [Prerekvizity](http://fable.io/docs/getting-started.html)
    - dotnet SDK 2.0+
    - node.js 6.11+
    - yarn/npm
    - Paket (instaluje se s Fable.Template)
- v architektuře a přístupu došlo v poslední době k výrazným změnám, hlavně s verzí 1.0

---

### Fable
#### Sample1 - REPL: 
[Functions](http://fable.io/repl/#?code=let%20add%20x%20y%20%3D%20x%20%2B%20y%0A%0Alet%20add5%20%3D%20add%205%0A%0Alet%20isOdd%20x%20%3D%20x%20%25%202%20%3D%201%20%0A%0Alet%20isOddWith5%20%3D%20add5%20%3E%3E%20isOdd%0A%0Alet%20result%20%3D%205%20%7C%3E%20isOddWith5%0A%0Aprintfn%20%22%25b%22%20result)

[Option](http://fable.io/repl/#?code=let%20getDefaultValue%20x%20def%20%3D%0A%20%20match%20x%20with%0A%20%20%7C%20Some%20v%20-%3E%20v%0A%20%20%7C%20None%20-%3E%20def%0A%20%20%0Alet%20testMap%20x%20%3D%20Option.map%20(fun%20v%20-%3E%20v%20*%202)%20x%0A%20%20%20%20%0Alet%20result1%20%3D%20getDefaultValue%20(Some%201)%205%0Alet%20result2%20%3D%20getDefaultValue%20None%205%0Alet%20result3%20%3D%20testMap%20(Some%203)%0Alet%20result4%20%3D%20testMap%20None%0A%20%20%0Aprintfn%20%22%25i%22%20result1%0Aprintfn%20%22%25i%22%20result2%0Aprintfn%20%22%25A%22%20result3%0Aprintfn%20%22%25A%22%20result4)

---

### Fable

#### Fable.Template
 - nejjednodušší způsob, jak začít s Fable projektem 

<br />
<br />
#### Sample2 - Template: 

    [lang=powershell]
    dotnet new -i Fable.Template
    dotnet new fable -n FableApp
    cd FableApp
    
    # Check README
    
    yarn install # JS dependencies
    dotnet restore # F# dependencies

    cd src
    dotnet fable yarn-start # script in package.json

    # http://localhost:8080/


***

### IDE
 - VS Code + Ionide
 - Atom + Ionide
 - Visual Studio
 - Visual Studio for Mac
 - Emacs + fsharp-mode
 - Rider

--- 

### VS Code + Ionide
###### Sample3 - VS Code
 - F# interactive
 - .fsproj
 - navigace
 - hot reloading

***

### Debugging
 - generování code maps
 - debugging např. v Chrome Dev Tools

<br />
<br />
###### Sample4 - debugging

***

### JS Interop
 - ekosystém JavaScriptu je obrovský a byla by škoda se o něj ochudit
 - navíc samozřejmě ne všechno už je do Fable "přeloženo"
 - JS část Fable pracuje s Webpackem a jako package manager používá yarn nebo npm
 - [F# Interop with Javascript in Fable: The Complete Guide](https://medium.com/@zaid.naom/f-interop-with-javascript-in-fable-the-complete-guide-ccc5b896a59f)

---

#### JS Interop - existující bindings pro JS knihovny
 - například pro React - Fable.React
 - https://github.com/fable-compiler/fable-react

---

#### JS Interop - konverze deklaračních souborů pro TypeScript
 - existuje projekt ts2fable
 - https://github.com/fable-compiler/ts2fable
 
---

#### JS Interop - POJO 
 - createObj
 - rozhranní a createEmpty
 - atribut `[<Global>]` a jsNative
 - atribut `[<Emit>]`
 - jsObject
 
---

#### Sample5 - custom binding
 - Chart.js
 - nepříliš funkcionální přístup původní knihovny
 - wrapper využívající síly F#

 
***

### F# knihovny
 - Fable aplikace umí pracovat s F# projekty
 - .NET Core část používá Paket jako package manager
 - má to samozřejmě určitá omezení
 
***

### Testování
 - Testujeme F# kód pomocí F# (.NET) nástrojů
 - Expecto
 
***

### Prohlížeče
 - Funguje vše, kromě IE
 
***

### Vývoj webu v F#?
 - funkcionální přístup se prosazuje víc a víc:
    - React.js - funkcionální UI
    - Redux.js - funkcionální správa stavu
    - ClojureScript - Clojure kompilovaný do JS
    - Elm - funkcionální jazyk pro tvorbu webových aplikací (také kompilovaný do JS)
 
***

### Fable.Elmish
 - inspirace v Elmu - "model view update" architektura
 - postaveno na Fable a využívá React
 - aktuálně doporučený způsob, jak vytvářet Single Page Applications
 - Sample6 - [Fable.Template.Elmish.React](https://github.com/fable-elmish/templates)
 
***

### [SAFE-Stack](https://safe-stack.github.io/)
 - End-to-end F# stack pro web development
 - S - Suave
 - A - Azure
 - F - Fable
 - E - Elmish
 
***

### Komunita a materiály
 - Dokumentace - [http://fable.io/docs/](http://fable.io/docs/)
 - Twitter - [@FableCompiler](https://twitter.com/fablecompiler), [@safe_stack](https://twitter.com/safe_stack), [@alfonsogcnunez](https://twitter.com/alfonsogcnunez)
 - FableConf 2017
 - Kniha: Mastering F# - Alfonso García-Caro Núñez, Suhaib Fahad
    - kapitola věnovaná Fable, ale před verzí 1.0
 - [Awesome Fable](https://github.com/kunjee17/awesome-fable)
 
***

### Děkuji za pozornost
***