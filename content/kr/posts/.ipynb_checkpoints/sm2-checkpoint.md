---
author: "Woohyeok Moon"
date: 2024-02-06
title: 확률의 정의
categories: 수리통계학
tags: [확률]
showtoc: false
weight: 10
---

러시아의 수학자 콜모고로프(Andrei Kolmogorov, 1903~1987)는 확률을 공리적으로 정의하고자 하였으며 다음과 같은 공리가 확률을 정의하는 필요충분조건이 됨을 보였다.

### 확률의 공리

(1) 임의의 사건 $A$에 대하여 $P(A) \ge 0$이다.  
(2) $P(S) = 1$이다.  
(3) 표본공간 $S$에 정의된 사건열 $A_1, A_2, \cdots$ 가 있다고 하자. 이제 모든 $i \ne j$에 대하여 $A_i \cap A_j = \varnothing$ 이면 $P(\displaystyle\bigcup_{i=1}^{\infty}A_i = \displaystyle\sum_{i=1}^{\infty}P(A_i)$이다.

### 정리 1.1
두 개의 사건 $A$와 $B$에 대하여 다음과 같은 성질들이 성립한다.  
1) $P(A^c) = 1 - P(A)$  
2) $P(\varnothing) = 0$  
3) $A \subset B$이면 $P(A) \le P(B)$이다.  
4) $P(A \cup B) = P(A) + P(B) - P(A \cap B)$

### 증명  
1) $1 = P(S) = P(A \cup A^c) = P(A) + P(A_c) (\because$ 공리 (3))  
2) $0 = 1 - P(S) = P(S^c) = P(\varnothing) (\because$ 공리 (2)와 (1))  
3) $B = A \cup (B \cap A^c)$로 나타낼 수 있으며, $A \cap (B \cap A^c) = \varnothing$이므로 공리 (1)과 (3)에 의해
$$
\\\
P(B) = P(A) + P(B \cap A^c) \ge P(A)
\\\
$$
가 성립한다.  
4) $P(A) = P(A \cap B^c) + P(A \cap B), \quad P(B) = P(B \cap A^c) + P(A \cap B)$

### `예 1.8`
[예 1.1](https://woohyeok-moon.github.io/posts/sm1/#%EC%98%88-11)의 실험에서 표본공간 $S$에 속한 8개의 점들이 모두 같은 확률 $\frac{1}{8}$을 가졌다고 가정하고, 최소한 1개의 앞면이 나오는 사건을 $A$, 꼭 2개의 앞면이 나오는 사건을 $B$, 그리고 첫 번째 동전이 앞면이 나오는 사건을 $C$라고 하자. 그러면, $A$의 여사건은 $A^c = {TTT}$가 되며
$$
\begin{align}
P(A) = 1 - P(A^c) = 1 - \frac{1}{8} = \frac{7}{8}
\end{align}
$$
이 된다. 또
$$
\begin{align}
P(B \cup C) = P(\{HHH, HHT, HTH, THH, HTT\}) = \frac{5}{8}
\end{align}
$$
인데, 이는
$$
\begin{align}
\begin{split}
P(\{HHT, HTH, THH\}) &+ P(\{HHH, HHT, HTH, HTT\})\\\
&- P(\{HHT, HTH\})\\\
&= \frac{3}{8} + \frac{4}{8} - \frac{2}{8} = \frac{5}{8}
\end{split}
\end{align}
$$
와 같이 구할 수도 있다.

### `예 1.9`
[예 1.5](https://woohyeok-moon.github.io/posts/sm1/#%EC%98%88-15)의 실험에서 표본공간 $S = \{1, 2, 3, 4, 5, 6\}$에 속한 6개의 점들이 모두 같은 확률 $\frac{1}{6}$을 가졌다고 가정하자. 사건 $A$와 $B$를
$$
A = \{2, 4, 6\} \qquad B = \{3, 6\}
$$
으로 표현하면, $A \cap B = \{6\}, A \cup B = \{2, 3, 4, 6\}$이 된다. 여기에서
$$
\begin{align}
P(A \cup B) &= P(A) + P(B) - P(A \cap B) \\\
&=\frac{3}{6} + \frac{2}{6} - \frac{1}{6} \\\
&=\frac{2}{3}
\end{align}
$$
와 같음을 알 수 있다.

### `예 1.10`
두 사건 $A$와 $B$가 표본공간 $S$에서 정의되어 있는데, 둘 중 적어도 한 사건이 일어날 확률이 0.3이고 $A$만 일어날 확률이 0.1이라고 하자. 이때 $P(A \cup B) = P(B) + P(A \cap B^c)$이므로 $P(B) = 0.3 - 0.1 = 0.2$가 된다.

### `예 1.11`
세 사건 $A, B, C$가 표본공간 $S$에서 정의되어 있을 때, [정리 1.1](#정리-11)의 (4)에 의해
$$
\begin{align}
P(A \cup B \cup C) =& P((A \cup B) \cup C) \\\
=& P(A \cup B) + P(C) - P((A \cup B) \cap C) \\\
=& P(A) + P(B) - P(A \cap B) + P(C) \\\ &- P((A \cap C) \cup (B \cap C)) \\\
=& P(A) + P(B) + P(C) - P(A \cap B) - P(A \cap C) \\\ &- P(B \cap C) + P(A \cap B \cap C) \\\
\end{align}
$$
이므로 다음이 성립한다.
$$
P(A \cup B \cup C) = P(A) + P(B) + P(C) - P(A \cap B) - P(B \cap C) - P(A \cap C) + P(A \cap B \cap C)
$$
