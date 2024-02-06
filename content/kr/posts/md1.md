---
author: "Woohyeok Moon"
date: 2024-02-06
title: 마크다운(markdown) KaTex 공식 정렬 시 번호 제거
categories: 마크다운
tags: [KaTex]
showtoc: false
weight: 10
---

마크다운에서 아래와 같이 식을 정렬하고 싶을 때가 있다.

```Markdown
$$
f(x) = ax_1 + bx_2 = cx_3 + dx_4 = ex_5 + fx_6\\\
\downarrow\\\
\begin{align}
f(x) &= ax_1 + bx_2\\\
&= cx_3 + dx_4\\\
&= ex_5 + fx_6\\\
\end{align}
$$
```

$$
f(x) = ax_1 + bx_2 = cx_3 + dx_4 = ex_5 + fx_6\\\
\downarrow\\\
\begin{align}
f(x) &= ax_1 + bx_2\\\
&= cx_3 + dx_4\\\
&= ex_5 + fx_6\\\
\end{align}
$$

그럼 이렇게 정렬된 식 우측에 (1), (2), $\cdots$ 와 같이 번호가 부여되는데, 등호(=)기준으로 정렬해야 하는 상황에서는 별다른 문제가 없지만 아래와 같은 상황에서는 문제가 발생한다.

``` markdown
$$
f(x) = ax_1 + bx_2 + cx_3 + dx_4 + ex_5 + fx_6\\\
\downarrow\\\
\begin{align}
f(x) =& ax_1 + bx_2\\\
&+ cx_3 + dx_4\\\
&+ ex_5 + fx_6\\\
\end{align}
$$
```

$$
f(x) = ax_1 + bx_2 + cx_3 + dx_4 + ex_5 + fx_6\\\
\downarrow\\\
\begin{align}
f(x) =& ax_1 + bx_2\\\
&+ cx_3 + dx_4\\\
&+ ex_5 + fx_6\\\
\end{align}
$$
