# ISyE 6525 HW2 - Question 1

## (a) Between-class variance

Let \(N=mn\) be the total number of pixels. Define the two class-indicator functions by

$$
I_1(x_{ij})=
\begin{cases}
1, & x_{ij}\le t,\\
0, & x_{ij}>t,
\end{cases}
\qquad
I_2(x_{ij})=
\begin{cases}
1, & x_{ij}>t,\\
0, & x_{ij}\le t.
\end{cases}
$$

Therefore,

$$
I_1(x_{ij})+I_2(x_{ij})=1.
$$

The class weights and class means can be written as

$$
\omega_k
=\frac{1}{N}\sum_{i=1}^{m}\sum_{j=1}^{n}I_k(x_{ij}),
\qquad
\mu_k
=\frac{\displaystyle\sum_{i=1}^{m}\sum_{j=1}^{n}x_{ij}I_k(x_{ij})}
{\displaystyle\sum_{i=1}^{m}\sum_{j=1}^{n}I_k(x_{ij})},
\qquad k\in\{1,2\}.
$$

Hence,

$$
\sum_{i=1}^{m}\sum_{j=1}^{n}I_k(x_{ij})=N\omega_k,
\qquad
\sum_{i=1}^{m}\sum_{j=1}^{n}x_{ij}I_k(x_{ij})
=N\omega_k\mu_k.
$$

The total mean is therefore

$$
\begin{aligned}
\mu_T
&=\frac{1}{N}\sum_{i=1}^{m}\sum_{j=1}^{n}x_{ij}\\
&=\frac{1}{N}\sum_{i=1}^{m}\sum_{j=1}^{n}
x_{ij}\bigl(I_1(x_{ij})+I_2(x_{ij})\bigr)\\
&=\omega_1\mu_1+\omega_2\mu_2.
\end{aligned}
$$

Expanding the total variance gives

$$
\begin{aligned}
\sigma_T^2
&=\frac{1}{N}\sum_{i=1}^{m}\sum_{j=1}^{n}(x_{ij}-\mu_T)^2\\
&=\frac{1}{N}\sum_{i=1}^{m}\sum_{j=1}^{n}x_{ij}^2-\mu_T^2.
\end{aligned}
$$

For each class,

$$
\sigma_k^2
=\frac{\displaystyle\sum_{i=1}^{m}\sum_{j=1}^{n}
I_k(x_{ij})(x_{ij}-\mu_k)^2}
{\displaystyle\sum_{i=1}^{m}\sum_{j=1}^{n}I_k(x_{ij})}.
$$

Thus, the within-class variance can be expressed using the indicators as

$$
\begin{aligned}
\sigma_w^2
&=\omega_1\sigma_1^2+\omega_2\sigma_2^2\\
&=\frac{1}{N}\sum_{i=1}^{m}\sum_{j=1}^{n}
\left[
I_1(x_{ij})(x_{ij}-\mu_1)^2
+I_2(x_{ij})(x_{ij}-\mu_2)^2
\right]\\
&=\frac{1}{N}
\left[
\sum_{i=1}^{m}\sum_{j=1}^{n}
x_{ij}^2\bigl(I_1(x_{ij})+I_2(x_{ij})\bigr)
-2\mu_1\sum_{i=1}^{m}\sum_{j=1}^{n}x_{ij}I_1(x_{ij})
-2\mu_2\sum_{i=1}^{m}\sum_{j=1}^{n}x_{ij}I_2(x_{ij})
\right.\\
&\hspace{3.7cm}\left.
+\mu_1^2\sum_{i=1}^{m}\sum_{j=1}^{n}I_1(x_{ij})
+\mu_2^2\sum_{i=1}^{m}\sum_{j=1}^{n}I_2(x_{ij})
\right]\\
&=\frac{1}{N}\sum_{i=1}^{m}\sum_{j=1}^{n}x_{ij}^2
-\omega_1\mu_1^2-\omega_2\mu_2^2.
\end{aligned}
$$

It follows that

$$
\begin{aligned}
\sigma_b^2
&=\sigma_T^2-\sigma_w^2\\
&=\omega_1\mu_1^2+\omega_2\mu_2^2-\mu_T^2\\
&=\omega_1\mu_1^2+\omega_2\mu_2^2
-\left(\omega_1\mu_1+\omega_2\mu_2\right)^2\\
&=\omega_1(1-\omega_1)\mu_1^2
+\omega_2(1-\omega_2)\mu_2^2
-2\omega_1\omega_2\mu_1\mu_2.
\end{aligned}
$$

Since \(\omega_1+\omega_2=1\), we have
\(1-\omega_1=\omega_2\) and \(1-\omega_2=\omega_1\). Therefore,

$$
\boxed{
\sigma_b^2(t)
=\omega_1(t)\omega_2(t)
\left(\mu_1(t)-\mu_2(t)\right)^2
}.
$$

## (b) Endpoint behavior

<!-- TODO: Explain the behavior at t = 0 and t = 255 and the two competing effects. -->
