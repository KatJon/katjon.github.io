---
layout: post
title:  "Category Theory 1 [PL]"
date:   2019-03-21 11:15:00 +0100
author: katjon
categories: category-theory
tags: category-theory, knsi, lambda
---
These are the notes from the meeting of Lambda section in the [Student Research Group KNSI][knsi]. They will be in Polish, but in the future I will translate them into English.

{% assign forall = "∀" %}
{% assign exists = "∃" %}
{% assign box = "∎" %}

[knsi]: https:/knsi-wppt.github.io


Wprowadzenie do Teorii Kategorii - spotkanie 1
===

Pojęcie kategorii
---

Kategorią nazywamy parę "kolekcji" (zauważmy, że nie mówię zbiór, bo w niektórych kategoriach mogą wystąpić kolekcje większe od zbioru np. w postaci zbioru wszystkich zbiorów) obiektów i morfizmów (strzałek) pomiędzy obiektami. Będziemy to oznaczać jako `C=(O,A)`, wtedy `Ob(C)=O` są obiektami, a `Arr(C)=A`. Każda strzałka ma swój początek i koniec, tzn. strzałka f ma początek w X i koniec w Y, co oznaczamy `f:X->Y`. Początek strzałki nazywamy dziedziną i piszemy `dom(f)=X`, a koniec przeciwdziedziną `cod(f)=Y`. Dodatkowo, istnieje operacja złożenia morfizmów `(.)` 

[](Dodać unicode'owy znak złożenia)

Aby taka para tworzyła kategorię, musi spełniać następujące prawa:

1. `{{forall}}X in Ob(C), {{exists}}id_X, ({{forall}}f:X->Y, f.id_X = f /\ {{forall}}g:Y->X, id_X.g = g)`

2. `{{forall}}X,Y,Z in Ob(C), {{forall}}f:X->Y, {{forall}}g:Y->Z, {{exists}}(g.f):X->Z`

Częstym problemem w zrozumieniu czym jest kategoria jest pytanie, czym są obiekty i strzałki? Odpowiedź na to pytanie może być trochę niezadowalająca, ale w kategorii wiemy jedynie, że obiekty i strzałki **są**. Traktujemy je podobnie jak zbiory w teorii mnogości - jako pojęcia pierwotne.

Przykłady kategorii
===

`Set`
---
Jest to kategoria zbiorów z funkcjami pomiędzy zbiorami. Ta kategoria jest bardzo ważną kategorią, ponieważ jest ona bliska naszym matematycznym intuicjom oraz wiele pojęć teoriomnogościowych daje się wyrazić jako pojęcia kategoryczne.

`(X,<=)`
---
Dla ustalonego zbioru X i relacji `<=`, która jest częściowym porządkiem, możemy zbudować kategorię, której obiektami będą elementy X. Kategoria ta jest o tyle ciekawa, że znaczenie strzałek jest następujące:
strzałka pomiędzy obiektami A i B istnieje, wtw. gdy `A≤B`.

Istotnie, konstrukcja ta jest kategorią, gdyż istnieje strzałka id_A (`A<=A`, ze zwrotności) oraz istnieje złożenie dwóch strzałek (`A<=B /\ B<=C => A<=C`, z przechodności).

<!-- <figure class="task">
Zadanie: Pokazać, że grupy z homomorfizmami grup tworzą kategorię (kategoria Grp).
</figure> -->

[](dodać więcej przykładów)

Izo-, mono- i epimorfizmy
===

Często chcemy pokazać, że dwa elementy są dla nas w jakimś sensie nierozróżnialne, pomimo, że są to istotnie różne elementy. Chcemy wtedy powiedzieć, że dwa obiekty są izomorficzne.

> **Def.** W teorii kategorii mówimy, że strzałka `f:X->Y` jest *izomorfizmem* oraz, że X i Y są izomorficzne, jeśli istnieje strzałka `g:Y->X`, taka, że  `f.g=id_Y /\ g.f=id_X`

> **Ćwiczenie:** Pokazać, że takie `g` jest jednoznaczne - oznaczmy je wtedy `f^{-1}` i nazywamy odwrotnością.

W teorii zbiorów mieliśmy dwie charakteryzacje "porządnych funkcji" - mianowicie surjekcje i injekcje czyli odpowiednio funkcje, których obraz jest równy przeciwdziedzinie i funkcje różnowartościowe. Teoriokategorycznymi odpowiednikami są epimorfizmy i monomorfizmy.

> **Def.** *Monomorfizmem* nazywamy strzałkę `f:X->Y`, taką, że dla dowolnego obiektu `Z` i dowolnych morfizmów `g,h:Z->X`, jeśli `f.g=f.h` to `g=h`.

> **Def.** *Epimorfizmem* nazywamy strzałkę `f:X->Y`, taką, że dla dowolnego obiektu `Z` i dowolnych morfizmów `g,h:Y->Z`, jeśli `g.f=h.f` to `g=h`.

{% include caption.html 
    src="/assets/img/epimorphism.jpg" 
    href="https://www.facebook.com/recreationaltypes/"
    caption="by Well-typed Constructivist Memes"
%}

```
Zadanie: Pokaż że złożenie monomorfizmów jest monomorfizmem.

Weźmy f:X->Y, g:Y->Z. Pokażmy, że g.f jest mono. 
Ustalmy więc obiekt W i morfizmy u,v:W->X.

Wtedy:

         (g.f).u = (g.f).v
        ------------------- (Assoc)
         g.(f.u) = g.(f.v) 
        ------------------- (g - mono)
             f.u = f.v 
            ----------- (f - mono)
               u = f
{{box}}
```

Elementy początkowe i końcowe 
---

Jak zobaczyliśmy w poprzednich konstrukcjach, teoria kategorii nie rozważa, czym są obiekty, a w jaki sposób są "połączone" z innymi obiektami. (*Można powiedzieć, że teoria mnogości mówi o tym, co to znaczy mieć, a teoria kategorii, jak być :D.*)

Często pojawiającym się schematem w teorii kategorii jest *konstrukcja uniwersalna*. Polega ona na wyszukaniu "wzorca" w całej kategorii (uniwersum), a następnie określeniu "rankingu" na znalezionych elementach. Konstrukcja tego typu jest pomocna, chociażby w przypadku próby zdefiniowania pojęcia zbioru pustego. W teorii mnogości, zbiór pusty, to zbiór, który nie zawiera żadnego elementu. Ale w teorii kategorii nie wolno nam zaglądać "do środka" zbiorów. Jedyne co mamy do dyspozycji, to obiekty i strzałki (które w kategorii `Set` są funkcjami). 

Z wstępu do logiki, możemy sobie przypomnieć, że ze zbioru pustego istnieje funkcja w dowolny inny zbiór (jeśli uda ci się dać mi jakiś element zbioru pustego, to dam ci element z przeciwdziedziny :v) - funkcja pusta. Dodatkowo, jest to jedyna taka funkcja. Widzimy, że jest to charakteryzacja wykorzystująca jednynie własności zewnętrzne obiektu. Możemy zastanawiać się, czy istotnie, opisuje ona jedynie zbiór pusty, jednak wiemy, że z żadnego innego obiektu nie istnieje strzałka do zbioru pustego, oraz że gdy mamy chociaż jeden element w dziedzinie, to istnieje co najmniej tyle funkcji ile wynosi moc przeciwdziedziny. 

Przenosząc powyższe rozumowanie na grunt teorii kategorii otrzymujemy definicję **obiektu początkowego**:

> **Def.** Obiekt `A` nazywamy początkowym, jeśli dla każdego obiektu `B`, istnieje dokładnie jedna strzałka `f:A->B`.

> **Ćwiczenie** Pokazać, że obiekty początkowe są wyznaczone jednoznacznie, z dokładnością do izomorfizmu.

Innym zbiorem, który często nas interesuje, jest singleton `{*}`. W tym wypadku, żaden zbiór (poza pustym) nie może narzekać na brak funkcji, których jest przeciwdzedziną. Jednak singleton ma tą własność, że istnieje *dokładnie* jedna funkcja z innego zbioru w singleton - funkcja stała. Zauważmy także, że działa to także dla dziedziny będącej zbiorem pustym (pokaż mi taką wartość ze zbioru pustego, która dawałaby wynik inny niż wartość singletonu :v). 

Sprawdźmy także, czy jakiś większy zbiór nie będzie miał takiej własności. Weźmy zbiór `B={T,F}`. Dla niepustej dziedziny, znamy co najmniej dwie różne funkcje: 
`t(x)=T` i `f(x)=F`. 

Przenosząc powyższe rozumowanie na grunt teorii kategorii otrzymujemy definicję obiektu końcowego:

> **Def.** Obiekt `A` nazywamy końcowym, jeśli dla każdego obiektu `B`, istnieje dokładnie jedna strzałka `f:B->A`.

> **Ćwiczenie** Pokazać, że obiekty końcowe są wyznaczone jednoznacznie, z dokładnością do izomorfizmu.

Oba pojęcia są do siebie bardzo podobne - definicje różnią się jedynie kierunkiem strzałek. Istotnie, powiązanie istnieje, ale omówimy je na późniejszych spotkaniach.

Wracając do konstrukcji uniwersalnej, dobrze byłoby pokazać ją w kontekście obiektów początkowych i końcowych. Naszym wzorcem będzie w tym wypadku pojedynczy obiekt, a rankingami: dla ob. początkowego "A jest lepsze od B, jeśli istnieje `f:A->B`", dla ob. końcowego "A jest lepsze of B, jeśli istnieje `f:B->A`". Możemy myśleć o tym, jako o mierze, jak blisko początku (odp. końca strzałki) obiekt może się znajdować.

Zmiany
---
* 02.04.19 - poprawienie literówek,  (K. Marek)
* 03.04.19 - dodanie literatury, drobne zmiany w układzie i typografii

Literatura
---
* Benjamin C. Pierce, *Basic Category Theory...* - rozdziały 1.1, 1.3, 1.4
* [Bartosz Milewski, *Categories great and small*](https://bartoszmilewski.com/2014/12/05/categories-great-and-small/)
