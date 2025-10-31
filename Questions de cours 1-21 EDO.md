# Questions de cours EDO (1-21)

(Cette fiche a été réalisé à partir du cours sur les EDO de F. Berthelin)
## EDO en se ramenant à l'ordre 1

Soit $y$ une solution de $(E_n)$. Définissons $Y$ comme dans l’énoncé.  
Comme $y$ est $n$ fois dérivable, $Y$ est dérivable et nous avons :

$$
Y'(t) =
\begin{pmatrix}
y'(t) \\
y''(t) \\
\vdots \\
y^{(n)}(t)
\end{pmatrix}
=
\begin{pmatrix}
Y_2(t) \\
Y_3(t) \\
\vdots \\
f(t, y(t), y'(t), \ldots, y^{(n-1)}(t))
\end{pmatrix}
$$

On remarque que la dernière composante du vecteur colonne de droite vaut  
$f(t, Y_0(t), Y_1(t), \ldots, Y_{n-1}(t))$ et on obtient donc $Y'(t) = F(t, Y(t))$.

Réciproquement, soit $Y$ une solution de $(E_1)$.  
Alors $Y_0$ est une solution de $(E_n)$. En effet, $Y$ étant dérivable, chaque $Y_i$ est dérivable. Ainsi $Y_0$ est dérivable et dérivée $Y_1$ elle-même dérivable et ainsi de suite $Y_0$ est $n$ fois dérivable. De plus :

$$
Y_0^{(n)}(t)
= ((Y_0')^{(n-1)})(t)
= (Y_1^{(n-1)})(t)
= (Y_2^{(n-2)})(t)
$$

$$
= \cdots = Y_{n-1}'(t)
= Y_n(t)
= f(t, Y_0(t), \ldots, Y_{n-1}(t))
$$

Ainsi :

$$
Y_0^{(n)}(t) = f(t, Y_0(t), (Y_0)'(t), \ldots, (Y_0)^{(n-1)}(t))
$$

ce qui termine la démonstration.

---

## Définition norme d’opérateur (subordonnée)

$$
\def\tn{|\!|\!|}
\tn f \tn = \sup_{x \in E,\, x \neq 0} \frac{\|f(x)\|_F}{\|x\|_E}
$$

---

## Propriété de la norme subordonnée

Soit $\|\cdot\|$ une norme sur $\mathbb{K}^N$.  
Soit $ \tn \cdot \tn$ la norme sur $M_N(\mathbb{K})$ subordonnée à la norme $\|\cdot\|$.  
Alors cette norme subordonnée vérifie la propriété supplémentaire :

$$
\tn AB\tn \leq \tn A \tn  \tn B \tn  \quad \text{pour tous } A, B \in M_N(\mathbb{K}).
$$

Preuve: 
$$
\def\tn{|\!|\!|}

\|(AB)x\| \leq \|A(Bx)\| \leq \tn A \tn \|Bx\| \leq \tn A \tn \tn B \tn \|x\|
$$

Puis, comme $ \def\tn{|\!|\!|} \tn A \tn $ ne dépend pas de x, on prend le sup d'où

$$
\def\tn{|\!|\!|}

\sup{\frac{\|(AB)x\|}{\|x\|}}  \leq \tn A \tn \tn B \tn \Leftrightarrow  \tn AB \tn \leq \tn A \tn \tn B \tn 
$$

---

## Définition exponentielle de matrice (convergence)

Pour $A \in M_N(\mathbb{K})$, on pose :

$$
e^A = \sum_{p=0}^{+\infty} \frac{A^p}{p!}
$$

Cette quantité est appelée **l’exponentielle de la matrice** $A$.

Vérifions que cette définition a bien un sens en montrant que  
$\sum_{p=0}^{+\infty} \frac{A^p}{p!}$ converge dans $M_N(\mathbb{K})$.

Prenons une norme subordonnée quelconque, par exemple celle associée à la norme euclidienne.  
Utilisant la majoration d'un produit par la norme subordonnée, on a pour tout $p \in \mathbb{N}^*$ :

$$
\def\tn{|\!|\!|}
\left\| \frac{A^p}{p!} \right\| \leq \frac{\tn A \tn ^p}{p!}
$$

Comme la série numérique $\sum \frac{\tn A \tn ^p}{p!}$ est convergente (c’est $e^{\tn A \tn}$),  
par comparaison $\sum \left\| \frac{A^p}{p!} \right\|$ l’est également,  
c’est-à-dire que la série de matrices $\sum \frac{A^p}{p!}$ est absolument convergente dans $M_N(\mathbb{K})$.  
Comme $M_N(\mathbb{K})$ est un espace vectoriel normé de dimension finie, il est complet.  
Et ainsi toute série absolument convergente est convergente.  
Ceci implique que :

$$
\sum_{p=0}^{+\infty} \frac{A^p}{p!}
$$

converge dans $M_N(\mathbb{K})$.

---

## Propriétés exponentielle de matrice

Posons :

$$
U_n = \frac{A^n}{n!}, \quad V_n = \frac{B^n}{n!}
$$

et utilisons le théorème de convergence du produit de cauchy de séries convergentes. Ceci prouve la convergence absolue de $\sum W_n$, où :

$$
W_n = \sum_{k=0}^n \frac{A^k B^{n-k}}{k! (n-k)!}
$$

et la relation :

$$
\sum_{n=0}^{+\infty} W_n =
\left(\sum_{n=0}^{+\infty} U_n\right)
\left(\sum_{n=0}^{+\infty} V_n\right)
= e^A e^B
$$

La formule du binôme, valable lorsque $A$ et $B$ commutent, donne :

$$
(A+B)^n = \sum_{k=0}^n \frac{n!}{k!(n-k)!} A^k B^{n-k}
$$

ainsi :

$$
W_n = \frac{1}{n!}(A+B)^n
$$

et donc :

$$
e^A e^B = e^{A+B}
$$

Ainsi :

$$
e^A e^B = e^{A+B} = e^{B+A} = e^B e^A
$$

---

## Solution EDO d'ordre 1 homogène

Tout d’abord, on vérifie que :

$$
\tilde{y}(t) = y_0 e^{\int_{t_0}^t a(s)\,ds}
$$

définie sur $I$ convient : elle est dérivable sur $I$ et :

$$
\tilde{y}'(t) = y_0 a(t) e^{\int_{t_0}^t a(s)\,ds} = a(t)\tilde{y}(t)
$$

et $\tilde{y}(t_0) = y_0$.

Étant définie sur $I$, elle est globale et donc maximale.

Montrons maintenant qu’il n’y a pas d’autres solutions maximales.  
Soit $y$ une solution maximale définie sur un intervalle $J \subset I$ telle que  
$t_0 \in J$ et $y(t_0) = y_0$. On calcule :

$$
(y(t)e^{-\int_{t_0}^t a(s)\,ds})'
= (y'(t) - a(t)y(t)) e^{-\int_{t_0}^t a(s)\,ds} = 0
$$

donc $t \mapsto y(t)e^{-\int_{t_0}^t a(s)\,ds}$ est constante sur $J$.  
Ceci donne :

$$
y(t)e^{-\int_{t_0}^t a(s)\,ds} = y(t_0) = y_0
$$

sur $J$, donc $y$ coïncide sur $J$ avec la solution $\tilde{y}$.  
Comme $y$ est maximale, on a donc $J = I$ et $y = \tilde{y}$.

---

## Démonstration de l’unicité du Théorème de Cauchy-Lipschitz

Soient $y, z$ deux solutions de $(E)$ sur $I$ avec la condition $y(t_0) = y_0$.  
Alors $y$ et $z$ vérifient la formulation intégrale :

$$
y(t) - z(t) = \int_{t_0}^t A(s)(y(s) - z(s))\,ds
$$

Ceci entraîne, pour $t \in I, t \geq t_0$ :

$$
\|y(t) - z(t)\| \leq \int_{t_0}^t \tn A(s) \tn ,\|y(s) - z(s)\|\,ds
$$

et pour $t < t_0$ :

$$
\|y(t) - z(t)\| \leq \int_t^{t_0} \tn A(s) \tn ,\|y(s) - z(s)\|\,ds
$$

Ainsi, pour tout $t \in I$, il vient :

$$
\|y(t) - z(t)\| \leq \int_{t_0}^t \tn A \tn ,\|y(s) - z(s)\|\,ds
$$

Le lemme de Gronwall 1.35, avec $u(t) = \|y(t) - z(t)\|$, $a = 0$, $v = \tn A \tn $, donne alors :

$$
\|y(t) - z(t)\| \leq 0
$$

pour tout $t \in I$, c’est-à-dire $y = z$.

---

## Structure de $S_H$

Soient $I$ un intervalle de $\mathbb{R}$ et $A \in C(I, M_N(\mathbb{K}))$.  
Alors :

a) L’ensemble $S_H$ des solutions maximales de $(L_H)$ est un **sous-espace vectoriel** de $C(I, \mathbb{K}^N)$.  
b) Pour tout $t_0 \in I$, l’application

$$
\Phi_{t_0} :
\begin{cases}
S_H \to \mathbb{K}^N \\
y \mapsto y(t_0)
\end{cases}
$$

est un **isomorphisme d’espaces vectoriels**.  
c) $S_H$ est de **dimension $N$**.


**Démonstration.**

a) Tout d’abord, on remarque que la fonction nulle est solution.  
Soient $\lambda \in \mathbb{K}$ et $y_1, y_2 \in S_H$.  
C’est-à-dire que $y_1$ et $y_2$ sont deux solutions de $(L_H)$.  
On a :

$$
(\lambda y_1 + y_2)'(t) = \lambda y_1'(t) + y_2'(t) = \lambda A(t)y_1(t) + A(t)y_2(t) = A(t)(\lambda y_1(t) + y_2(t))
$$

ainsi $\lambda y_1 + y_2 \in S_H$.

b) Soient $\lambda \in \mathbb{K}$ et $y_1, y_2 \in S_H$. On a :

$$
\Phi_{t_0}(\lambda y_1 + y_2) = (\lambda y_1 + y_2)(t_0) = \lambda y_1(t_0) + y_2(t_0) = \lambda \Phi_{t_0}(y_1) + \Phi_{t_0}(y_2)
$$

Ceci démontre la linéarité de $\Phi_{t_0}$.

Soit $y_0 \in \mathbb{K}^N$. D’après l’existence et l’unicité d’une solution maximale pour un problème de Cauchy (théorème 2.3), il existe une et une seule $y \in S_H$ telle que $y(t_0) = y_0$.  
Ainsi $\Phi_{t_0}$ est bijective.

c) Comme $\mathbb{K}^N$ est de dimension $N$, par isomorphisme de b), $S_H$ est aussi de dimension $N$. □

---

## Solutions Équation différentielle linéaire scalaire d’ordre 1

Soient $a, b : I \to \mathbb{K}$ des fonctions continues avec $I$ un intervalle de $\mathbb{R}$.  
Soient $t_0 \in I$ et $y_0 \in \mathbb{K}$.  
La solution maximale (et définie sur $I$, donc globale) de l’équation différentielle :

$$
y' = a(t)y + b(t)
$$

avec la condition initiale $y(t_0) = y_0$, est donnée par :

$$
y(t) = y_0 e^{\int_{t_0}^t a(s)\,ds}
+ \int_{t_0}^t b(s)e^{\int_s^t a(\sigma)\,d\sigma}\,ds
$$

## Lemme de Gronwall différentiel

Soient $I$ un intervalle de $\mathbb{R}$, $t_0 \in I$, $w \in C^1(I, \mathbb{R})$ et $\nu \in C(I, \mathbb{R})$.  
Supposons que, pour tout $t \in I$,  

$$
w'(t) \leq \nu(t)w(t).
$$

Alors, pour tout $t \in I$ tel que $t \geq t_0$,  

$$
w(t) \leq w(t_0)e^{\int_{t_0}^t \nu(s)\,ds}.
$$

**Démonstration.**  
L’hypothèse $w'(t) \leq \nu(t)w(t)$ donne :

$$
\frac{d}{dt}\left[w(t)e^{-\int_{t_0}^t \nu(s)\,ds}\right]
= (w'(t) - \nu(t)w(t)) e^{-\int_{t_0}^t \nu(s)\,ds} \leq 0.
$$

Ainsi, $t \mapsto w(t)e^{-\int_{t_0}^t \nu(s)\,ds}$ est décroissante, ce qui, pour $t \geq t_0$, entraîne :

$$
w(t)e^{-\int_{t_0}^t \nu(s)\,ds} \leq w(t_0).
$$

---

## Régularité des solutions

Soit $\Omega$ un ouvert de $\mathbb{R} \times \mathbb{K}^N$.  
Si $f : \Omega \to \mathbb{K}^N$ est de classe $C^k$ avec $k \in \mathbb{N}$, alors toute solution de $(E)$ est de classe $C^{k+1}$.

**Démonstration.**  
Démontrons ce résultat par récurrence sur $k \in \mathbb{N}$.  
Commençons par $k=0$, c’est-à-dire supposons que $f$ est continue.  
Soit $y : I \to \mathbb{R}^N$ une solution de $(E)$.  
La fonction $y$ est dérivable et $y'(t) = f(t, y(t))$, ainsi $y'$ est continue et $y$ est de classe $C^1$.

Supposons le résultat vrai au rang $k$ et soit $f : \Omega \to \mathbb{R}^N$ de classe $C^{k+1}$.  
Soit $y : I \to \mathbb{R}^N$ une solution de $(E)$.  
Par hypothèse de récurrence, $y$ est de classe $C^{k+1}$ (car $f$ est de classe $C^{k+1}$ et donc de classe $C^k$).  
Ainsi $y'(t) = f(t, y(t))$ est de classe $C^k+1$ et donc $y$ est de classe $C^{k+2}$.

---

## Formulation intégrale du problème de Cauchy

Soient $\Omega$ un ouvert de $\mathbb{R} \times \mathbb{K}^N$ et $f : \Omega \to \mathbb{R}^N$ continue.  
Soit $(t_0, y_0) \in \Omega$.  
Une fonction $y : I \to \mathbb{K}^N$ est une solution de $(E)$ telle que $y(t_0)=y_0$ si et seulement si :  

i) $y$ est continue,  
ii) pour tout $t \in I$, $(t, y(t)) \in \Omega$,  
iii) pour tout $t \in I$,  

$$
y(t) = y_0 + \int_{t_0}^t f(s, y(s))\,ds.
$$

**Démonstration.**  
Supposons d’abord que $y : I \to \mathbb{K}^N$ soit une solution de $(E)$ telle que $y(t_0) = y_0$.  
Alors $y$ est dérivable sur $I$, donc continue sur $I$.  
En intégrant la relation $y'(s) = f(s, y(s))$ entre $t_0$ et $t$, on obtient :

$$
y(t) - y(t_0) = \int_{t_0}^t f(s, y(s))\,ds.
$$

Réciproquement, si $y(t) = y_0 + \int_{t_0}^t f(s, y(s))\,ds$ sur $I$, alors comme $f$ et $y$ sont continues, cette relation montre que $y$ est dérivable sur $I$ et, en dérivant la relation, on obtient :

$$
y'(t) = f(t, y(t)), \quad \text{pour tout } t \in I.
$$

De plus, $y(t_0) = y_0$.

---

## Lemme de Gronwall intégral

Soient $I$ un intervalle de $\mathbb{R}$, $t_0 \in I$, $a \in \mathbb{R}$ et $u, \nu \in C(I, \mathbb{R})$.  
Supposons $\nu \geq 0$ et que, pour tout $t \in I$ tel que $t \geq t_0$,  

$$
u(t) \leq a + \int_{t_0}^t \nu(s)u(s)\,ds.
$$

Alors, pour tout $t \in I$ tel que $t \geq t_0$,  

$$
u(t) \leq a e^{\int_{t_0}^t \nu(s)\,ds}.
$$

**Démonstration.**  
Pour $t \in I$ tel que $t \geq t_0$, posons :

$$
w(t) = a + \int_{t_0}^t \nu(s)u(s)\,ds.
$$

On a $w'(t) = \nu(t)u(t)$.  
L’hypothèse $u(t) \leq w(t)$ implique alors $w'(t) \leq \nu(t)w(t)$.  
En appliquant le lemme de Gronwall différentiel, on obtient :

$$
w(t) \leq w(t_0)e^{\int_{t_0}^t \nu(s)\,ds},
$$

et ainsi :

$$
u(t) \leq w(t) \leq a e^{\int_{t_0}^t \nu(s)\,ds}.
$$

**Remarque**
Cette démonstration assez classique est à connaitre car elle permet de résoudre ce genre d'inégalité en se ramenant à le Lemme de Gronwall différentiel.
Il faut se méfier des hypothèses car ici on ne suppose pas $u \in C^1(I, \mathbb{R}) $ mais on suppose $ v\geq 0$. 

---

## Démonstration (variation de la constante)

D’après Cauchy-Lipschitz, les solutions de l’équation homogène associée $y' = a(t)y$ sont :

$$
y(t) = Ce^{\int_{t_0}^t a(s)\,ds},
$$

avec $C$ une constante quelconque.  
La méthode de variation de la constante consiste à poser :

$$
y(t) = C(t)e^{\int_{t_0}^t a(s)\,ds}
$$

et à chercher $C(t)$ pour que $y$ soit solution de l’équation donnée.  
Nous calculons :

$$
y'(t) = (C'(t) + a(t)C(t)) e^{\int_{t_0}^t a(s)\,ds}.
$$

Ainsi, $y'(t) - a(t)y(t) = C'(t)e^{\int_{t_0}^t a(s)\,ds}$,  
et $y'(t) = a(t)y(t) + b(t)$ si et seulement si :

$$
C'(t)e^{\int_{t_0}^t a(s)\,ds} = b(t),
$$

c’est-à-dire :

$$
C(t) = C_0 + \int_{t_0}^t e^{-\int_{t_0}^s a(\sigma)\,d\sigma} b(s)\,ds.
$$

D’où :

$$
y(t) = C_0 e^{\int_{t_0}^t a(s)\,ds} + \int_{t_0}^t b(s)e^{\int_s^t a(\sigma)\,d\sigma}\,ds.
$$

Enfin, la valeur en $t = t_0$ impose $C_0 = y_0$.  
La fonction obtenue est bien solution.  
D’après le théorème de Cauchy–Lipschitz linéaire, il s’agit de l’unique solution vérifiant $y(t_0) = y_0$.

---

## Identité d’Abel

Soient $I$ un intervalle de $\mathbb{R}$ et $A \in C(I, M_N(\mathbb{K}))$.  
Soit $\Phi(t)$ une matrice fondamentale du système $(L_H)$.  
Alors le wronskien $W(t)$ associé à $\Phi(t)$ vérifie :

$$
W'(t) = \text{Tr}(A(t))W(t),
$$

et donc l’identité d’Abel :

$$
W(t) = W(t_0)e^{\int_{t_0}^t \text{Tr}(A(s))\,ds}.
$$

**Démonstration.**  
Le wronskien est défini par la relation $W(t) = \det \Phi(t)$.  
La matrice fondamentale étant dérivable, on a :

$$
\Phi(t+h) = \Phi(t) + h\Phi'(t) + o(h) \quad (h \to 0),
$$

et ainsi :

$$
W(t+h) = \det(\Phi(t+h)) = \det(\Phi(t)) \det(Id + h\Phi'(t)\Phi(t)^{-1} + o(h)).
$$
Or $\Phi'(t) = A(t)\Phi(t)$, on en déduit :
$$
\begin{align}
W(t+h) = \det(Id + hA(t) + o(h))W(t)
\end{align}
$$

Et on utilise la formule du polynôme caractéristique $ \chi_M$ de $M$:

$$
\det(\lambda Id-M) = \lambda^n -\text{Tr}(M)\lambda^{n-1} + ... + (-1)^n\det(M)
$$

D'où en posant $\det(Id + \lambda A) = \lambda^n\chi_M(\frac{-1}{\lambda}) $ on obtient:

$$
det(Id +\lambda M) = 1 + \lambda \text{Tr}(M) + ... + \lambda^n\det(M)
$$

Ce qui, en remplaçant $\lambda$ par $h$ et $M$ par $A(t) + o(1)$ dans l'équation (1):

$$
W(t+h) = (1 + h\text{Tr}(A(t)) + o(h))W(t)
$$

Puis en développant puis en réarangeant les termes pour exprimer la dérivée de $W(t)$:
$$
\begin{align}
W'(t) = \text{Tr}(A(t))W(t).
\end{align}
$$

On obtient ensuite l'identité intégrale en cherchant les solutions de l'équation différentielle d'ordre 1 homogène vérifiée par $W(t)$ à (2).

---

## Calcul de l’exponentielle d’une matrice

Commençons par le cas d’une matrice diagonale :

$$
A = \text{diag}(\lambda_1, \lambda_2, \ldots, \lambda_N).
$$

Pour tout $k \in \mathbb{N}$, on a $A^k = \text{diag}(\lambda_1^k, \lambda_2^k, \ldots, \lambda_N^k)$ et donc :

$$
\exp(tA) = \sum_{k=0}^{+\infty} \frac{t^k A^k}{k!}
= \text{diag}(e^{t\lambda_1}, e^{t\lambda_2}, \ldots, e^{t\lambda_N}).
$$

Passons au cas d’une matrice diagonalisable :

$$
A = P D P^{-1} \quad \text{avec} \quad D = \text{diag}(\lambda_1, \ldots, \lambda_N).
$$

Alors, pour tout $k \in \mathbb{N}$ :

$$
A^k = P D^k P^{-1}.
$$

D’où :

$$
\sum_{k=0}^{K} \frac{t^k A^k}{k!}
= P \left(\sum_{k=0}^{K} \frac{t^k D^k}{k!}\right) P^{-1}.
$$

En faisant $K \to +\infty$, on obtient :

$$
\exp(tA) = P \exp(tD) P^{-1} = P \text{diag}(e^{t\lambda_1}, \ldots, e^{t\lambda_N}) P^{-1}.
$$

---

## Cas d’une matrice sous forme de Jordan

Comme toute matrice commute avec l’identité, on a pour $R$ nilpotente :

$$
\exp(R) = \sum_{k=0}^{N-1} \frac{R^k}{k!}.
$$

Ainsi, pour $A = \lambda I + R$, on obtient :

$$
\exp(tA) = e^{t\lambda} \exp(tR)
= e^{t\lambda} \sum_{k=0}^{N-1} \frac{t^k R^k}{k!}.
$$

**Remarque**  
Ceci marche également dans le cas où $A \in M_N(\mathbb{K})$ admet une unique valeur propre $\lambda$ dans $\mathbb{C}$.
De plus, en exprimant la matrice diagonalement avec ses blocs de jordan, cela peut se généraliser à toutes matrices dans $\mathbb{R}$ car elle sont toutes diagonalisable au sens de Jordan (Un bloc par valeur propre.)

## Principe de superposition des solutions

Soient $a_0, \ldots, a_{n-1} \in \mathbb{C}$, $c_1, \ldots, c_N \in \mathbb{C}$ et $b_1, \ldots, b_N \in C(I, \mathbb{C})$ avec $I$ un intervalle de $\mathbb{R}$.  
Si, pour $l = 1, \ldots, N$, $y_l$ est une solution de :

$$
y^{(n)} + a_{n-1}y^{(n-1)} + \cdots + a_1y' + a_0y = b_l(t),
$$

alors $c_1y_1 + c_2y_2 + \cdots + c_Ny_N$ est une solution de :

$$
y^{(n)} + a_{n-1}y^{(n-1)} + \cdots + a_1y' + a_0y = c_1b_1(t) + c_2b_2(t) + \cdots + c_Nb_N(t).
$$

**Démonstration.**  
Nous avons :

$$
(c_1y_1 + \cdots + c_Ny_N)^{(n)} + a_{n-1}(c_1y_1 + \cdots + c_Ny_N)^{(n-1)} + \cdots + a_0(c_1y_1 + \cdots + c_Ny_N)
$$

$$
= c_1(y_1^{(n)} + a_{n-1}y_1^{(n-1)} + \cdots + a_1y_1' + a_0y_1) + \cdots + c_N(y_N^{(n)} + a_{n-1}y_N^{(n-1)} + \cdots + a_1y_N' + a_0y_N)
$$

$$
= c_1b_1 + \cdots + c_Nb_N.
$$

En utilisant la linéarité de la dérivation.

---

## Allure système 2x2 valeurs propres réelles — matrice diagonalisable

Supposons d’abord que les deux valeurs propres sont réelles, notons-les $\lambda$ et $\mu$, et que la matrice est diagonalisable.  
Alors il existe $P \in M_2(\mathbb{R})$ telle que :

$$
A = P
\begin{pmatrix}
\lambda & 0 \\
0 & \mu
\end{pmatrix}
P^{-1}.
$$

Notons $e_1$ et $e_2$ les vecteurs colonnes de $P$, ce sont des vecteurs propres pour $A$ de valeurs propres respectives $\lambda$ et $\mu$.  
Dans le cas où $\lambda = \mu$, comme $A$ est supposée diagonalisable, l’espace propre associé à la valeur propre est de dimension 2 et les vecteurs $e_1$ et $e_2$ forment une base de cet espace.

Posons :

$$
B =
\begin{pmatrix}
\lambda & 0 \\
0 & \mu
\end{pmatrix},
\quad
\tilde{Y} = P^{-1}Y =
\begin{pmatrix}
\tilde{x} \\
\tilde{y}
\end{pmatrix}.
$$

Alors :

$$
\tilde{Y}' = P^{-1}Y' = P^{-1}AY = BP^{-1}Y = B\tilde{Y}.
$$

Ainsi, le système différentiel s’écrit dans les nouvelles variables :

$$
\begin{cases}
\tilde{x}' = \lambda\tilde{x}, \\
\tilde{y}' = \mu\tilde{y}.
\end{cases}
$$

Les solutions sont :

$$
\begin{cases}
\tilde{x}(t) = C_1 e^{\lambda t}, \\
\tilde{y}(t) = C_2 e^{\mu t}.
\end{cases}
$$

et les solutions de $Y' = AY$ sont données par :

$$
Y(t) = P\tilde{Y}(t) = C_1 e^{\lambda t} e_1 + C_2 e^{\mu t} e_2.
$$

Pour $C_1 = 0$, on trouve $\tilde{x} = 0$, et pour $C_2 = 0$, on trouve $\tilde{y} = 0$.  
Pour $C_1C_2 \neq 0$, on a :

$$
\frac{\tilde{x}(t)}{C_1} = e^{\lambda t}, \quad \frac{\tilde{y}(t)}{C_2} = e^{\mu t},
$$

d’où :

$$
\left( \frac{\tilde{x}(t)}{C_1} \right)^\mu = \left( \frac{\tilde{y}(t)}{C_2} \right)^\lambda,
$$

soit :

$$
\tilde{y} = C |\tilde{x}|^{\frac{\mu}{\lambda}},
\quad
C = \frac{C_2}{|C_1|^{\frac{\mu}{\lambda}}}.
$$

---

## Allure système 2x2 valeurs propres réelles — matrice non diagonalisable

Supposons que les valeurs propres soient réelles et que la matrice ne soit pas diagonalisable.  
Alors il n’y a qu’une seule valeur propre $\lambda$ et un bloc de Jordan.  
Il existe $P \in M_2(\mathbb{R})$ telle que :

$$
A = P
\begin{pmatrix}
\lambda & 1 \\
0 & \lambda
\end{pmatrix}
P^{-1}.
$$

Posons :

$$
B =
\begin{pmatrix}
\lambda & 1 \\
0 & \lambda
\end{pmatrix},
\quad
\tilde{Y} = P^{-1}Y =
\begin{pmatrix}
\tilde{x} \\
\tilde{y}
\end{pmatrix}.
$$

Alors :

$$
\tilde{Y}' = P^{-1}Y' = P^{-1}AY = BP^{-1}Y = B\tilde{Y},
$$

et le système s’écrit :

$$
\begin{cases}
\tilde{x}' = \lambda \tilde{x} + \tilde{y}, \\
\tilde{y}' = \lambda \tilde{y}.
\end{cases}
$$

On résout d’abord la seconde équation :

$$
\tilde{y}(t) = C_2 e^{\lambda t}.
$$

Puis la première :

$$
\tilde{x}' = \lambda \tilde{x} + C_2 e^{\lambda t}.
$$

On applique la méthode de variation de la constante :

$$
\tilde{x}(t) = (C'(t) + \lambda C(t)) e^{\lambda t} = C_1 e^{\lambda t} + C_2 t e^{\lambda t}.
$$

Ainsi :

$$
\tilde{x}(t) = (C_1 + C_2 t)e^{\lambda t}, \quad \tilde{y}(t) = C_2 e^{\lambda t}.
$$

et :

$$
Y(t) = P\tilde{Y}(t) = (C_1 + C_2 t)e^{\lambda t} e_1 + C_2 e^{\lambda t} e_2.
$$

Les courbes intégrales s’écrivent :

$$
\tilde{x} = C_1 + C_2 t, \quad \tilde{y} = C_2 e^{\lambda t},
$$

et :

$$
\tilde{x} = C + \frac{1}{\lambda} \ln |\tilde{y}|.
$$

---

## Détail méthode de la variation de la constante (MVC) pour le cas d’ordre 2

Soient $I$ un intervalle de $\mathbb{R}$, $a_0, a_1, b \in C(I, \mathbb{C})$, et l’équation différentielle :

$$
y'' + a_1(t)y' + a_0(t)y = b(t).
$$

Soient $y_1$ et $y_2$ deux solutions indépendantes de l’équation homogène associée.  
Posons (en utilisant la technique pour se ramener à l'ordre 1 puis en identifiant A):

$$
Y =
\begin{pmatrix}
y \\
y'
\end{pmatrix},
\quad
A(t) =
\begin{pmatrix}
0 & 1 \\
-a_0(t) & -a_1(t)
\end{pmatrix},
\quad
B(t) =
\begin{pmatrix}
0 \\
b(t)
\end{pmatrix}.
$$

L’équation différentielle s’écrit $Y' = A(t)Y + B(t)$.  
Posons $Y(t) = \Phi(t)C(t)$ avec $\Phi(t)$ matrice fondamentale :

$$
\Phi(t) =
\begin{pmatrix}
y_1 & y_2 \\
y_1' & y_2'
\end{pmatrix},
\quad
C(t) =
\begin{pmatrix}
\lambda(t) \\
\mu(t)
\end{pmatrix}.
$$

Alors :

$$
\Phi'(t)C(t) + \Phi(t)C'(t) = A(t)\Phi(t)C(t) + B(t),
$$

et comme $\Phi'(t) = A(t)\Phi(t)$, il vient :

$$
\Phi(t)C'(t) = B(t).
$$

Soit donc :

$$
\begin{cases}
\lambda'(t)y_1' + \mu'(t)y_2' = 0, \\
\lambda'(t)y_1' + \mu'(t)y_2' = b(t).
\end{cases}
$$

il suffit ensuite de calculer des primitives de $\lambda'$ et $\mu'$ et remplacer dans le système initial.

---

## Réduction d’ordre (D’Alembert)

Soit $y_1$ une solution particulière de :

$$
y'' + p(y)y' + q(y)y = 0.
$$

On définit une nouvelle fonction inconnue $z$ par $y = y_1 z$.  
Alors :

$$
y' = y_1' z + y_1 z', \quad y'' = y_1'' z + 2y_1' z' + y_1 z''.
$$

On obtient :

$$
y'' + p(y)y' + q(y)y = y_1(z'' + (2\frac{y_1'}{y_1} + p)y_1z' + (y_1'' + p y_1' + q y_1)z).
$$

Ainsi, $y$ sera solution si et seulement si $z$ est solution de (en multipliant par $y_1$) :

$$
y_1^2 z'' + (2y_1 y_1' + p y_1^2)z' = 0,
$$

ou encore :

$$
(y_1^2z')' + p(t)y_1^2z' = 0.
$$

Cette dernière équation est du premier ordre en $z'$, on la résout :

$$
z'(t) = C_1 \frac{1}{y_1^2(t)} e^{-\int p(t)\,dt}.
$$

Ainsi :

$$
y(t) = y_1(t) \left(C_1 \int_{t_0}^t \frac{1}{y_1^2(s)} e^{-\int_{t_0}^s p(\sigma)\,d\sigma}\,ds + C_2\right).
$$

**Remarque**  
Cette technique se généralise à l’ordre $n$ et permet d’obtenir une équation d’ordre $n-1$ sur $z'$ à partir d’une équation d’ordre $n$ en $z$.  
Elle a été trouvée par D’Alembert.
