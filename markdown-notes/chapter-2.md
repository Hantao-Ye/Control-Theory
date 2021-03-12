# Chapter 2

## Transfer Function and Impulse Response Function

### Transfer Function

The *transfer function* of a linear, time-invariant, differential equation system defined as the **ratio** of the **Laplace transform of the output** to the **Laplace transform of the input** under the assumption that all initial conditions are zero

Consider the linear time-invariant system defined by the following differential equation

$$
\begin{aligned}
    a_0 y^{(n)}+a_1y^{(n-1)}&+\cdots+a_{n-1}\dot{y}+a_n y\\[2ex]
    &=b_0x^{(m)}+b_1x^{(m-1)}+\cdots+b_{m-1}\dot{x}+b_m x
\end{aligned}
$$

where $y$ is the output of the system and $x$ is the input

$$
\begin{aligned}
    \text{Transfer Function} &= G(s) = \frac{\mathscr{L}[\text{output}]}{\mathscr{L}[\text{input}]}\Bigg |_{\text{zero initial conditions}}\\[2ex]
    &= \frac{Y(s)}{X(s)} = \frac{b_0 s^m+b_1s^{m-1}+\cdots+b_{m-1}s+b_m}{a_0 s^n+a_1s^{n-1}+\cdots+a_{n-1}s+a_n}=\frac{N(s)}{D(s)}
\end{aligned}
$$

>1. the concept of transfer function is only appropriate to the LTI system
>2. transfer function is only determined by the structure and parameter of system
>3. if the highest power of $s$ in the **denominator** of the TF is equal to $n$, the system is called as **n-th system**

- **characteristic polynomial**: the denominator polynomial $D(s)$
- **characteristic equation**: the formula of $D(s) = 0$
- **zeros**: the roots of the **numerator polynomial** $N(s)$
- **poles**: the roots of the **denominator polynomial** $D(s)$

### Example

$$
G(s) = \frac{K(2s+1)}{s(3s+1)(T^2s^2+2\xi Ts+1)}
$$

which could be rewritten as

$$
G(s)= K\cdot \frac{1}{s}\cdot(2s+1)\cdot \frac{1}{3s+1}\cdot\frac{1}{T^2s^2+2\xi Ts+1}
$$

- $K$: gain factor
- $1/s$: integral factor
- $2s+1$: first-order differential factor (differential factor)
- $1/(3s+1)$: inertial element (reciprocal first-order)
- $1/(T^2s^2+2\xi Ts+1)$: quadratic factor