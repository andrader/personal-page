# Assignment 3 - Maximum Likelihood Estimation [TODO]

```{contents}
:local:
```

## Lista 3

1. Seja $Z_1, \ldots, Z_n$ uma amostra aleatória de $Z \sim \text{Ber}(\theta)$, $\theta \in (0,1)$.
   1. Encontre o EMV para $g(\theta) = \mathbb{E}_\theta(Z)$.
   2. Encontre o EMV para $g(\theta) = \mathbb{P}_\theta(Z=0)$.
   3. Encontre o EMV para $g(\theta) = \text{Var}_\theta(Z)$.
   4. Considere que os dados foram observados $(1, 1, 1, 0, 0, 1)$. Encontre as estimativas de MV nos itens acima.
2. Seja $Z_1, \ldots, Z_n$ uma amostra aleatória de $Z \sim \text{Exp}(\theta)$, $\theta \in (0,\infty)$.
   6. Encontre o EMV para $g(\theta) = \mathbb{E}_\theta(Z)$.
   7. Encontre o EMV para $g(\theta) = \mathbb{P}_\theta(Z>1)$.
   8. Encontre o EMV para $g(\theta) = \mathbb{P}_\theta(0.1 < Z < 1)$.
   9.  Encontre o EMV para $g(\theta) = \text{Var}_\theta(Z)$.
   10. Considere que os dados foram observados $(0.1, 0.5, 0.2, 0.2, 0.7, 0.15)$. Encontre as estimativas de MV nos itens acima.
2. Seja $Z_1, \ldots, Z_n$ uma amostra aleatória de $Z \sim N(\mu, \sigma^2)$, $\theta = (\mu, \sigma^2) \in (-\infty, \infty) \times (0, \infty)$.
   1. Encontre o EMV para $g(\theta) = \mathbb{E}_\theta(Z)$.
   2. Encontre o EMV para $g(\theta) = \mathbb{P}_\theta(Z<2.5)$.
   3. Encontre o EMV para $g(\theta) = \mathbb{P}_\theta(2.4 < Z < 2.5)$.
   4. Encontre o EMV para $g(\theta) = \text{Var}_\theta(Z)$.
   5. Considere que os dados foram observados $(2.4, 2.7, 2.3, 2 , 2.5, 2.6)$. Encontre as estimativas de MV nos itens acima.
3. Seja $Z_1, \ldots, Z_n$ uma amostra aleatória de $Z \sim f_\theta$, $\theta \in (0,\infty)$, tal que $f_\theta(x) = \theta x^{\theta-1}$, se $x \in (0,1)$, e $f_\theta(x) = 0$, caso contrário.
   1. Encontre o EMV para $g(\theta) = \mathbb{E}_\theta(Z)$.
   2. Encontre o EMV para $g(\theta) = \mathbb{P}_\theta(Z>1/3)$.
   3. Encontre o EMV para $g(\theta) = \mathbb{P}_\theta(1/3 < Z < 1/2)$.
   4. Encontre o EMV para $g(\theta) = \text{Var}_\theta(Z)$.
   5. Considere que os dados foram observados $(0.11, 0.52, 0.23, 0.21, 0.36, 0.15)$. Encontre as estimativas de MV para os itens acima.

Verifique se o EMV em cada exercício anterior é função de uma estatística suficiente.
Justifique todos os passos.


## Resolução

### 1. 

Se $Z$ é uma variável aleatória de Bernoulli com parâmetro $\theta$, então a função de massa de probabilidade de $Z$ é

$$ f(z|\theta) = \theta^z (1-\theta)^{1-z}, \quad z \in \{0,1\}. $$

E como a amostra é $iid$, segue que a função de verossimilhança é

$$ 
\begin{aligned}
L(\theta) &= \prod_{i=1}^n f(z_i|\theta) = \theta^{\sum_{i=1}^n z_i} (1-\theta)^{n - \sum_{i=1}^n z_i} \\
&= \theta^{n\bar{z}} (1-\theta)^{n - n\bar{z}} \\
&= \theta^{n\bar{z}} (1-\theta)^{n(1-\bar{z})},
\end{aligned}
$$

em que $\bar{z} = \frac{1}{n} \sum_{i=1}^n z_i$.

E a função log-verossimilhança é

$$ \ell(\theta) = \log L(\theta) = n\bar{z} \log \theta + n(1-\bar{z}) \log(1-\theta). $$

#### 1. a)

Notemos que $g(\theta) = \mathbb{E}_\theta(Z) = \theta$. 
Então, o EMV para $g(\theta)$ é o valor de $\theta$ que maximiza $L(\theta)$ ou, de forma equivalente, $\ell(\theta)$.

Para maximizar $\ell(\theta)$, primeiro derivamos $\ell(\theta)$ em relação a $\theta$:

Em seguida, igualamos a derivada a zero e resolvemos para $\theta$:

$$
\begin{aligned}
\frac{d}{d\theta} \ell(\theta) = 0 &\Rightarrow \frac{n\bar{z}}{\theta} - \frac{n(1-\bar{z})}{1-\theta} = 0 \\
&\Rightarrow \frac{n\bar{z}}{\theta} = \frac{n(1-\bar{z})}{1-\theta} \\
&\Rightarrow \bar{z} (1-\theta) = (1-\bar{z})\theta \\
&\Rightarrow \bar{z} - \bar{z}\theta = \theta - \bar{z}\theta \\
&\Rightarrow \theta = \bar{z}.
\end{aligned}
$$

Assim, $\bar{z}$ é um ponto crítico de $\ell(\theta)$. Para verificar se é um ponto de máximo, vejamos se $\frac{d^2}{d\theta^2} \ell(\theta) \mid_{\theta = \bar{z}} \, < 0$.

$$
\frac{d^2}{d\theta^2} \ell(\theta) = -\frac{n\bar{z}}{\theta^2} - \frac{n(1-\bar{z})}{(1-\theta)^2}. 
$$

No ponto $\theta = \bar{z}$, temos que

$$ \frac{d^2}{d\theta^2} \ell(\bar{z}) = -\frac{n\bar{z}}{\bar{z}^2} - \frac{n(1-\bar{z})}{(1-\bar{z})^2} = -\frac{n}{\bar{z}} - \frac{n}{1-\bar{z}} < 0. 
$$

Logo, $\theta = \bar{z}$ é um ponto de máximo de $\ell(\theta)$ e, portanto, o EMV para $g(\theta) = \mathbb{E}_\theta(Z)$ é $\widehat{\theta \,} = \bar{Z}$.

#### 1. b)

Notemos que $g(\theta) = \mathbb{P}_\theta(Z=0) = 1 - \theta$.

Pela propriedade de invariância do EMV, temos que $\widehat{g(\theta)} = g(\widehat{\theta})$. Assim, $\widehat{g(\theta)} = 1 - \widehat{\theta} = 1 - \bar{Z}$.

#### 1. c)

Notemos que $g(\theta) = \text{Var}_\theta(Z) = \theta(1-\theta)$.

E pela propriedade de invariância do EMV, temos que $\widehat{g(\theta)} = g(\widehat{\theta})$. Assim, $\widehat{g(\theta)} = \widehat{\theta}(1-\widehat{\theta}) = \bar{Z}(1-\bar{Z})$.


#### 1. d)

Considere que os dados foram observados $(1, 1, 1, 0, 0, 1)$. Então, $\bar{Z} = \frac{1}{6} \sum_{i=1}^6 z_i = \frac{4}{6} = \frac{2}{3}$.

Assim, as estimativas de MV são:
1. $\widehat{\theta} = \bar{Z} = \frac{2}{3}$.
2. $\widehat{\mathbb{P}_\theta(Z=0)} = 1 - \bar{Z} = 1 - \frac{2}{3} = \frac{1}{3}$.
3. $\widehat{\text{Var}_\theta(Z)} = \bar{Z}(1-\bar{Z}) = \frac{2}{3} \left(1 - \frac{2}{3}\right) = \frac{2}{9}$.

### 2.

Se $Z$ é uma variável aleatória exponencial com parâmetro $\theta$, então a função densidade de probabilidade de $Z$ é
$$ f(z|\theta) = \theta e^{-\theta z}, \quad z \in (0,\infty). $$

E como a amostra é $iid$, segue que a função de verossimilhança é

$$
\begin{aligned}
L(\theta) &= \prod_{i=1}^n f(z_i|\theta) = \theta^n e^{-\theta \sum_{i=1}^n z_i} \\
&= \theta^n e^{-n\theta \bar{z}}.
\end{aligned}
$$

E a função log-verossimilhança é

$$ \ell(\theta) = \log L(\theta) = n \log \theta - n\theta \bar{z}. $$

#### 2. a)

Notemos que $g(\theta) = \mathbb{E}_\theta(Z) = \frac{1}{\theta}$.
