# 1. Fourier Series

## 1.1 Choices: Welcome Aboard

* The question of convergence of Fourier series, believe it or not, led 
  G. Cantor near the turn of the 20th century to investigate and invent 
  the theory of infinite sets and to distinguish diﬀerent cardinalities 
  of infinite sets.

## 1.2 

### 1.2.1. Time and space.

The frequency and wavelength are related through the equation $v = λν$, which is the
same as speed = distance/time.

More on spatial periodicity.

* a crystal has a regular, repeating 
  pattern of atoms in space; the 
  arrangement of atoms is called a lattice. 
  The function that describes the electron 
  density distribution of the crystal is 
  then a periodic function of the spatial 
  variables, in three dimensions, that 
  describes the crystal.

### 1.2.2. Definitions, examples, and things to come.

$f(t)$ is defined on $\mathbb{R}$. The 
smallest $T$ such that

$$f(t+T) = f(t)$$

is called the *fundamental period* of the 
function.

* Is the sum of two periodic functions periodic?

No, consider $\cos t$ and $\cos \sqrt[]{2}t$.

### 1.2.3. The building blocks: A few more examples.

The state of the harmonic oscillator system 
is described by a single sinusoid, say of 
the form

$$ 
A \sin (2 \pi \nu t + \phi )
$$

The period is $\nu$.

When Fourier consider the problem when a
ring is heated up, he came to the idea that
the distribution of temperature can be
modeled as a sum of sinusoids

$$ 
\sum_{n=1}^{N}
A_n \sin (n \theta + \phi_n)
$$

## 1.3 It All Adds Up

It's a little bit awkward to use the above equation

$$ 
\sum_{n=1}^{N}
A_n \sin (2 \pi n t + \phi_n)
$$

It’s more common to write a general trigonometric sum as

$$
\tag{1-3-1}
\frac{a_0}{2} +
\sum_{n = 1}^{N} a_n \cos (2πnt) + b_n \sin (2πnt)
$$

The above 2 equations are the same, because we have
$\sin(α+β) = \sinα\cosβ +\cosα\sinβ$.

$$ 
\sin (2 \pi n t + \phi_n) = \\
\sin (2 \pi n t) \cos (\phi_n) + \cos (2 \pi n t) \sin (\phi_n)
$$

And let $a_n = \sin (\phi_n), b_n = \cos (\phi_n)$, then
we can see they are the same.

#### Using complex exponentials.

Now from Appendix B, we know

$$ 
\cos (2 \pi n t) =
\frac{
  e^{2πint} + e^{-2πint}
}{2},
\quad
\sin (2 \pi n t) =
\frac{
  e^{2πint} - e^{-2πint}
}{2i}
$$

Then we can rearrange and simplify the equation (1-3-1).

$$ 
\sum_{n = -N}^{N} c_n e^{2πint} \\
c_0 = \frac{a_0}{2} \\
c_n = a_n - i b_n, \text{ for } n > 0,\\
c_n = a_n + i b_n, \text{ for } n < 0.\\
$$

Let

$$ 
f(t) = \sum_{n = -N}^{N} c_n e^{2πint}
$$

Note, $c_n$ can be complex numbers. If $f(t)$ is real,
then

$$ 
\overline{f(t)} = \sum_{n = -N}^{N} \overline{c_n e^{2πint}}
= \sum_{n = -N}^{N} \overline{c_n} e^{-2πint} = f(t)
$$

So we have

$$ 
\overline{c_n} = c_{-n}
$$

On the other hand, if $c_n$ satisfy $\overline{c_n} = c_{-n}$,

$$ 
f(t) = \sum_{n = -N}^{N} c_n e^{2πint} \\
= c_0 + \sum_{n = 1}^{N} c_n e^{2πint} + c_{-n} e^{-2πint} \\
= c_0 + \sum_{n = 1}^{N} 2\Re(c_n e^{2πint}) \\
= c_0 + \Re\left\{ \sum_{n = 1}^{N} c_n e^{2πint} \right\}
$$

$\square$

### 1.3.1. Lost at c.

Let

$$ 
f(t) = \sum_{n = -N}^{N} c_n e^{2πint}
$$

and we want to solve $c_k$. Rearrange it a little bit

$$ 
c_k = e^{-2πikt} f(t) - e^{-2πikt} \sum_{n \neq k} c_n e^{2πint} \\
= e^{-2πikt} f(t) - \sum_{n \neq k} c_n e^{2πi(n-k)t}
$$

> This is as far as algebra will take us, and when algebra is 
> exhausted, the desperate mathematician will turn to calculus,
> i.e., to diﬀerentiation or integration.
> Here’s a hint: diﬀerentiation won’t get you anywhere.

Another idea is needed, and that idea is integrating both sides from 0 to 1.

Note

$$ 
\int_{0}^{1} e^{2πi(n-k)t} dt = \\
\frac{1}{2πi(n-k)} e^{2πi(n-k)t} \bigg|_{0}^{1} = \\
\frac{1}{2πi(n-k)} (e^{2πi(n-k)} - 1) = 0
$$

So

$$ 
c_k = \int_{0}^{1} e^{-2πikt} f(t) dt
$$

Let’s summarize and be careful to note what we’ve done here, and 
what we haven’t done. We’ve shown that if we can write a periodic 
function $f(t)$ of period $1$ as a sum

$$ 
f(t) = \sum_{n = -N}^{N} c_n e^{2πint}
$$

then the coeﬃcients $c_n$ must be given by

$$ 
c_n = \int_{0}^{1} e^{-2πint} f(t) dt.
$$

We have not shown that every periodic function can be expressed 
this way.

If we assume $f(t)$ is real, then

$$ 
\overline{c_n} =
\overline{\int_{0}^{1} e^{-2πint} f(t) dt} =
\int_{0}^{1} \overline{e^{-2πint} f(t) dt} = \\
\int_{0}^{1} \overline{e^{-2πint}} f(t) dt = \\
\int_{0}^{1} e^{2πint} f(t) dt = c_{-n}
$$

$\square$

### 1.3.2. Fourier coeﬃcients.

This sum is called Fourier Series

$$ 
\sum_{n = -N}^{N} c_n e^{2πint}
$$

Fourier coefficients, hip version

$$ 
\hat{f}(n) = \int_{0}^{1} e^{-2πint} f(t) dt
$$

The next step is to show given any $a$,

$$ 
\hat{f}(n) = \int_{a}^{a+1} e^{-2πint} f(t) dt
$$

In "Understanding Analysis", we learned that the 2nd part
of The Fundamental Theorem of Calculus, if $g(x)$ is integrable,
and $G(x) = \int_{a}^{x} g(x)$. If $g(x)$ is continuous at $x$,
then $G'(x) = g(x)$.

Then let 

$$ 
G(a) = \int_{0}^{a} g(x) \\
H(a) = \int_{0}^{a+1} g(x)
$$

Then

$$ 
G'(a) = g(a), H'(a) = G'(a+1) = g(a+1)
$$

So $\frac{d}{da} \int_{a}^{a+1} g(x) = g(a+1) - g(a)$.

We assume this is also true for the complex function.
Then

$$ 
\frac{d}{da} \hat{f}(n) =
e^{-2πint} f(t) \bigg|_{a}^{a+1} \\
= e^{-2πin(a+1)} f(a+1) - e^{-2πina} f(a) \\
= e^{-2πin} e^{-2πina} f(a+1) - e^{-2πina} f(a) \\
= e^{-2πina} f(a+1) - e^{-2πina} f(a) \\
= 0 \\
$$

That means $\hat{f}(n)$ is independent of $a$.

There are times when the following is helpful — integrating over a symmetric interval, that is.

$$ 
\int_{-1/2}^{1/2} e^{-2πint} f(t)dt
$$

#### Symmetry relations.

If $f(t)$ is real, we have seen

$$ 
\overline{c_n} = c_{-n} \Leftrightarrow 
\overline{\hat{f}(n)} = \hat{f}(-n) \\
\Rightarrow \\
|\overline{\hat{f}(n)}| = |\hat{f}(-n)|
$$

So the magnitude of the Fourier coeﬃcients is
an even function of $n$.

Now assume $f(t)$ is even function
We have

$$
\begin{split}
\hat{f}(-n) &= \int_{0}^{1} e^{-2πi(-n)t} f(t) dt \\
&= \int_{0}^{1} e^{-2πi(-n)t} f(-t) dt
\end{split}
$$

Now let $t = g(s) = -s$ and recall the change-of-variable formula

$$ 
\int_{a}^{b} f(g(x)) g'(x) dx =
\int_{g(a)}^{g(b)} f(t) dt
$$

We have

$$
\int_{0}^{1} e^{-2πi(-n)t} f(t) dt = 
\int_{0}^{-1} e^{-2πi(-n)(-s)} f(-s) g'(s) ds\\
 = -\int_{0}^{-1} e^{-2πins} f(s) ds\\
 = \int_{-1}^{0} e^{-2πins} f(s) ds\\
 = \hat{f}(n)
$$

So we have

$$ 
\hat{f}(-n) = \hat{f}(n)
$$

$\square$

* If $f(t)$ is even, then the Fourier coeﬃcients $\hat{f}(n)$ are also even.
* If $f(t)$ is real and even, then the Fourier coeﬃcients $\hat{f}(n)$ are also real and even.

Now assume $f(t)$ is odd function.
We have

$$
\begin{split}
\hat{f}(-n)
&= \int_{0}^{1} e^{-2πi(-n)t} f(t) dt \\
&= -\int_{0}^{-1} e^{-2πi(-n)(-s)} f(-s) dt \\
&= \int_{0}^{-1} e^{-2πins} f(s) dt \\
&= -\int_{-1}^{0} e^{-2πins} f(s) dt \\
&= - \hat{f}(n)
\end{split}
$$

* If $f(t)$ is odd, then the Fourier coeﬃcients $\hat{f}(n)$ are also odd.
* If $f(t)$ is real and odd, then the Fourier coeﬃcients $\hat{f}(n)$ are odd and purely imaginary.

> If we think of $\hat{f}(n) = \int_{0}^{1} e^{-2πint}f(t)dt$
> as a transform of $f$ to a new function $\hat{f}(n)$.
> While $f(t)$ is defined for a continuous variable $t$,
> the transformed function $\hat{f}(n)$ is defined on the
> integers. **There are reasons for this that are much deeper
> than simply solving for the unknown coeﬃcients in a
> Fourier series.**

### 1.3.3. Period, frequencies, and spectrum.

We’re assuming that $f(t)$ is a real, periodic signal of period
$1$ with a representation as the series

$$ 
f(t) = \sum_{n = -\infty }^{\infty}
\hat{f}(n) e^{2πint}
$$

* Rather, being able to write f(t) as a Fourier series means that
  it is synthesized from many harmonics, many frequencies, 
  positive and negative, perhaps an infinite number.
* The set of frequencies n that are present in a given 
  periodic signal is the spectrum of the signal.

For a real signal, $\overline{\hat{f}(n)} = \hat{f}(-n)$.
Then the coeﬃcients $\hat{f}(n)$ and $\hat{f}(-n)$ are either both 
zero or both nonzero.

If the coeﬃcients are all zero from some point on, say
$\hat{f}(n) = 0 \text{ for } |n| > N$, it’s common to say that the 
signal has no spectrum from that point on. One also
says in this case that the signal is bandlimited and that the 
bandwidth is $2N$.

$|\hat{f}(n)|^2$ is said to be the energy of
the (positive and negative) harmonic $e^{\pm  2πint}$.

The sequence of squared magnitudes $|\hat{f}(n)|^2$ is called the energy spectrum or the power spectrum.

Rayleigh’s identity:

$$ 
\int_{0}^{1} |f(t)|^2 dt =
\sum_{n = -\infty }^{\infty} |\hat{f}(n)|^2
$$

#### Viewing a signal: Why do musical instruments sound diﬀerent?

* why do two instruments sound diﬀerent even when they are playing 
  the same note?
    * It’s because the note that an instrument produces is not a 
      single sinusoid of a single frequency, not a pure A at 440 
      Hz, for example, but a sum of many sinusoids each of its own
      frequency and each contributing its own amount of energy.
    * two instruments sound diﬀerent because of the diﬀerent
      harmonics they produce and because of the diﬀerent strengths 
      of the harmonics.

* To oversimplify, your inner ear (the cochlea) finds the 
  harmonics and their amounts (the key is resonance) and
  passes that data on to your brain to do the synthesis. Nature 
  knew Fourier analysis all along!

### 1.3.4. Changing the period, and another reciprocal relationship.

Suppose $f(t)$ has period $T$. Then let $g(t) = f(Tt)$,

$$ 
g(t+1) = f(T(t+1)) = f(Tt + T) = f(Tt) = g(t)
$$

So $g$ has period of $1$.

$$ 
g(t) = \sum_{n = -\infty}^{\infty} c_n e^{2πint}
$$

Let $s = Tt$

$$ 
f(s) = g(t) =
\sum_{n = -\infty}^{\infty} c_n e^{2πint} =
\sum_{n = -\infty}^{\infty} c_n e^{2πins/T}
$$

Also

$$ 
c_n = \int_{0}^{1} e^{-2πint} g(t) dt \\
= \frac{1}{T} \int_{0}^{T} e^{-2πin s/T} f(s) ds
$$

Sometimes, it's useful to write

$$ 
c_n
= \frac{1}{T} \int_{-T/2}^{T/2} e^{-2πin s/T} f(s) ds
$$

Or take the harmonics as

$$
\frac{1}{\sqrt[]{T}} e^{2πint/T}
\\
c_n
= \frac{1}{\sqrt[]{T}} \int_{0}^{T} e^{-2πint/T} f(t) dt
$$

#### Time domain – frequency domain reciprocity.

Given

$$ 
f(t) = \sum_{n = -\infty}^{\infty}
c_n e^{2πint/T}
$$

* In the time domain the signal repeats after T seconds, while the 
  points in the spectrum are $0, ±1/T, ±2/T, ...$, which are 
  spaced $1/T$ apart.
* This is worth elevating to an aphorism:
    * The larger the period in time, the smaller the spacing in
      the spectrum. The smaller the period in time, the larger the 
      spacing in the spectrum.
