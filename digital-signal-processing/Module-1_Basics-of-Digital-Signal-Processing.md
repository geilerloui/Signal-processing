# Module 1: Basics of Digital Signal Processing



## 1.1 Introduction to Digital Signal Processing



**What is a signal ?**

---

It is a **description of the evolution of a physical phenomenon**.

* weather $\longrightarrow$ temperature

* sound $\longrightarrow$ pressure

* sound $\longrightarrow$ magnetic deviation

* light intensity $\longrightarrow$ gray level on paper

  

So, we have a signal then we have the processing part. And the processing part is where we make sense of this information that has been described by the signal. We can process the signal in two ways. 

* **Analysis:** We can analyze it, namely we want to understand the information carried by the signal and perhaps extract some more high level description. 

* **Synthesis:** Or we can synthesize a signal, that's also signal processing. And that's when we create a physical phenomenon that contains a certain amount of information, that we want to put out in the world. And this is really what we do when we transmit information, like when we use our cell phone or the radio, or when we generate sounds with a music synthesizer.



### Analog vs Digital signals : 



**Analog:**

---

Now if I show you a wave form like this, you probably have seen this before and you can guess that it is some sort of representation of a sound or speech. 

<img src="images/im2.png" style="height:150px">

And if we were to apply this mathematical model to this kind of information. The question is, what is the function that describes the sound? Well there's no really an easy answer for that. What I can try to do is record this information, and people have invented extremely sophisticated devices to do so. So for sound, for instance, I could come up with a record player, I could come up with a tape recorder, and then if I want to measure a temperature signal then I would have to come up with a mechanical system that drags a pencil on a piece of paper to record the evolution of temperature. And to capture photographs, I will have to invent a camera. But you see every device is specific to a certain signal. It will record any information but it will not let me manipulate this nformation easily and in a generic way. In other words, the recording device will give me something like a picture, something like this. 

<img src="images/im1.png" style="height:200px">

But it will not answer the question, what is the function that describes the phenomenon? This is the problem with analogue signals. Mathematically we will formalise with the following mapping:
$$
f : \mathbb{R} \rightarrow \mathbb{V}
$$


**Digital:**

-----

The big paradigm shift and the power inherent to digital signal processing, is that we're moving away from an analog model for signals like this. So we're not asking, what is the function that represents the signal anymore, we're just moving to a recording of the values of this function. And represent the phenomenon just as a series of numbers. And in particular, for digital signals, these numbers are integers. The so called digital paradigm is composed of two fundamental ingredients:

* Discrete time
* Discrete amplitude

We will formalize with the following mapping:
$$
\mathbb{x} : \mathbb{Z} \rightarrow \mathbb{V}
$$
We will denote a discrete time signal by:
$$
\mathbb{x}[n] = ~..., 1.2390, -0.7372, 0.8987, 0.1798, -1.1501, -0.2642, ...
$$


**We will pretty soon see that $n$ does not have a physical dimension.** It's just an ordinal number that orders the samples one after the other.



**Sampling Theory:**

---

**Are we loosing information using a discrete time sequence ?** The question is a fundamental importance and the answer was given to use at the beginning of last century by Harry Nyquist and Claude Shannon. The answer is positive and it states that under very mild conditions, the continuous time representation and the discrete time representation are equivalent. Mathematically, the result is known as a **sampling theorem (1920)**, and it has a very simple statement. The relationship between the continuous time a presentation of a signal, and its discret time counterpart is given by this formula. 
$$
\mathbb{x}(t) = \sum_{n= - \infty}^{+ \infty} \mathbb{x}[n] ~ sinc \Big( \frac{t - n T_s}{T_s} \Big)
$$
The **cardinal sine function** looks like so, with an infinite support function that keeps oscillating from minus infinity to plus infinity:

<img src="images/im3.png" style="height:150px">

**Continuous to discrete :** And sampling theorem graphically looks like so, you start with a contunous times signal and then you take measurements and then you throw away all the rest

<img src="images/im4.png" style="height:150px">

**Discrete to continuous :** to go back to contunous time, all you need to do is take copies of the $sinc(\cdot)$ function and place them at each sample location scaled by the amplitude of the sample. When you sum all these copies of the $sinc( \cdot)$ together, you get back exactly the original function.

<img src="images/im5.png" style="height:150px">

We will have to use the Fourier analysis to do that.



**Discretization of Amplitude :**

---

If our data is just a set of integers it means that its representation is completely abstract and completely general, and this has three important consequences:

* Storage : we won't need a specific storage as we saw for different type of signals, and can be stored as $\{0, 1 \}$
* Processing : with CPUs that are very effective on integers 
* Transmission : we have extremely effective ways to combat noise and maximise the capacity of the communication channel

Let's delve deeper into the Transmission; let's say we have a communication channel, and we try to send information from a transmitter to a receiver,

<img src="images/im6.png" style="height:70px">

We will face the **fundamental problem of noise**. Inside the channel it will introduce attenuation ($1/G$) and also add noise ($\sigma(t)$).

<img src="images/im7.png" style="height:175px">

We can see the original signal (on the left) and the one received, an attenuated copy plus noise(on the right):

<img src="images/im8.png" style="height:175px">

The only thing we can do is adding an amplification at the end of the channel :

<img src="images/im-9.png" style="height:175px">

What we get, the Gain factor has also amplified the noise. This is a typical situation that you get in second generation or third generation of say, a tape or if you're trying to do a photocopy of a photocopy.

<img src="images/im10.png" style="height:175px">

**Practical example - Transmitting a signal overseas**

We split the channel into several chunks and try to undo the attenuation of a chunk in sequence. We put what are called repeater every 10km or so. 

**For an analog signal :** This can lead very quickly to complete loss of intelligibility in a phone conversation.

<img src="images/im11.png" style="height:175px">

**For a digital signal : **The noise is much larger than before but we can just threshold and say if the signal value is above zero, we just output $5V$ and vice versa. 

<img src="images/im12.png" style="height:175px">

So the thresholding operator will reconstruct a signal like so. So you can seee that at the end of the first repeater, we actually have an exact copy of the transmitted signal and not a noise corrupted copy.

<img src="images/im13.png" style="height:175px">



## 1.2 Discrete-time signals

Discrete-time signal: a sequence of **complex** numbers

* one dimension (for now)
* notation: $\mathbb{x}[n]$
* Two-sided sequences: $\mathbb{x}:  \mathbb{Z} \rightarrow \mathbb{C}$
* n is a-dimensional "time"
* analysis: periodic measurement
* Synthesis: stream of generated samples

