% Funciones Recursivas
% Pablo Verdes. LCC.
% 9 de Abril de 2019.

------------------------------

# Contenidos #

- *Motivacion*: Las FRP no alcanza.

  - Funciones parciales y totales.

  - Relacion entre FTP y funciones totales.

  - La funcion de Ackermann.

- *Nuevo operador*: Minimizador.

- *Funciones recursivas*: Definicion.

- *Tesis de Church*.

------------------------------

## Las FRP no alcanzan ##

- *Definicion*: Una funcion numerica f : ℕᵏ → ℕ se dice *parcial* si no esta definida sobre todos los elementos de ℕᵏ. Ejemplos:

  - La funcion:

    ------ ------------
     f : ℕ → ℕ
         n ↦ f(n) = n/3
    ------ ------------

    solo esta definida para n ∈ {0, 3, 6, 9, 12, 15, ...}.

  - La funcion:

     ------ ------------
      f : ℕ → ℕ
          n ↦ f(n) = √n
     ------ ------------

    solo esta definida para n ∈ {0, 1, 4, 9, 16 , 25, ...}.

  - La funcion definida como: f(0) = 0; f(n + 2) = f(n) + 3.

------------------------------

## Las FRP no alcanzan ##

- *Definicion*: Una funcion numerica f : ℕᵏ → ℕ se dice *total* si esta definida sobre todos los elementos de ℕᵏ.
- *Teorema*: Si f ∈ FRP entonces f es una funcion total.
  *Demostracion*: Por induccion sobre el conjunto FRP.
  - *Caso base*: Trivial. Las funciones base c⁽ᵏ⁾, pᵢ⁽ᵏ⁾ y s⁽¹⁾ son totales.
  - *Composicion*: Supongamos que f⁽ⁿ⁾, g₁⁽ᵏ⁾, ..., gₙ⁽ᵏ⁾ son totales y veamos que

    --------------------------------
     h = ϕ(f, g₁, ..., gₙ) : ℕᵏ → ℕ
    --------------------------------

    tambien es total. Dado X ∈ ℕᵏ podemos calcular

    -------------------------
     Y = (g₁(X), ..., gₙ(X))
    -------------------------

    pues cada gᵢ es total (H.I.). Como f es total en ℕⁿ, podemos tambien calcular f(Y). Por lo tanto ∃ z ∈ ℕ tal que z = F(Y) = h(X). Dado que ∀ X ∈ ℕᵏ ∃ h(X), concluimos que h es una funcion total.

  - *Recursion*: Ejercicio 1, Practica 4.

------------------------------

## Las FRP no alcanzan ##

* En otras palabras, acabamos de probar que

  ----------------------------------
   FRP ⊆ { f | f es funcion total }
  ----------------------------------

* Es decir, las FRP no pueden representar funciones parciales.

* Consideremos la pregunta inversa. ¿Sera que todas las funcionestotales son FRP? Es decir, ¿sera cierto que f total ⇒ f ∈ FRP?

* La respuesta es no: veremos a continuacion la funcion de Ackermann, que es total pero no recursiva primitiva.

* Para demostrar que dicha funcion no es FRP, la estrategia sera demostrar que todas las FRP cumplen cierta propiedad, mientras quela funcion de Ackermann no la cumple.

* Resumiendo, las FRP no pueden representar a:

  * Ninguna funcion parcial.

  * Todas las funciones totales.

------------------------------------

## Las FRP no alcanzan ##

* Deciamos que vamos a demostrar que cierta funcion (llamada de Ackermann) no es FRP mostrando que:

  * Todos los elementos del conjunto FRP satisfacen cierta propiedad.

  * La funcion de Ackermann no la satisface.

* En terminos coloquiales, dicha propiedad sera la siguiente:

. . .

> Ser mayorado por algun elemento de la sucesion de Ackerman

. . .

* Para formalizar este argumento, a continuacion definiremos:

  * La sucesion (o serie) de Ackermann, { fₖ(x) } con k ∈ ℕ.

  * La funcion de Ackemann, ACK(x).

  * El concepto "f mayora a g", que indicaremos f ↑ g.

  . . .

  y demostraremos:

  . . .

  1. g ∈ FRP ⇒ ∃ k ∈ ℕ | fₖ ↑ g
  2. ∄ k ∈ ℕ | fₖ ↑ ACK

----------------------------------------

## Sucesion (o serie) de Ackermann

* Consideremos la siguiente sucesion de funciones, que llamaremos *sucesion (o serie) de Ackermann*:

  --------------------------------
   f₀(x) = s(x) = x + 1
  --------------------------------
