# Chapter 3

## 3-1 Transient and Steady-State Response Analysis

The time response of a control system consists of two parts: the transient response and the steady-state response

- **transient response**: goes from the initial state to the final state
- **steady-state response**: the manner in which the system output behaves as $t\to\infty$

$$
y(t) = \mathscr{L}^{-1}\Big[G(s)H(s)\Big]=y_t(t)+y_s(t)
$$

in other words

$$
\text{time response}=\text{transient response}+\text{steady-state response}
$$

### Transient Response

<div align = center><img src = "../assets/ch3-1.png"></div>

The transient performance could be measured in terms of the transient response to a unit-step input, and there are some specifications 

- $t_d$: **delay time**, the time of the response to reach half the final value
- $t_r$: **rise time**, the time of the response rise from $10\%$ to $90\%$ or $0\%$ to $100\%$ of its final value
- $t_p$: **peak time**, the time required for the response to reach the first peak of the overshoot
- $t_s$: **setting time**, the time required for the response curve to reach and stay within a range about the final value of size specified by absolute percentage of the final value (usually $5\%$ or $2\%$)
- $\sigma\%$: **maximum overshoot**, it is defined by $[c(t_p)-c(\infty)]/c(\infty)\times 100\%$

> **Response speed** is measured by rise time, delay time and setting time
> **Relative stability** is measured by percent overshoot

And there could also be error after the transient response has delayed, leaving only the continuous response

$$
e_{ss} = \lim_{t\to\infty}{e(t)} = e(\infty)
$$

## 3-2 First-Order Systems

<div align = center><img height = 200 src = "../assets/ch3-2.png"></div>

Consider the first-order system in the figure above, the input-output relationship is given by

$$
\frac{C(s)}{R(s)} = \frac{\frac{1}{Ts}}{1+\frac{1}{Ts}} = \frac{1}{Ts}
$$

### Unit-Step Response of First-Order Systems

Since the Laplace transform of the unit step function is $1/s$, the unit step response of the system is

$$
C(s) = \frac{1}{Ts+1}\frac{1}{s}=\frac{1}{s}-\frac{1}{s+(1/T)}
$$

Taking the inverse Laplace transform, we could obtain that

$$
c(t) = 1 - e^{-t/T}
$$

- $1$: steady-state response
- $e^{-t/T}$: transient response
  
<div align = center><img height = 400 src = "../assets/ch3-3.png"></div>

- Steady-State Error is 0
- Setting time is about 3T to 4T
- Smaller the time constant T is, the faster the system response

## 3-3 Second-Order Systems

$$
G(s) = \frac{\omega_n^2}{s^2+2\zeta\omega_n s+\omega_n^2}
$$

- $\omega_n$: undamped natural frequency
- $\zeta$: damping ratio

<div align = center><img height = 200 src = "../assets/ch3-4.png"></div>

which has the characteristic equation of 

$$
s^2+2\zeta \omega_n s+\omega_n^2=0
$$

and the closed loop poles

$$
s_{1,2} = -\zeta \omega_n\pm\omega_n\sqrt{\zeta^2-1}
$$

| Classifications of second order systems | The number of $\zeta$ |
| :-------------------------------------: | :-------------------: |
|             Overdamped Case             |       $\zeta>1$       |
|         Critically Damped Case          |       $\zeta=1$       |
|            Underdamped Case             |      $0<\zeta<1$      |
|          Undamped Damped Case           |       $\zeta=0$       |

<div align = center><img height = 500 src = "../assets/ch3-5.png"></div>

### Overdamped Case

Since the poles are

$$
s_{1,2} = -\zeta\omega_n\pm\omega_n\sqrt{\zeta_2-1}
$$

which means they are all real

And the output gives the following response

$$
c(t) = 1+\frac{1}{\frac{s_1}{s_2}-1}e^{s_1t}+\frac{1}{\frac{s_2}{s_1}-1}e^{s_2t}
$$

which includes two delaying exponential terms

> If $s_1$ is located very much closer to the $j\omega$ asia than $s_2$, then the effect of $s_2$ on the response is much smaller than that of $s_1$, which response is similar to that of a **first-order** system

### Critically Damped Case

The poles become to

$$
s_{1,2} = -\omega_n
$$

And the output gives the following response

$$
C(t) = 1-(1+\omega_n t)e^{-\omega_n t}
$$

### Underdamped Case

There are two complex conjugate poles for this case

$$
s_{1,2} = -\zeta \omega_n \pm j\omega_n\sqrt{1-\zeta^2}
$$

And the unit-step response becomes

$$
c(t) = 1-\frac{e^{-\zeta \omega_n t}}{\sqrt{1-\zeta^2}}\sin(\omega_d t+\beta)
$$

- $\beta$ =  $\arccos(\zeta)$
- damped natural frequency: $\omega_d = \omega_n\sqrt{1-\zeta^2}$

$$
\sigma\% =\frac{y(t_p)-y(\infty)}{y(\infty)}\times 100\% = e^{-\frac{\pi \zeta}{\sqrt{1-\zeta^2}}}
$$

and the setting time of it are

$$
\begin{aligned}
    t_s = \frac{3}{\zeta \omega_n}(\Delta = 0.05)\\[2ex]
    t_s = \frac{4}{\zeta \omega_n}(\Delta = 0.02)\\[2ex]
\end{aligned}
$$

### Undamped Case

There're two poles both on $j\omega$ axis

$$
s_{1,2} = \pm j\omega_n
$$

And the unit-step response is 

$$
c(t) = 1-\cos\omega_nt
$$

**Remarks**

- if two second-order systems have the same $\zeta$ but different $\omega_n$, they will exhibit the same overshoot asn the same oscillatory, which is called to have the **same relative stability**
- underdamped system with $\zeta$ between 0.5 and 0.8 gets close to the final value more rapid ly than a critically or overdamped system
- overdamped system is always sluggish in responding to any inputs

## 3-5 Stability Analysis of the n-th Order Systems

$$
\frac{C(s)}{R(s)} = \frac{b_m s^m+b_{m-1}s^{m-1}+\cdots+b_1 s+b_0}{a_n s^n+a_{n-1}s^{n-1}+\cdots+a_1 s+a_0}=\frac{N(s)}{D(s)}
$$

For the unit step response

$$
C(s) = R(s)G(s) = \frac{1}{s}\frac{N(s)}{D(s)}=\frac{K\prod_{i=1}^m(s+z_i)}{\prod_{j=1}^q(s+p_j)\prod_{k=1}^r(s+\alpha_k)^2+\beta_k^2}
$$

In the time domain

$$
c(t) = a+\sum_{j=1}^q{b_j e^{-p_j t}}+\sum_{k=1}^r{A_ke^{-\alpha_k t}}\sin(\beta_k t+\theta_k)
$$

- real poles contribute exponential terms
- complex pair of poles contribute damped oscillations
- magnitude of contribution depends on residues

### Stability of System Response

The transient term will converge to zero if and only if **all poles** are on the **left-hand of plains** (LHP), and the further to the left on the LHP for the poles, the faster the convergence.

#### Method 1: Direct Factorization

Solve for solutions of characteristic equation

$$
a_0s^n+a_1s^{n-1}+\cdots+a_{n-1}s+a_n=0
$$

and check if all of them are on the LHP

#### Method 2: Routh's Stability Criterion

Determine the locations of roots without having to solve the equation

- step 1: determine if all the coefficients of the characteristic equation have the same sign and are nonzero or it is unstable
- step 2: if all coefficients are positive, arrange all coefficients in rows and columns to the following pattern, construct the Routh table

| power of s |             column 1              |             column 2              | column 3 | $\cdots$ |
| :--------: | :-------------------------------: | :-------------------------------: | :------: | :------: |
|   $s^n$    |               $a_0$               |               $a_2$               |  $a_4$   | $\cdots$ |
| $s^{n-1}$  |               $a_1$               |               $a_3$               |  $a_5$   | $\cdots$ |
| $s^{n-2}$  |  $b_1=\frac{a_1a_2-a_0a_3}{a_1}$  | $b_2 = \frac{a_1a_4-a_0a_5}{a_1}$ | $\cdots$ | $\cdots$ |
| $s^{n-3}$  |  $c_1=\frac{b_1a_3-a_1b_2}{b_1}$  |             $\cdots$              | $\cdots$ | $\cdots$ |
|  $\vdots$  |             $\vdots$              |             $\cdots$              | $\vdots$ | $\vdots$ |
|   $s^2$    |               $e_1$               |               $e_2$               |          |          |
|   $s^1$    |               $f_1$               |                $0$                |          |          |
|   $s^0$    | $g=\frac{f_1e_2-e_1\cdot 0}{f_1}$ |                                   |          |          |

##### Special Case 1

If the first element in any row of Rough's array is zero, but the others are not.

The zero element in the first column should be replaced by small positive number of $\epsilon$, then proceed with Rough's array

$$
s^3+2s^2+s+2 = 0
$$

the array of coefficients is

$$
\begin{aligned}
    s^4 &\quad 1\quad 1\quad 1\\[2ex]
    s^3 &\quad 2\quad 2\\[2ex]
    s^2 &\quad \varepsilon>0\quad 1\\[2ex]
    s^1 &\quad 2-\frac{2}{\varepsilon}\\[2ex]
    s^0 &\quad 1
\end{aligned}
$$

##### Special Case 2

An entire row of the Rough array may become zero, which indicates that there are roots of equal magnitude lying radially opposite in the s-plane

The situation can be remedied by forming an **auxiliary polynomial** with the coefficients of the last row.

$$
s^6+2s^5+7s^4+12s^3+14s^2+16s+8=0
$$

the array of coefficients is

$$
\begin{aligned}
    s^6 &\quad 1 \quad 7 \quad 14 \quad 8\\[2ex]
    s^5 &\quad 2 \quad 12 \quad 16 \quad 0\\[2ex]
    s^4 &\quad 1 \quad 6 \quad 8\\[2ex]
    s^3 &\quad 0 \quad 0 \quad 0\\[2ex]
    s^3 &\quad 4 \quad 12\\[2ex]
    s^2 &\quad 3 \quad 8\\[2ex]
    s^1 &\quad 4/3\\[2ex]
    s^0 &\quad 8
\end{aligned}
$$

the auxiliary polynomial is

$$
\begin{aligned}
    p(s) &= s^4+6s^2+8\\[2ex]
    \frac{\mathrm{d}p(s)}{\mathrm{d}s} &= 4s^3+12s
\end{aligned}
$$

#### Useful Tips for Stability

|       System        |          Equation          |                                 Tip                                  |
| :-----------------: | :------------------------: | :------------------------------------------------------------------: |
| First order system  |        $a_0s+a_1=0$        |                  $a_1$ and $a_0$ have the same sign                  |
| Second order system |    $a_0s^2+a_1s+a_2=0$     |              $a_2$, $a_1$ and $a_0$ have the same sign               |
| Third order system  | $a_0s^3+a_1s^2+a_2s+a_3=0$ | $a_3$, $a_2$, $a_1$ and $a_0$ have the same sign and $a_1a_2>a_0a_3$ |

## 3-6 Steady-State Errors in Feedback

<div align = center><img height = 250 src = "../assets/ch3-6.png"></div>

$$
e(t) = r(t)-b(t)
$$

- $e(t)$: error
- $r(t)$: reference input
- $b(t)$: feedback signal

Since the transfer function from the input or the disturbance to the error signal is

$$
\Phi_e(s) = \frac{E(s)}{R(s)}\qquad \Phi_{en}(s)=\frac{E(s)}{N(s)}
$$

Using the final value theorem to obtain the steady-state error

$$
e_{ss} = \lim_{s\to 0}s[\Phi_e(s)R(s)+\Phi_{en}(s)N(s)]
$$

The **steady-state error** is defined as

$$
e_{ss} = \lim_{t\to\infty}e(t)= \lim_{s\to 0}sE(s) = \lim_{s\to 0}s\Phi_e(s)R(s) = \lim_{s\to0}s\cdot\frac{1}{1+G(s)H(s)}\cdot R(s)
$$

> All roles of $sE(s)$ must lie on the left-half of the s-plane, which means the system is stable

### Classification of Control Systems

Consider a feed back control system with following open-loop transfer function

$$
G(s)H(s) = \frac{K_k\prod_{i=1}^m(T_is+1)}{s^N \prod_{j=1}^{n-N}(T_j s+1)}
$$

- $K_k$: open-loop gain
- $N$: the number of integrations

| the number of N | the system integration |
| :-------------: | :--------------------: |
|        0        |     type 0 system      |
|        1        |     type 1 system      |
|        2        |     type 2 system      |

### Steady-State Errors in Unity-Feedback Control Systems

<div align = center><img height = 250 src = "../assets/ch3-7.png"></div>

$$
e(t) = r(t)-c(t)
$$

The **steady-state error** is defined as

$$
e_{ss} = \lim_{t\to\infty}e(t) =  \lim_{s\to 0}sE(s) =\lim_{s\to0}\frac{sR(s)}{1+G(s)}
$$

#### Unit-Step Input

The input signal is the unit-step signal, where $R(s)=\frac{1}{s}$

$$
e_{ss} = \lim_{s\to 0} sE(s) = \lim_{s\to 0}s\Phi_e(s)R(s)=s\cdot \frac{1}{1+G(s)} \cdot \frac{1}{s} = \frac{1}{1+\lim_{s\to 0}G(s)}=\frac{1}{1+K_p}
$$

> $K_p = \lim_{s\to 0}G(s)$, which is defined as the static position error constant

##### Type 0 System

For the type 0 system, there is no difference between static position error constant

$$
K_p = K_k
$$

Therefore, the steady-state error becomes to

$$
e_{ss} = \frac{1}{1+K_k}
$$

##### Type 1 System

According to the definition of the static position error constant

$$
K_p = \lim_{s\to 0} \frac{K_k\prod_{i=1}^m(T_is+1)}{s \prod_{j=1}^{n-N}(T_j s+1)} = \infty
$$

Then the steady-state error becomes to

$$
e_{ss} = 0
$$

##### Type 2 System

Similar to the type 1 system

$$
K_p = \infty \qquad e_{ss} =0
$$

#### Unit-Ramp Input

The input signal is the unit-stamp signal, where $R(s) = \frac{1}{s^2}$

$$
e_{ss} = \lim_{s\to 0} sE(s) = \lim_{s\to 0}s\Phi_e(s)R(s)=\lim_{s\to 0}s\cdot \frac{1}{1+G(s)} \cdot \frac{1}{s^2} = \lim_{s\to 0}\frac{1}{sG(s)} = \frac{1}{K_v}
$$

> $K_v = \lim_{s\to 0}sG(s)$, which is defined as the static velocity error constant

##### Type 0 System

For the type 0 system, the steady-state error becomes to

$$
K_v = \lim_{s\to 0}sG(s) = 0
$$

Therefore, the steady-state error becomes to

$$
e_{ss} = \infty
$$

##### Type 1 System

There is no difference between the 

$$
K_v = K_k
$$

Then the steady-state error becomes to

$$
e_{ss} = \frac{1}{K_k}
$$

##### Type 2 System

$$
K_v = \infty \qquad e_{ss} =0
$$

#### Unit-Parabolic Input

The input signal is the unit-parabolic signal $r(t) = \frac{1}{2}t^2$, where $R(s) = \frac{1}{s^3}$

$$
e_{ss} = \lim_{s\to 0} sE(s) = \lim_{s\to 0}s\Phi_e(s)R(s)=\lim_{s\to 0}s\cdot \frac{1}{1+G(s)} \cdot \frac{1}{s^3} = \lim_{s\to 0}\frac{1}{s^2G(s)} = \frac{1}{K_a}
$$

> $K_a = \lim_{s\to 0}s^2G(s)$, which is defined as the static acceleration error constant

##### Type 0 System

For the type 0 system, the steady-state error becomes to

$$
K_a = \lim_{s\to 0}s^2G(s) = 0
$$

Therefore, the steady-state error becomes to

$$
e_{ss} = \infty
$$

##### Type 1 System

There is no difference between the 

$$
K_a = \lim_{s\to 0}s^2G(s) = 0
$$

Then the steady-state error becomes to

$$
e_{ss} = \infty
$$

##### Type 2 System

$$
K_a = K_k \qquad e_{ss} =\frac{1}{K_k}
$$

| System Type |    Step Input     |   Ramp Input    | Acceleration Input |
| :---------: | :---------------: | :-------------: | :----------------: |
|   Type 0    | $\frac{1}{K_k+1}$ |    $\infty$     |      $\infty$      |
|   Type 1    |         0         | $\frac{1}{K_k}$ |      $\infty$      |
|   Type 2    |         0         |       $0$       |  $\frac{1}{K_k}$   |

### Reduce or Eliminate the Steady State Error

- Method 1: increase the open-loop gain
- Method 2: increase the tpe of the system by adding a integrator or integrators to the feedforward path
- Method 3: feedforward compensation

#### Feedforward Compensation of Input

<div align = center><img src = "../assets/ch3-8.png"></div>

#### Feedforward Compensation of Disturbance

<div align = center><img src = "../assets/ch3-9.png"></div>