# Résumé des propriétés de la notation Big O
La notation Big O permet d'évaluer la complexité temporelle d'un algorithme en se concentrant sur le pire des cas, c'est-à-dire le scénario où l'algorithme prend le plus de temps à s'exécuter. Cette notation exprime la croissance de la durée d'exécution en fonction de la taille de l'entrée, permettant de déterminer comment l'algorithme se comporte lorsque la taille de l'entrée tend vers l'infini.

La notation Big O revient à trouver une fonction qui majorise (ou borne asymptotiquement) le temps d'exécution de l'algorithme, ce qui signifie qu'elle décrit la manière dont le temps de calcul augmente à mesure que la taille des données augmente, tout en négligeant les constantes et les termes de moindre importance.

## Définition
$\forall f(n), g(n), \qquad f(n) = O(g(n)) \Longleftrightarrow \exists c > 0, n_0 \in N \qquad$ tels que $\qquad \forall n \ge n_0, f(n) \le c * g(n)$


## Exemple
Considérons les fonctions $\qquad f : \mathbb{N} \rightarrow \mathbb{R}^+, \quad f(n) = n^2, \qquad$ et $\qquad g : \mathbb{N} \rightarrow \mathbb{R}^+, \quad g(n) = n^4$.<br>
Nous souhaitons montrer que $\qquad f(n) = O(g(n)) \iff \exists c > 0, n_0 \in \mathbb{N} \qquad$ tels que $\qquad \forall n \geq n_0, \quad f(n) \leq c * g(n)$.<br>
Cela revient à vérifier que $\qquad \forall n \geq n_0, \quad n^2 \leq c * n^4$.<br>
$\forall n > 0 \qquad$ on peut simplifier l'inégalité en divisant par $\quad n^2 \quad$: $\qquad 1 \le c * n^2$

**Pour que l'inégalité soit vérifiée, il faut que :**<br>
$\exists c > 0, n_0 \in \mathbb{N} \qquad$ tels que $\qquad \forall n \ge n_0, \quad 1 \le c * n^2$<br>
Il suffit de choisir une constante $\qquad c > 0 \qquad$ et $\qquad n_0 \qquad$ suffisamment grand tel que pour tout $\qquad n \ge n_0 \qquad$ l'inégalité soit vraie. Par exemple, si nous prenons $\qquad c = 1 \qquad$ il nous faut : $\qquad \forall n \ge 1, \quad 1 \le n^2$

Cette condition est vérifiée pour $n_0=1$, car pour tout $n \ge 1$, nous avons $n^2 \ge 1$.<br>
Donc, l'inégalité est vérifiée, et nous pouvons conclure que<br>
$f(n) = n^2$ est bien en $O(g(n))$ où $g(n) = n^4$.

## Réflexivité
```math
\begin{equation}\begin{split}\forall f(n), f(n) = O(f(n)) \Longrightarrow \exists C > 0, n_0 \in N \qquad tels \quad que \qquad \forall n \ge n_0, f(n) \le C * f(n)\end{split}\end{equation}
```

## Transitivité
```math
\begin{equation}\begin{split}\forall f(n), f(n) = O(g(n)) \quad et \quad \forall g(n), g(n) = O(h(n)) \Longrightarrow f(n) = O(h(n))\end{split}\end{equation}
```
```math
\begin{equation}\begin{split}\forall f(n), g(n), h(n) \quad \exists C_1, C_2 > 0, n_1, n_2 \in N \qquad tels \quad que \qquad f(n) \le C_1 * g(n) \quad et \quad g(n) \le C_2 * h(n) \quad pour \quad n \ge max(n_1,n_2) \Longrightarrow f(n) \le C_1 * C_2 * h(n) \Longrightarrow f(n) = O(h(n))\end{split}\end{equation}
```

## Facteur constant
```math
\begin{equation}\begin{split}\forall f(n), f(n) = O(g(n)) \Longrightarrow \exists C > 0, n_0 \in N, \forall n \ge n_0, f(n) \le C * g(n)\end{split}\end{equation}
```
```math
\begin{equation}\begin{split}\forall c > 0, c * f(n) = O(g(n)) \Longleftrightarrow \exists C' > 0, n'_0 \in N, \forall n \ge n'_0, c * f(n) \le C' * g(n)\end{split}\end{equation}
```

## Règle de la somme
```math
\begin{equation}\begin{split}\forall f(n), f(n) = O(g(n)) \qquad et \qquad \forall h(n), h(n) = O(g(n)) \Longrightarrow f(n) + h(n) = O(g(n))\end{split}\end{equation}
```
```math
\begin{equation}\begin{split}f(n) + h(n) \le C_1 * g(n) + C_2 * g(n) = (C_1 + C_2) * g(n)\end{split}\end{equation}
```

## Règle du produit
```math
\begin{equation}\begin{split}\forall f(n), f(n) = O(g(n)) \qquad et \qquad \forall h(n), h(n) = O(k(n)) \Longrightarrow f(n) * h(n) = O(g(n) * k(n))\end{split}\end{equation}
```
```math
\begin{equation}\begin{split}\exists C_1, C_2 > 0, n_0 \in N, \forall n \ge n_0, f(n) * h(n) \le (C_1 * C_2) * (g(n) * k(n)) = C * (g(n) * k(n))\end{split}\end{equation}
```

## Règle de composition
```math
\begin{equation}\begin{split}\forall f(n), f(n) = O(g(n)) \qquad et \qquad g(n) = O(h(n)) \Longrightarrow f(g(n)) = O(h(n))\end{split}\end{equation}
```
```math
\begin{equation}\begin{split}\exists C_1, C_2 > 0, n_1, n_2 \in N \qquad tels \quad que \qquad \forall n \ge n_1, f(n) \le C_1 * g(n), \qquad et \qquad \forall n \ge n_2, g(n) \le C_2 * h(n), \quad ainsi \quad pour \quad n \ge max(n_1,n_2), f(g(n)) \le C_1 * C_2 * h(n) \Longrightarrow \quad avec \quad C = C_1 * C_2, \qquad on \quad a \qquad f(g(n)) = O(h(n)) \end{split}\end{equation}
```
