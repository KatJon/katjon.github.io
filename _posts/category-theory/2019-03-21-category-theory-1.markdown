---
layout: post
title:  "Category Theory 1 [PL]"
date:   2019-03-21 11:15:00 +0100
author: katjon
categories: category-theory
tags: category, theory, knsi, lambda
---

These are the notes from the meeting of Lambda section in the [Student Research Group KNSI][knsi]. They will be in Polish, but in the future I will translate them into English.

[knsi]: https:/knsi-wppt.github.io


Wprowadzenie do Teorii Kategorii - spotkanie 1
===

Pojęcie kategorii
---

Kategorią nazywamy parę "kolekcji" (zauważmy, że nie mówię zbiór, bo w niektórych kategoriach mogą wystąpić kolekcje większe od zbioru np. w postaci zbioru wszystkich zbiorów) obiektów i morfizmów (strzałek) pomiędzy obiektami. Będziemy to oznaczać jako `C = (O, A)`, wtedy `Ob(C) = O` są obiektami, a `Arr(C) = A`. Każda strzałka ma swój początek i koniec, tzn. strzałka f ma początek w X i koniec w Y, co oznaczamy `f:X -> Y`. Początek strzałki nazywamy dziedziną i piszemy `dom(f) = X`, a koniec przeciwdziedziną `cod(f) = Y`. Dodatkowo, istnieje operacja złożenia morfizmów `(.)` 

[](Dodać unicode'owy znak złożenia)

Aby taka para tworzyła kategorię, musi spełniać następujące prawa:

1. `∀X in Ob(C), ∃id_X, ∀f, id_X.f = f.id_X = f`

2. `∀X,Y,Z in Ob(C), ∀f:X->Y, ∀g:Y->Z, ∃(g.f):X->Z`

Częstym problemem w zrozumieniu czym jest kategoria jest pytanie, czym są obiekty i strzałki? Odpowiedź na to pytanie może być trochę niezadowalająca, ale w kategorii wiemy jedynie, że obiekty i strzałki **są**. Traktujemy je podobnie jak zbiory w teorii mnogości - jako pojęcia pierwotne.

Przykłady kategorii
===

`Set`
---
Jest to kategoria zbiorów z funkcjami pomiędzy zbiorami. Ta kategoria jest bardzo ważną kategorią, ponieważ jest ona bliska naszym matematycznym intuicjom oraz wiele pojęć teoriomnogościowych daje się wyrazić jako pojęcia kategoryczne.

`(X, ≤)`
---
Dla ustalonego zbioru X i relacji ≤, która jest częściowym porządkiem, możemy zbudować kategorię, której obiektami będą elementy X. Kategoria ta jest o tyle ciekawa, że znaczenie strzałek jest następujące:
strzałka pomiędzy obiektami A i B istnieje, wtw. gdy `A ≤ B`.

Istotnie, konstrukcja ta jest kategorią, gdyż istnieje strzałka id_A (`A ≤ A`, ze zwrotności), oraz istnieje złożenie dwóch strzałek (`A ≤ B /\ B ≤ C => A ≤ C`, z przechodności).

<!-- <figure class="task">
Zadanie: Pokazać, że grupy z homomorfizmami grup tworzą kategorię (kategoria Grp).
</figure> -->

[](dodać więcej przykładów)

Izo-, mono- i epimorfizmy
===

Często chcemy pokazać, że dwa elementy są dla nas w jakimś sensie nierozróżnialne, pomimo, że są to istotnie różne elementy. Chcemy wtedy powiedzieć, że dwa obiekty są izomorficzne.

> **Def.** W teorii kategorii mówimy, że strzałka `f:X->Y` jest *izomorfizmem* oraz, że X i Y są izomorficzne, jeśli istnieje strzłka `g:Y->X`, taka, że  `f.g=id_Y /\ g.f=id_X`

> **Ćwiczenie:** Pokazać, że takie `g` jest jednoznaczne - oznaczmy je wtedy `f^{-1}` i nazywamy odwrotnością.

W teorii zbiorów mieliśmy dwie charakteryzacje "porządnych funkcji" - mianowicie surjekcje i injekcje czyli odpowiednio funkcje, których obraz jest równy przeciwdziedzinie i funkcje różnowartościowe. Teoriokategorycznymi odpowiednikami są epimorfizmy i monomorfizmy.

> **Def.** *Monomorfizmem* nazywamy strzałkę `f:X->Y`, taką, że dla dowolnego obiektu `Z` i dowolnych morfizmów `g,h:Z->X`, jeśli `f.g = f.h` to `g = h`.

> **Def.** *Epimorfizmem* nazywamy strzałkę `f:X->Y`, taką, że dla dowolnego obiektu `Z` i dowolnych morfizmów `g,h:Y->Z`, jeśli `g.f = h.f` to `g = h`.

{% include caption.html 
    src="/assets/img/epimorphism.jpg" 
    href="https://www.facebook.com/recreationaltypes/"
    caption="by Well-typed Constructivist Memes"
%}
