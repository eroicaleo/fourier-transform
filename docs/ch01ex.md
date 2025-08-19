# 1. Fourier Series

## 1.1. Playing with Fourier series using MATLAB

**Solution**: Since I do not have the matlab code yet,
I use python to draw the following:

```python
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.ticker import MultipleLocator

# ex 1.1

# Generate x values from 0 to 10 with a step of 0.1
t = np.arange(0, 2, 0.01)

# Calculate the amplitude as the sine of the time values
f = np.zeros_like(t)
for n in range(5):
    amp = -15.0 / (1+n);
    phase = -0.1 * n
    f += amp * np.sin(2*np.pi*n*t + phase)

# Plot the sine wave
plt.plot(t, f)

# Add labels and title
plt.title('Sine wave')
plt.xlabel('Time')
plt.ylabel('Amplitude = sin(time)')
plt.gca().xaxis.set_major_locator(MultipleLocator(0.2))

# Add a grid and a horizontal line at y=0
plt.grid(True, which='both')
plt.axhline(y=0, color='k')

# Display the plot
plt.show()
```

![](./assets/ex0101.png)

## 1.2. Adding periodic functions

You can sometimes be misled by thinking too casually about 
modifying or combining periodic functions: scaling a periodic 
function results in a periodic
function; shifting a periodic function results in a periodic 
function. What about adding?

(a) Let $f(x) = \sin(2πmx) + \sin(2πnx)$ where $n$ and $m$ are positive integers. Is $f(x)$ periodic? If so, what is its period?

**Solution**:

Yes, because apprantly $f(x+1) = f(x)$.
If $d = \gcd(m, n)$, then $T = \frac{1}{d}$.

I cannot prove it though.

(b) Let $g(x) = \sin(2πpx) + \sin(2πqx)$ where $p$ and $q$ are 
positive rational numbers (say $p= m/r$ and $q= n/s$, as fractions 
in lowest terms). Is $g(x)$ periodic? If so, what is its period?

**Solution**:

Yes, the period is

$$ 
\frac{\text{lcm}(r,s)}{\gcd(m,n)}
$$

$\square$

(c) It’s not true that the sum of two periodic functions is 
periodic. For example, show that $f(t) = \cos t+\cos \sqrt[]{2} t$ 
is not periodic. (Hint: Suppose by way of contradiction that there 
is some $T$ such that $f(t+T) = f(t)$
for all $t$. In particular, the maximum value of $f(t)$ repeats. 
This will lead to a contradiction.)

**Proof**: 

Based on the hint, note that when $t=0$, $f(t)$ reaches its
maximum, i.e. $2$. Note assume $f(t+T) = f(t)$, especially
$f(T) = f(0) = 2$ 
.

$$ 
T = 2 n \pi \\
\sqrt[]{2} T = 2 m \pi \\
$$

Then we have

$$ 
\sqrt[]{2} = \frac{m}{n}
$$

This is not possible.

So $f(t)$ is not a periodic function.

## 1.3 Periods of sums and products

Let $f(t) = \sin3t+\cos5t$ and $g(t) = \sin3t·\cos5t$

(a) What is the period of $f(t)$?
Find the Fourier series for $f(t)$.

**Solution**:

The period of $\sin 3t$ is $2/3 \pi$, and the period of $\cos5t$
is $2/5 \pi$. Since $3, 5$ are coprime, then their common period
has to be $2 \pi$.

$$
\begin{split}
c_n &= \frac{1}{2π} \int_{0}^{2 \pi } \sin 3t · e^{-2πint / (2π)} \\
&= \frac{1}{2π} \int_{0}^{2 \pi } \sin 3t · e^{-int} \\
&= \frac{1}{2π} \int_{-\pi}^{\pi} \sin 3t · (\cos (-nt) + i \sin (-nt)) \\
&= \frac{1}{2π} \int_{-\pi}^{\pi} \sin 3t · (\cos (nt) - i \sin (nt)) \\
\end{split}
$$

We use the conclusion from Understanding Analysis Exercise 8.5.2.

$$ 
c_n =
\begin{cases}
    -i/2 &\text{if }  n = 3  \\
    i/2 &\text{if } n = -3 \\
    0 &\text{else}\\
\end{cases}
$$

So

$$ 
\sin 3t = \frac{i}{2} e^{-3it} - \frac{i}{2} e^{3it}
$$

On the hindsight, we can just use the complex number knowledge in
Appendix B to get this.

For the same reason

$$ 
\cos 5t = \frac{1}{2} e^{5it} - \frac{1}{2} e^{-5it}
$$

So

$$ 
\sin 3t + \cos 5t =
- \frac{1}{2} e^{-5it} + \frac{i}{2} e^{-3it}
- \frac{i}{2} e^{3it} + \frac{1}{2} e^{5it}
$$

$\square$

(b) Find the Fourier series for $g(t)$. What is the period of
$g(t)$? (The period of the product is more interesting. The 
product repeats every $2π$, that is, $g(t+2π) = g(t)$, so the 
period of $g(t)$ is a divisor of $2π$. To determine the 
fundamental frequency of $g(t)$, we find its Fourier series.)

**Solution**:

$$
\begin{split}
\sin3t·\cos5t &=
\frac{e^{3it} - e^{-3it}}{2i} \cdot
\frac{e^{5it} + e^{-5it}}{2} \\
&=\frac{1}{4i}
(-e^{-8it} + e^{-2it} - e^{2it} + e^{8it})
\end{split}
$$

From this Fourier series, we can see, $π$ is a period.

$$ 
\sin 3(t+π) \cdot \cos 5(t+π) \\
= (- \sin 3t) \cdot (-\cos 5(t)) \\
= \sin3t·\cos5t
$$

$\square$
