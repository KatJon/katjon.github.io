---
layout: post
title:  "Category Theory 2.5 [PL]"
date:   2019-04-15 11:15:00 +0100
author: katjon
categories: category-theory
tags: category-theory, knsi, lambda
---
Short second (and half) meeting of Lambda section of KNSI Research Group.

Wprowadzenie do Teorii Kategorii - spotkanie 2.5
===
{% assign forall = "∀" %}
{% assign exists = "∃" %}
{% assign in = "∈" %}
{% assign box = "∎" %}
{% assign pi = "π" %}

Na poprzednich spotkaniach poruszaliśmy temat konstrukcji uniwersalnej. Dzisiaj postaram się pokazać bardziej formalne przedstawienie "kategorycznej wyszukiwarki".

Konstrukcja uniwersalna
===

Przypomnijmy sobie, pojęcia obiektu początkowego i końcowego:

> **Def.** Obiekt `A` nazywamy początkowym, jeśli dla każdego obiektu `B`, istnieje dokładnie jedna strzałka `f:A->B`.

> **Def.** Obiekt `A` nazywamy końcowym, jeśli dla każdego obiektu `B`, istnieje dokładnie jedna strzałka `f:B->A`.

Konstrukcja uniwersalna polega na stworzeniu nowej kategorii, w której będziemy szukać elementu końcowego (analogicznie konstrukcja kouniwersalna polega na szukaniu elementu początkowego).

Zacznijmy od przykładu - konstrukcji produktu.

Przypomnijmy, co chcemy osiągnąć: 

> **Def.** **Produktem** obiektów `A` i `B` nazywamy obiekt `AxB`, taki, że dla dowolnego `(X, f:X->A, g:X->B)` poniższy diagram komutuje:
> {% include caption.html src="/diagrams/CT-2/product.png" %}

Tworzymy więc kategorię "klinów" `C'`, której obiektami są `(X,f:X->A,g:X->B)`, a `C'`-strzałka `h:(X,f:X->A,g:X->B)->(Y,i:Y->A,j:Y->B)` istnieje, gdy istnieje `C`-strzałka (strzałka w kategorii C) `m:X->Y`, t. że `f=i.m /\ g=j.m`.

```
Sprawdźmy, że istotnie C' jest kategorią. 
Identyczność otrzymujemy za darmo, bo istnienie 
C'-strzałki h:(X,f,g)->(X,f,g) wynika z istnienia 
strzłki identycznościowej w C - id_X.

Złożenie strzałek także jest poprawne, bo jeśli są
h:(X,f:X->A,g:X->B)->(Y,i:Y->A,j:Y->B)
k:(Y,i:Y->A,j:Y->B)->(Z,l:Z->A,n:Z->B)

to istnieje k.h, bo istnieją m1:X->Y i m2:Y->Z, t. że 

f = i.m1 /\ g = j.m1
i = l.m2 /\ j = n.m2

więc 

f = l.(m2.m1) /\ g = n.(m2.m1)

więc poszukiwaną strzałką m':X->Z jest m'=m2.m1
{{box}}
```

Wyznaczmy więc w tej kategorii obiekt końcowy. Jeśli istnieje, to będzie to trójka `(P,l:P->A,r:P->B)`, taka, że, dla każdego klina `(X,f:X->A,g:X->B)` istnieje dokładnie jedna strzałka `h:(X,f:X->A,g:X->B)->(P,l:P->A,r:P->B)` (a stąd `m:X->P`), t.że `f=l.m /\ g=r.m`.

Jak widzimy, jest to dokładnie nasza oczekiwana definicja produktu.

Jednoznaczne strzałki w konstrukcji uniwarsalnej nazywamy strzałkami mediacyjnymi (więc jest to nazwa szersza niż tylko dla produktu).

W przyszłości, prawdopodobnie omówimy jeszcze kilka pojęć wykorzystujących konstrukcję uniwersalną. Zwykle, gdy widzimy, że ma istnieć dokładnie jedna strzałka, możemy przypuszczać, że stoi za tym pewna konstrukcja uniwersalna.

Uwagi
---
* Strzałka pomiędzy klinami (`h:(X,f:X->A,g:X->B)->(Y,i:Y->A,j:Y->B)`), jest niejako zanurzeniem strzałki `m:X->Y` w kategorii C' - wskazaniem strzałki o porządanych właściwościach.

Literatura
---
* Benjamin C. Pierce, *Basic Category Theory...* -- rozdział 1.6
