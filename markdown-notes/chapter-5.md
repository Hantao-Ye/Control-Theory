# Chapter 5 Frequency Response Analysis

## 5-1 Frequency Response

### Introduction

Consider the low-pass filter built by RC circuit, the transfer function of the filter is

$$
G(s) = \frac{1}{CRs+1}\Big|_{T=CR}=\frac{1}{Ts+1}
$

if the input voltage signal is $A\sin(\omega t)$

$$
U_o(t) = \frac{A\omega T}{1+\omega^2 T^2}e^{-\frac{t}{T}}+\frac{A}{\sqrt{1+\omega^2T^2}}\sin(\omega t-\arctan\omega T)
$$

Where the latter component is called as the **frequency response**

### Definition

The ratio of the complex vector of the steady-state output versus sinusoid input for a linear system

$$
G(j\omega) = \frac{C(j\omega)}{R(j\omega)}
$$

- $C(j\omega)$: complex vector representation of the output
- $R(j\omega)$: complex vector representation of the input

Or it could be rewritten as

$$
G(j\omega) = \|G(j\omega)\|\angle{G(j\omega)}
$$

- $A(j\omega)$: magnitude response
- $\phi(j\omega)$: phase response

$$
\begin{aligned}
    \|G(j\omega)\| &=\frac{\|C(j\omega)\|}{\|R(j\omega)\|}\\[2ex]
    \angle{G(j\omega)} &=\angle{C(j\omega)}-\angle{R(j\omega)}
\end{aligned}
$$