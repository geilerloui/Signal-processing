# Module 3: Part 1 - Basics of Fourier Analysis



## 3.1 Introduction to Fourier Analysis

### 3.1.a The frequency domain

<img src="images/im44.png" style="height:150px">



### 3.1.b The DFT as a change of basis

We will start with a finite-length signals (i.e. vectors in $\mathbb{C}^N$) to illustrate this, let's see a temporal signal, wheree we do not notice anything special.

<img src="images/im45.png" style="height:150px">

And the same signal in the frequency domain with a proper change of basis

<img src="images/im46.png" style="height:150px">

The Fourier basis will be

<img src="images/im47.png" style="height:175px">

We claim that

<img src="images/im48.png" style="height:175px">

We're going around the circle at each iteration, the second vector in the basis will be the second one



let's see a concrete example, with $N=64​$, we look at the real and imaginary part of the vector when the vector rotate around the circle



the second basis vector



the bigger the N the more it is difficult to image a sinusoide, but even at 16 we still have a sinusoids

add many images



## 3.2 The Discrete Fourier transform

### 3.2.a DFT definition



<img src="/Users/geilerloui/Documents/GitHub/Signal-processing/digital-signal-processing/images/im25.png" style="height:150px">







## 3.3 The DFT in Practice

### 

## 3.4 The Short-Time Fourier transform

### 