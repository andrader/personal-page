# Assignment 1 - Condicional Possibility Measures

```{contents}
:local:
```

O objetivo desse texto é introduzir uma medida de possibilidade condicional e um exemplo numérico. Começamos definindo um *espaço de possibilidade* ($\Omega$, $\mathcal{A}$, $\Pi$) em que $\Omega$ é o conjunto universo, $\mathcal{A}=2^\Omega$ é uma familia de subconjuntos de $\Omega$ e $\Pi:\mathcal{A} \rightarrow [0,1]$ é uma medida de possibilidade. Isto é, $\pi: \Omega \rightarrow [0,1]$ é uma distribuição de possibilidades, então $\Pi$ satisfaz: 
$$
\begin{align}
\Pi(A) = \sup_{w \in A}\pi(w),\ \forall A \in \mathcal{A} \\
\Pi(\Omega) = 1\ \text{ e }\ \Pi(\varnothing) = 1
\end{align}
$$

<!-- Observações: 
- $\Pi$ é também é uma medida de plausibilidade, pois satisfaz (1) Se $A \subseteq B,\ \Pi(A) \leq \Pi(B)$ e (2) $\Pi(\Omega) = 1\ \text{ e }\ \Pi(\varnothing) = 1$;
- propriedade de "maxitividade": $\Pi(A \cup B) = \max(\Pi(A),\Pi(B))$; -->

<!-- Nós estamos interessados em uma medida de possibilidade em um contexto condicional, isto é, na possibilidade de um evento A dado uma nova informação de que um evento B ocorreu. -->

Prade e Dubois[^bignote] citam duas medidas de possibilidade condicional. Aqui apresentamos apenas a primeira medida apresenta por eles, em que a nova informação $B$ altera a distribuição de possibilidades fazendo impossíveis todos os elementos de $\Omega$ que não estão em $B$. É preciso que $B$ seja um evento possível, ou seja, $\Pi(B)= 1$.

Seja $\pi(\cdot \mid B): \Omega \rightarrow [0,1]$ a nova distribuição de possibilidades dada a informação de $B$:
$$
\pi(w \mid B) = 
\begin{cases}
\frac{\pi(w)}{\Pi(B)}, & \text{se}\ w \in B \\
0, & \text{caso contrário}
\end{cases}
$$

Com isso, definimos a possibilidade de $A$ *dado* $B$ é 
$\Pi(A \mid B) := \sup_{w \in A}\pi(w \mid B)$
que também é uma medida de possibilidade pois satisfaz os itens 1 e 2.

<!-- A outra medida de possibilidade condicional citada pelos autores considera que a distribuição de possibilidades codifica informações estatísticas imprecisas mais em linha com uma abordagem bayesiana. -->


**Exemplo**: Suponha um experimento de lançar um dado equilibrado de 6 faces e obervar a face voltada para cima. Nesse caso, consideramos todas as seis faces como plenamente possíveis. Desse mode, $\Omega = \{1,2,3,4,5,6\}$, $\mathcal{A}=2^\Omega$ e $\pi(w) = 1 , \forall w \in \Omega$.

Suponha que surge a informação de que a face voltada para cima é maior que três: $B = \{4,5,6\}$. Com isso, podemos definir uma distribuição de possibilidade condicional:
$$
\pi(w \mid B) := 
\begin{cases}
\frac{\pi(w)}{\Pi(B)}, & \text{se}\ w \in B \\
0, & \text{caso contrário}
\end{cases} = 
\begin{cases}
1, & \text{se}\ w \in \{4,5,6\} \\
0, & \text{se}\ w \in \{1,2,3\}
\end{cases}
$$
e $\ \Pi(A \mid B) := \sup_{w \in A}\pi(w \mid B)$.

Portanto, se estamos interessados na possibilidade de ocorrer um número par, $A = \{2,4,6\}$ dado $B$, obtemos que a possbilidaded é $\Pi(A \mid B) = 1$.
No entanto, se estamos interessados no evento "ocorrer um número par menor que quatro", $C = \{2\}$, então $\Pi(C \mid B) = \pi(2 \mid B) = 0$.
Em palavras, sabendo que a face voltada para cima será maior do que três, é impossível que ocorra um número par menor que quatro.


[^bignote]: Dubois, D., Prade, H. (2012). Possibility Theory. In: Meyers, R. (eds) Computational Complexity. Springer, New York, NY. https://doi.org/10.1007/978-1-4614-1800-9_139