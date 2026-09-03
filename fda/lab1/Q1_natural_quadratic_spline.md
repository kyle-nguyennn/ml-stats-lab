# ISyE 6525 HW1 - Question 1

For the spline in the question, the outside expression is

$$
y(x)=\beta_1+\beta_2x+\sum_{k=1}^{K}\theta_k(x-\xi_k)_+^2,
\qquad x\text{ outside }(\xi_1,\xi_K),
$$

where

$$
(x-\xi_k)_+=\max(x-\xi_k,0).
$$

We want $y''(x)=0$ outside the boundary knots.

## Left of the first knot

If $x<\xi_1$, then every truncated term is zero. Therefore,

$$
y(x)=\beta_1+\beta_2x
$$

and hence

$$
y''(x)=0.
$$

Thus the left boundary condition is already satisfied.

## Right of the last knot

If $x>\xi_K$, then $(x-\xi_k)_+=x-\xi_k$ for every $k$. Differentiating twice gives

$$
\begin{aligned}
y'(x)
&=\beta_2+2\sum_{k=1}^{K}\theta_k(x-\xi_k),\\
y''(x)
&=2\sum_{k=1}^{K}\theta_k.
\end{aligned}
$$

Therefore, the right boundary condition requires

$$
\boxed{\sum_{k=1}^{K}\theta_k=0}.
$$

Equivalently,

$$
\theta_K=-\sum_{k=1}^{K-1}\theta_k.
$$

Substitute this into the truncated-power part:

$$
\begin{aligned}
\sum_{k=1}^{K}\theta_k(x-\xi_k)_+^2
&=\sum_{k=1}^{K-1}\theta_k(x-\xi_k)_+^2
  +\theta_K(x-\xi_K)_+^2\\
&=\sum_{k=1}^{K-1}\theta_k(x-\xi_k)_+^2
  -\left(\sum_{k=1}^{K-1}\theta_k\right)(x-\xi_K)_+^2\\
&=\sum_{k=1}^{K-1}\theta_k
\left[(x-\xi_k)_+^2-(x-\xi_K)_+^2\right].
\end{aligned}
$$

Define the new basis functions

$$
\boxed{
h_k(x)=(x-\xi_k)_+^2-(x-\xi_K)_+^2,
\qquad k=1,\ldots,K-1.
}
$$

For $x>\xi_K$,

$$
\begin{aligned}
h_k(x)
&=(x-\xi_k)^2-(x-\xi_K)^2\\
&=2(\xi_K-\xi_k)x+(\xi_k^2-\xi_K^2),
\end{aligned}
$$

which is linear in $x$. For $x<\xi_1$, $h_k(x)=0$. Thus $h_k''(x)=0$ on both outside regions.

To follow the piecewise form given in the question, also define

$$
q(x)=
\begin{cases}
x^2, & x\in[\xi_1,\xi_K],\\
0, & x\text{ outside }(\xi_1,\xi_K).
\end{cases}
$$

Then the spline can be written as

$$
y(x)=\beta_1+\beta_2x+\beta_3q(x)
+\sum_{k=1}^{K-1}\theta_k h_k(x).
$$

Therefore, one set of basis functions is

$$
\boxed{
1,\quad x,\quad q(x),\quad h_1(x),\ldots,h_{K-1}(x).
}
$$

This basis builds the constraint into the representation, so the remaining coefficients are unrestricted.
