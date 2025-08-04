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
