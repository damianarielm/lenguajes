% Funciones Recursivas 
% Pablo Verdes. LCC.
% 9 de Abril de 2019.

------------------------------------

### Contenidos ###

- *Motivacion*: Las FRP no alcanzan.
  - Funciones parciales y totales.
  - Relacion entre FRP y funciones totales.
  - La funcion de Ackermann.
- *Nuevo operador*: Minimizador.
- *Funciones recursivas*: Definicion.
- *Tesis de Church*.

------------------------------------

###### Las FRP no alcanzan ######

- *Definicion*: Una funcion numerica $f:\mathbb{N}^k \to \mathbb{N}$ se dice *parcial* si no esta definida sobre todos los elementos de $\mathbb{N}^k$. Ejemplos:
  - La funcion:

    $$
       \begin{aligned}
         f : \mathbb{N} & \to \mathbb{N} \\
                      n & \mapsto f(n) = n/3
       \end{aligned}
    $$

    solo esta definida en $n=0,3,6,9,12,15,\ldots$
  - La funcion:

    $$
      \begin{aligned}
        f : \mathbb{N} & \to \mathbb{N} \\
                     n & \mapsto f(n) = \sqrt{n}
      \end{aligned}
    $$

    solo esta definida en $n=0,1,4,9,16,25,\ldots$
  - La funcion definida como: $f(0)=0, f(n+2)=f(n)+3$

------------------------------------

###### Las FRP no alzancan ######

- *Definicion*: Una funcion numerica $f:\mathbb{N}^k \to \mathbb{N}$ se dice *total* si esta definida sobre todos los elementos de $\mathbb{N}^k$.
- *Teorema*: Si $f\in FRP$ entonces $f$ es una funcion total.  
  *Demostracion*: Por induccion sobre el conjunto FRP.
  - *Caso base*: Trivial. Las funciones base $c^{(k)},p_i^{(k)}$ y $s^{(1)}$ son totales.
  - *Composicion*: Supongamos que $f^{(n)},g_1^{(k)},\ldots,g_n^{(k)}$ son totales y veamos que
    $$h=\phi(f,g_1,g_2,\ldots,g_n)$$

    tambien es total. Dado $X\in \mathbb{N}^k$, podemos calcular

    $$Y=(g_1(X),g_2(X),\ldots,g_n(X))$$

    pues cada $g_i$ es total (H.I.). Como $f$ es total en $\mathbb{N}$, podemos tambien calcular $f(Y)$. Por lo tanto, $\exists z\in\mathbb{N}$ tal que $z=F(Y)=h(X)$. Dado que $\forall X\in\mathbb{N}^k \exists h(X)$, concluimos que $h$ es una funcion total.
  - *Recursion*: Ejercicio 1, Practica 4.

---------------------------------------

###### Las FRP no alcanzan ######

- En otras palabras, acabamos de probar que

  $$FRP\subseteq\{f / f \text{ es funcion total}\}$$

- Es decir, las FRP no pueden representar funciones parciales.
- Consideremos la pregunta inversa: ¿Sera que todas las funciones totales son FRP? Es decir, ¿sera cierto que $f$ total $\Rightarrow f\in FRP$?
- La respuesta es no: veremos a continuacion la funcion de Ackermann, que es total pero no recursiva primitiva.
- Para demostrar que dicha funcion no es FRP, la estrategia sera demostrar que todas las FRP cumplen cierta propiedad, mientras que la funcion de Ackermann no la cumple.
- Resumiendo, las FRP no pueden representar a:
  - Ninguna funcion parcial.
  - Todas las funciones totales.

---------------------------------------

###### Las FRP no alcanzan ######

- Deciamos que vamos a demostrar que cierta funcion (la llamada de Ackermann) no es FRP mostrando que:
  - Todos los elementos del conjunto FRP satisfacen cierta propiedad.
  - La funcion de Ackermann no la satisface.
- En terminos coloquiales, dicha propiedad sera la siguiente:

. . .

  > Ser mayorado por algun elemento de la sucesion de Ackermann

- Para formalizar este argumento, a continuacion definimos:
  - La sucesion (o serie) de Ackermann, $\{ f_k(x) \}_{k\in\mathbb{N}}$.
  - La funcion de Ackermann, $ACK(x)$.
  - El concepto "$f$ mayora a $g$", que indicaremos $f \uparrow g$.  
- Luego demostraremos:
  1. $g\in FRP \Rightarrow \exists k\in\mathbb{N} / f_k \uparrow g$.
  2. $\nexists k\in\mathbb{N} / f_k \uparrow ACK$.

---------------------------------------

###### Sucesion (o serie) de Ackermann ######

- Consideremos la siguiente sucesion de funciones, que llamaremos *sucesion (o serie de Ackermann)*:

  $$
    \begin{aligned}
      f_0(x) = & s(x)=x+1 \\
      f_1(x) = & f_0^{x+2}(x)=s^{x+2}(x)=x+(x+2)=2x+2 \\
      f_2(x) = & f_1^{x+2}(x) \\ \vdots \\ 
      f_k(x) = & f_{k-1}^{x+2}(x) \\ \vdots
    \end{aligned}
  $$

- Para ver mejor como funciona, calculemos algunos valores de $f_2(x)$:
  - $f_2(0) = f_1^2(0) = (2(2x+2)+2)|_{x=0}=6$.
  - $f_2(1) = f_1^3(1) = (2(2(2x+2)+2)+2)|_{x=1}=6$.
  - $f_2(2) = f_1^4(2) = (2(2(2(2x+2)+2)+2)+2)|_{x=2}=6$.

---------------------------------------

###### Funcion de Ackermann ######

- *Propiedades*:
  - $\forall k\in\mathbb{N} : f_k(x)\in FRP$
  - $\forall x,k\in\mathbb{N} : f_k(x)>x$
  - $\forall x_1,x_2,k\in\mathbb{N}: x_1 < x_2 \Rightarrow f_k(x_1) < f_k(x_2)$
  - $\forall x,k\in\mathbb{N} : f_k(x) < f_{k+1}(x)$
- *Demostracion*: Ejercicio 2, Practica 4.
- *Definicion*: Funcion de Ackermann

  $$ACK(x)=f_x(x)$$

  Calculemos algunos valres en el pizarron.

---------------------------------------

###### Funcion de Ackermann ######

- *Definicion*: Decimos que una funcion $f^{(1)}$ *mayora* a otra funcion $g^{(n)}$ si $\forall (x_1,x_2,\ldots,x_n)\in\mathbb{N}$ se verifica que:
  $$g(x_1,x_2,\ldots,x_n)\leq f(\max \{ x_1,x_2,\ldots,x_n \})$$
  *Notacion*: $f^{(1)} \uparrow g^{(n)}$.

1. *Teorema*: Sea $g^{(n)}\in FRP$, entonces existe $f_k$ de la sucesion de Ackermann tal que $f_k \uparrow g$.
   *Demostracion*: Por induccion en $g$. No la hacemos en clase (ver el libro *Temas de Teoria de la Computacion, Proyecto LATIn, pag. 56*).
2. *Teorema*: $ACK(x)\notin FRP$.
   *Demostracion*: Por el absurdo, supongamos que $ACK(x)\in FRP$.
   Luego $ACK(x)+1 \in FRP$. Por el teorema anterior, existe $f_M$ en la sucesion de Ackermann que la mayora:
   $$
     \begin{aligned}
       \forall x\in\mathbb{N}: ACK(x)+1 & \leq f_M(x) \\
       \forall x\in\mathbb{N}: f_x(x)+1 & \leq f_M(x) \\
               x=M \Rightarrow f_M(M)+1 & \leq f_M(M) \text{ Absurdo!}
     \end{aligned}
   $$
   Por lo tanto $ACK(x)\notin FRP$.

---------------------------------------

###### Operador Minimizador M ######

- Con la intencion de completar nuestro modelo de calculo, agregamos un nuevo operador.
- *Definicion*: Operador Minimizador M.
  Dada $h^{(n+1)}$, decimos que $g^{(n)}$ se construye por minimizacion de $h$ (y lo notaremos $g=M[h]$) cuando $g$ se define del modo siguiente:

  $$g(X)=M [h] (X) = \mu_{t} (h(t,X)=0)$$

  donde $\mu_t (h(t,X)=0)$ es, si existe, el minimo valor de $t$ tal que $h(t,X)=0$.
- Observacion: Nada garantiza que tal valor de $t$ exista. Por lo tanto, las funciones construidas con el operador M pueden ser parciales.

---------------------------------------

###### Ejemplos ######

- La funcion *cociente* $C(x,y)=x/y$, que solo esta definida si existe $t$ tal que

  $ty=x$: $C(x,y)=\mu_t (h(t,x,y)=0)$ donde $$h(t,x,y)=(ty \dot{-} x)+(x \dot{-} ty)$$

- La funcion *logaritmo* $\log(x,y)=\log_x(y)$, que solo esta definida si existe $t$ tal que $x^t=y$: $\log(x,y)=\mu_t (h(t,x,y)=0)$ donde

  $$h(t,x,y)=(x^t \dot{-} y)+(y \dot{-} x^t)$$

- La funcion *raiz enesima* $Rad(x,n)=\sqrt[n]{x}$, que solo esta definida si existe $t$ tal que $t^n=x$: $Rad(x,n)=\mu_t (h(t,x,y)=0)$ donde

  $$h(t,x,y)=(t^n \dot{-} x)+(x \dot{-} t^n)$$

::: notes
- Realizar traza en el pizarron.
- Alertar sobre casos extremos. La funcion C falla en (0,0).
:::

---------------------------------------

###### Pseudocodigo ######

. . .

La siguiente analogia muestra como dada $h^{(n+1)}$, podemos pensar a $g=M[h]$ como un programa:

. . .

```python
def g(X):
  t = 0
  while (h(t,X) != 0):
    t += 1
  return t
```

---------------------------------------

###### Funciones Recursivas ######

- *Definicion*: Definimos inductivamente el conjunto de *Funciones Recursivas (FR)* como el menor conjunto tal que:
  - Las funciones base pertenecen a FR.
  - Las funciones obtenidas aplicando un numero finito de operaciones de composicion ($\phi$), recursion ($R$) y minimizacion ($M$) sobre elementos de FR tambien pertenecen a FR.
- Observemos que $FRP \subset FR$.
- Se extiende la propiedad de ser *revursivos* a conjuntos y relaciones de manera analoga a como se hizo para la recursion primitiva.
- Todos los mecanismos que permiten construir elementos nuevos de FRP, CRP y RRP a partir de otros elementos pueden ser extendidos al caso de FR, CR y RR.

---------------------------------------

###### Tesis de Church ######

- ¿Hara falta introducir algun operador mas?
- La *Tesis de Church* afirma que el conjunto de las FR coincide con el de las funciones "calculables".
- Por funcion "calculable" entendemos una funcion para la cual podemos, en principio, obtener el valor de la imagen de cualquier elemento de su dominio mediante un algoritmo. (Esto no significa que efectivamente podamos realizar el calculo pues podria haber limitaciones de tiempo y espacio).
- Observemos que no es posible demostrar la Tesis de Church, pues la definicion de funcion "calculable" es intuitiva pero no rigurosa.
- Sin embargo, en la busqueda de otros posibles modelos para el calculo (que estudiaremos en la materia) no se ha encontrado ningun algoritmo que no pueda ser representado como una FR.
