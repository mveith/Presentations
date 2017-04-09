- title : F# a interaktivní programování
- description : F# for Kiwi/Fenix team
- author : Miroslav Veith
- theme : night
- transition : default

***

### F# a interaktivní programování

***

### Funkcionální jazyk

---

#### Imutabilita by default 
 - game changer
    - vyžaduje trošku změnu přemýšlení
 - mnohem lepší vícevláknové programování
 - stav aplikace nemůže být roztahaný v miliardě tříd, ale musí být nějakým způsobem izolovaný a přehledný
 - když člověk překoná počáteční bariéru, zjistí, že mu to neuvěřitelně ulehčuje život

---

#### Side effect free

 - sladký život
 - něco někam pošlu a vím, že se mi to nezměnilo
 - pure functions

---

#### Funkce jako first-class citizen

    // přebírá funkci (condition) a vrací funkci (list -> list)
    let where condition = List.filter condition
    
    //list od 1 do 10
    let list = [1..10]
    
    let isEven x = x % 2 = 0

    // částečná aplikace - definujeme parametr a pak už ho definovat nemusíme
    let onlyEven = where isEven
    
    // Pipeline - posílám list do onlyEven, odpovídá onlyEven list, 
    // ale má to logičtější směr
    let even = list |> onlyEven
    
    // skládání funkcí firstEven je funkce, která uvnitř parametr pošle do onlyEven, 
    // ta pošle výsledek do Seq.head a to je výsledek firstEven
    let firstEven = onlyEven >> Seq.head
    
    let x = list |> firstEven

***

### Multiparadigmatický jazyk
 - klíčové slovo mutable
 - interoperabilita se C#
 - možnost pracovat s rozhranními, třídami, práce s objekty...

***

### Výhody
 - jediný důvod proč používat jiný jazyk je, že v něm budu produktivnější a budu psát lepší kód

---

#### Méně zbytečností v kódu
    let square x = x * x
 - nemusím psát { }, () ani ; a ,
 - type inference - magic
    - je to stále silně typovaný jazyk, ale chytrý

---

#### Porovnávání podle obsahu
    // true
    let equals = [ 0; 1; 2; 3 ] = [ 0; 1; 2; 3 ]
 - by default - i u listů atd.

---

#### Pattern matching
    let list = [1;2;3]
    match list with 
    | [1;x;y] -> printfn "x=%A y=%A" x y
    | 1::tail -> printfn "tail=%A" tail 
    | [] -> printfn "empty"
    | _ -> printfn "default"
    
 - mnohem mocnější než switch a mnohem čistší než C# 7 pattern matching
 - kompilátor varuje o nepokrytých možnostech (je možné nastavit tvrději)
 
---

#### Neexistuje null
    // tryFind - když neexistuje, vrací None, když existuje, vrací Some x
    let find seq condition = seq |> Seq.tryFind condition

    let finded = find [ 1; 2; 3;] (fun x -> x > 2)
    
    // Nepůjde zkompilovat, protože Option<int> a int nejdou sčítat
    let x = finded + 3

 - existuje Option a kompilátor nám ani nedovolí udělat null chybu!

***

### Interaktivní programování
 - REPL - read-eval-print loop
 - píšu kód a rovnou spouštím a testuju funkce
 - u C# to není prakticky možné - všude je prolezlý stav, existuje velký strom závislých objektů atd.
 - ukázka řekne víc...

***

### Interoperabilita
 - z F# se dá volat C# kód - což by ani jinak nešlo, protože se používá klasická C# BCL
 - ze C# se ale dá volat také F# kód
    - protože C# je objektový, má na F# trošku požadavků
    - klasické F# moduly jsou statické třídy
    - v F# používají trošku jiné konvence, takže tam, kde se má volat ze C# je vhodné použít C# konvence atd.
 - některé věci nejdou úplně hladce - listy v F# jsou jiné než v C#, také tuply atd.
 - tyhle rozdíly se pokoušejí zmenšovat v dalších verzích

***

### Nevýhody
 - nabízí se říct, že žádné nejsou
 - ona je pravda, že nejsou, ale na počátku se to může zdát jinak

---

### Nevýhoda?
#### Funkcionální přístup vyžaduje trošku změnu myšlení
 - imutabilita
 - pure functions
 - izolace stavu
 - atd.

> Za mě výhoda - vyplatí se to myšlení změnit

---

### Nevýhoda?
#### Funkcionální programování má z nějakého důvodu nesmyslnou pověst, že je pro matematiky atd., což spoustu lidí odradí

> Pomluva, ne nevýhoda...

---

### Nevýhoda?
#### FP připomíná lidem LISP, Prolog apod., kterými je někdo (nějaký vůl) trápil ve škole

> Za mě spíš problém těch, co to vyučují, ne FP

---

### Nevýhoda?
#### Není to tak rozšířené

> Možná o to akčnější komunita kolem a o zdroje nebo příklady vážně není nouze

---

### Nevýhoda
#### U některých věcí se to nepoužívá tak snadno jako C# z jejich principu - např. WPF, kde se třeba s mutabilitou hodně počítá

> Většinou ale existuje alternativa a vždy je možné využít interoperatbilitu se C# - vhodný nástroj na vhodný problém...

***

### Děkuji za pozornost

![Thanks](https://media.giphy.com/media/yoJC2El7xJkYCadlWE/giphy.gif)

***