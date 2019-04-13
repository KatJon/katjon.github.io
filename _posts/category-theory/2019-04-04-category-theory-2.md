---
layout: post
title:  "Category Theory 2 [PL]"
date:   2019-04-04 11:15:00 +0100
author: katjon
categories: category-theory
tags: category-theory, knsi, lambda
---
Second meeting of Lambda section of KNSI Research Group.

Wprowadzenie do Teorii Kategorii - spotkanie 2
===
{% assign forall = "∀" %}
{% assign exists = "∃" %}
{% assign in = "∈" %}
{% assign box = "∎" %}
{% assign pi = "π" %}

Na poprzednim spotkaniu omówiliśmy podstawowe konstrukcje teoriokategoryczne. Dzisiaj skupimy się na pokazaniu konstrukcji produktu oraz poznamy symetrię pojęć w teorii kategorii.

Produkt
---

W teorii mnogości bardzo ważną konstrukcją jest produkt kartezjański, definiowany jako

> `AxB = {(a,b): a{{in}}A, b{{in}}B}`

Jednak nas, jako teoriokategorystów, taka definicja bardzo smuci, ponieważ jest wyrażona całkowicie przez *elementy* zbiorów A i B. Jak przekonaliśmy się na poprzednim spotkaniu, w języku kategorii nie możemy tego wyrazić. Jednak z pomocą przychodzą dwie funkcje: `{{pi}}_A: AxB->A` i `{{pi}}_B: AxB->B` - projekcje "na osi".

Ustalmy obiekty A i B. Chcemy uzyskać kategoryczną definicję produktu AxB. Rozważmy zatem trójki `(X,f:X->A,g:X->B)`. Korzystając z konstrukcji uniwersalnej, budujemy ranking na takich trójkach: mówimy, że `(X,f:X->A,g:X->B)` jest lepsze od `(Y,i:Y->A,j:Y->B)`, gdy istnieje strzałka `h:Y->X`, taka, że `i = f.h /\ j = g.h`.

> **Def.** **Produktem** obiektów `A` i `B` nazywamy obiekt `AxB`, taki, że dla dowolnego `(X, f:X->A, g:X->B)` poniższy diagram komutuje:
> {% include caption.html src="/diagrams/CT-2/product.png" %}
> Diagram rozumiemy w ten sposób, że dla trójki `(X, f:X->A, g:X->B)` istnieje dokładnie jedna strzałka `h:X->AxB`, taka, że `{{pi}}_A.h=f` i `{{pi}}_B.h=g`.
>
> Kiedy `AxB` jest produktem, to taką strzałkę `h:X->AxB` nazywamy strzałką mediacyjną.

W kategorii **`Set`** strzałka mediacyjna ma postać `<f,g>`, która definiowana jest jako

> `<f,g>(x)=(f(x),g(x))`

Kategoria dualna
---
Ustalmy kategorię `C`. Zbudujmy kategorię `C^{op}`, w następujący sposób: obiektami `C^{op}` są obiekty `C`, a morfizm `f:Y->X` istnieje w `C^{op}`, jeśli `f:X->Y` jest morfizmem w `C`. Intuicyjnie - odwracamy kierunek strzałek. 

Pokażmy, że istotnie, C^{op} jest kategorią. Zdefiniujmy najpierw czym jest złożenie w `C^{op}` 

> `(w C^{op}) f * g = g . f (w C)`

Pokażmy, że złożenie jest łączne

> `f*(g*h) = f*(h.g) = (h.g).f = h.(g.f) = h.(f*g) = (f*g)*h`

Strzałka identycznościowa istnieje trywialnie.

Wobec tego `C^{op}` jest istotnie porządną kategorią.

Dualność
---

Na poprzednim spotkaniu mówiliśmy o elementach początkowych i końcowych. Przypomnijmy definicje:

> **Def.** Obiekt `A` nazywamy początkowym, jeśli dla każdego obiektu `B`, istnieje dokładnie jedna strzałka `f:A->B`.

> **Def.** Obiekt `A` nazywamy końcowym, jeśli dla każdego obiektu `B`, istnieje dokładnie jedna strzałka `f:B->A`.

Definicje te są do siebie bardzo zbliżone. Różnią się jedynie kierunkiem strzałki pomiędzy obiektami B i A. 

Pozwala nam to sformułować następujący wniosek:

> Obiekt początkowy w kategorii C, jest obiektem końcowym w kategorii C^{op}.

Pojęcia które są związane przez wyrażenie konstrukcji w kategorii odwrotnej, nazywamy **pojęciami dualnymi**.

Koprodukt
---

Wyraźmy więc pojęcie dualne do pojęcia produktu.

Oczekujemy, że będzie komutował następujący diagram:
{% include caption.html src="/diagrams/CT-2/coproduct.png" %}

> **Def.** **Koproduktem** obiektów `A` i `B`, nazywamy trójkę `(A+B,i_A,i_B)`, taką, że dla dowolnej trójki `(X,f,g)` istnieje dokładnie jedna strzałka `y:A+B->X`, taka, że `f = y.i_A /\ g = y.i_B`.

W kategorii Set koprodukt odpowiada sumie rozłącznej zbiorów, a "strzałka komediacyjna" funkcji, która trzyma parę funkcji - `[f,g]` i aplikuje odpowiednią, w zależności, element z którego zbioru otrzymała.

Literatura
---
* Benjamin C. Pierce, *Basic Category Theory...* -- rozdziały 1.4, 1.5
* [Bartosz Milewski, *Products and Coproducts*](https://bartoszmilewski.com/2015/01/07/products-and-coproducts/)
