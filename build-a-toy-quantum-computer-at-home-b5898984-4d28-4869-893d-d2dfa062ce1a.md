## Outline

In the past few [posts](https://www.houseofwisdom.online/maths-courses/matrices) we've gone over how to interpret matrices, basis vectors, and eigenvectors. Today, we'll put all that together towards a really fun goal - building a toy quantum computer at home!  We'll even solve a real problem on this "computer" that we couldn't solve as efficiently on a standard computer.

All this will continue our understanding of the diverse and exciting applications of Linear Algebra.

### Project Overview

We are going to build a toy "quantum computer" just using a display, and a few polarizing filters.

**Cost:** \$20

**Materials**

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1cenlSoImsPoTcLINUSF-Q2w2JpG3z85Z" alt="Embedded Image">

These are all the materials we will use. A cell phone, and a linear polarizer filter sheet.

1. Your cell phone (or any display/light).
2. A polarization sheet such as the one in the link below.

[Linear Polarization A4 Sheet Polarizer Educational Physics Polarized Filter Optical](https://www.amazon.com/Polarization-Polarizer-Educational-Physics-Polarized/dp/B06XWXRB75)
3. Cut the polarizer sheet into squares. Apply a yellow post it flag so we can track the orientation of the square.

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1OGQXNBrVSj0jtAExLGM6rgkSfePwSzr4" alt="Embedded Image">

A small post it note lets us track the orientation of this square.

---

## Some Background Knowledge

### Using Light to Harness Quantum Properties

To begin our process of building a computer we need to understand one of the foundational concepts in physics - light! Physicists in the 20th century developed quantum mechanics by studying some of the incredible properties of light. A few of these examples are shown below:

- [Photoelectric Effect (the discovery that Einstein won his Nobel Prize for)](https://en.wikipedia.org/wiki/Photoelectric_effect).
    - Showed light is composed of discrete units called photons.
- [Double-Slit Experiment](https://www.youtube.com/watch?v=Iuv6hY6zsd0)
    - One of the seminal experiments in proving light can behave as both a wave and a particle.
- The [Black Body Radiation problem](https://www.youtube.com/watch?v=FXfrncRey-4)
    - Studied by Max Planck and led to the discovery of Planck's constant - a fundamental number in Quantum Mechanics.

In this project, we will use the quantum properties of light to create something like a computer. Specifically, we will use a property of light known as polarization to carry out computations in our computer.

Let's now dive into what exactly light polarization is and how we can leverage it.

---

## Polarization Overview

In the 1800s, Maxwell [famously discovered](https://www.space.com/speed-of-light-properties-explained.html) that light is a direct consequence of electricity and magnetism (in fact, the movement of electrons in space generates light!). He found that light is an **electromagnetic** wave (an electric and magnetic field that travels through space).

In this electromagnetic wave, there are two parts: the electric field wave and the magnetic field wave. We call direction of orientation of the electric field the **polarization** of light.

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1m6srzLHOjeuG6JGAhVToc24AqAOaihIL" alt="Embedded Image">

---

You may be surprised at just how often we use polarization everyday. For instance, any time you put on a pair of polarized sunglasses on a sunny day, you are harnessing light polarization! The black lenses on polarized sunglasses block certain types of light to reduce the glare that we see. The lenses do so by only letting in light of a certain polarization angle and blocking all other light.

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1x3NGHy0IcLHdoLYO2HsmOuTL9XgKstIG" alt="Embedded Image">

The lenses on polarized sunglasses are polarization filters that only allow light of a specific polarization through.

A sunglass lens is a specific example of a polarization filter - a barrier that only lets in light of a specific polarization angle.

This may seem fairly straight forward but as we study polarization more, we notice some really counterintuitive properties that are in fact deeply rooted in quantum mechanics. Namely, light can seemingly be polarized in multiple states at once!

## Photons Can Be Polarized in Multiple Directions at Once

Let us now dig into what makes light polarization so useful in building a quantum computer.

Through experiments, we  will see that a single photon of light can be polarized **in multiple directions at once**. This is an idea rooted in quantum physics known as **superposition.**.

<p class='image-block'>
<iframe width="560" height="315" src="https://www.youtube.com/embed/UjaAxUO6-Uw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
<br/>
In the thought experiment, Schrodinger's Cat is somehow both **dead and alive** at the same time. In the same way, a photon of light can be polarized **in multiple directions** at the same time.
</p>

You may have seen superposition in the famous Schrodinger's Cat paradox where the cat is somehow both   "dead" and "alive" at the same time. This is exactly what we'll see is going on with the state of a photon's polarization!

### Experiments

Let us now see this ourselves! We will run a set of experiments to in fact ourselves verify that **light can be polarized in multiple angles at once.**. Note with a large set of photons we can explain these effects using classical physics but when we get down to single photons, we need to use the quantum interpretation we will soon discuss.

Here are the experiments we will run:

- **Experiment 1 -** Shows how polarizers work to help us develop an intuition.
- **Experiment 2 -** Shows that if light is vertically polarized it cannot be horizontally polarized.
- **Experiment 3 -** Shows that introducing a 45º polarizer allows light to be superposed in multiple polarizations at once.

These experiments are heavily based on the following video from Minute Physics and 3Blue1Brown.

<iframe width="560" height="315" src="https://www.youtube.com/embed/zcqZHYo7ONs" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---

### Experiment 1 - Effect of Vertical polarizer

**Description**

Our first experiment is going to simply show what a vertical polarizer does. We'll be able to see that it blocks out some amount of light and only lets vertically polarized light through.

**Instructions**

1. Take your cell phone. Turn the display on.
2. Place a vertical filter on a section of the phone.
3. Only vertically polarized light comes out of that section.

**Seeing it in Action**

Below is my phone with a small vertical polarizer on the top left corner.

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1vG5EWmp1QnVtyyy-3GwnfaMIHvjGgiyy" alt="Embedded Image">

A vertical polarizer is present on the top-left corner of the screen.
</div>

---

Conceptually, the polarizer in the top-left corner is blocking everything but vertically polarized light as shown below.

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1Pf8N3r12cU8ds1l9FNasU8MyLxORZkbk" alt="Embedded Image">

**Conclusions**

A vertically polarized filter only lets vertically polarized light out.

---

### Experiment 2 - Effect of Vertical + Horizontal Polarizer

**Description**

Our next experiment will show that vertically polarized light is entirely blocked by a horizontal polarizer. We will place a horizontal polarizer on top of a vertical polarizer and see that little to no light comes through.

**Instructions**

1. Take your cell phone. Turn the display on.
2. Place a vertical filter on a section of the phone.
3. Place a horizontal filter on the same section of the phone.
4. Notice how little to no light now appears.

**Seeing it In Action**

Below is my phone with a both a vertical and horizontal polarizer in sequence (the yellow tab shows the orientation of the polarizer). Notice how we can no longer read the screen.

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1DMY45vVvade7oitsiFE2MlnROpCS3-4q" alt="Embedded Image">

---

With the addition of the horizontal polarizer, all light is effectively blocked in the top-left corner of the screen as seen below:

<p class='image-block'>
<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1olELBTgnYsQo5EH69vd_N047UTRInOT-" alt="Embedded Image">

A vertical polarizer followed by a horizontal polarizer will block all light.
</p>

**Conclusion**

Vertically polarized light cannot go through a horizontal filter.

---

### Experiment 3 - Effect of Vertical + 45º + Horizontal polarizer

**Description**

This is the fun part! We now get to see what happens when you place a 45º filter in between a vertical and horizontal polarizing filter. What we'd expect is the same as in experiment 2 - no light gets through. If polarizers just block light, surely adding a third polarizer will only block more light.

However,  what we end up seeing is quite unexpected!

**Instructions**

1. Take your cell phone. Turn the display on.
2. Place a vertical filter on a section of the phone.
3. Place a horizontal filter on top of it.
4. Place a 45º filter in between the vertical and horizontal filter.

**Seeing it in Action**

Adding the diagonal polarizer really does let some light through (about 50% of it)! You can see this below as I move a diagonally oriented polarizer between the vertical and horizontal polarizer.

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1T9Q03cdFscufKaZuAca6w7M6HuVIdqgq" alt="Embedded Image">

---

Adding the diagonal polarizer somehow leads to **more light** against all expectations! We can see what's happening in the diagram below. We will explain this more in the following section so don't worry too much if you don't understand it.

<p class='image-block'>
<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1C7095b5p6jHmo2tXQW4FidADLpa_o15k" alt="Embedded Image">

A vertical filter followed by a 45º filter and then a horizontal filter will let some light through.
</p>

**Conclusion**

- Light that is seemingly vertically polarized can somehow become horizontally polarized.
- The 45º filter is needed for this change to happen. Without it we see no light can come out.
    - Without 45º filter

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=12_EnBhWvcH2dOj2y0QQKEaPolNS-jMn5" alt="Embedded Image">

- With 45º filter

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=14yLS-bic3PkHR6_ubQeO9Jjju_iIJ0l1" alt="Embedded Image">

---

## Understanding Experiment 3

So what is going on in Experiment 3? How does vertically polarized light go through the 45º filter?

### Thinking of Photons as Combinations

We can think of a vertical line/vector (black) as the sum of a 135º (blue) vector and 45º (purple) vector. This is shown below:

<div>
<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1EsOreCHgFqORxdjQcN6s-p0UaqjZ3hjk" alt="Embedded Image">

A vertical line can be seen as a sum of diagonal line 1 and diagonal line 2.
</p>
<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1nBi6ww5tLAtUHuAjvLx8QLdQVEEg4opQ" alt="Embedded Image">

The horizontal components of 1 and 2 cancel out when added, leading to a vertical line.
</p>
</div>

So in that sense, we can think of a vertically filtered photon as the **combination** of a 135º filtered photon and a 45º filtered photon. Or in other words, the vertically filtered photon can be seen as filtered in **both these angles at once** (Note that it's a very **specific amount**  $\frac{\sqrt{2}}{2}$ of each of these options. But we are going to postpone that discussion for now).

<p class='image-block'>
<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=14M0DcVlfTgCsnfS9ZXJnn27PLoD0Tp92" alt="Embedded Image">

A vertically filtered photon can be seen as a combination of a 45º polarized photon and a 135º polarized photon.
</p>

Equipped with this idea, let's now revisit experiment 4's setup. We are going to break it up into **Step 1, Step 2, and Step 3.**

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1pl5ZSRk3SZYGa4AV9f6mFezE6idu6Gox" alt="Embedded Image">

We will break up Experiment 3 into three steps.

### Step 1 - Vertical Filter

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1YTBOncjEqY0z4UKThx9cf3AeIDuc2frn" alt="Embedded Image">

Step 1 is fairly straightforward - The vertical polarizer only lets vertically polarized  photons through. The horizontally polarized photons get blocked.

### Step 2 - 45º Filter

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=11YSYhz2QiXPmDHjIMCluiTtGotGYgVJP" alt="Embedded Image">

In Step 2, vertically polarized photons pass through the diagonal polarizer.

In Step 2, we decompose the vertically polarized photons into 45º polarized photons. The 45º polarized photons then get passed through. Let's see how:

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1mCI9FhGEU53fNaaKw-r0-KTl2lg0VQK5" alt="Embedded Image">

We start with a vertically polarized photon entering a 45º polarizer. The vertically polarized photon can be thought of as a combination of a 135º and 45º polarized photon. The 45º photon then goes through!

### Step 3 - Horizontal Filter

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1jrKD0uHZOj1O1xFgmvxkCpE6hk2PpVkS" alt="Embedded Image">

In Step 3,  light enters the horizontally filtered polarizer and we see light appear on the other side.

Similar to step 2, 45º polarized photons get broken down into a horizontally polarized subcomponent. The horizontally polarized subcomponent gets passed through.

Let's break this down and see how:

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1Gqx4yZQZ6Eh3_nnW2vHCAKhnNIX96eNK" alt="Embedded Image">

We start with a diagonally polarized photon entering a horizontal polarizer. The  photon can be thought of as a combination of a vertically and horizontally polarized photon. The horizontal "part" of the photon goes through!
</p>

### Putting it All Together

Putting this all together, we see how we get light at the end of this process:

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1_rtHOoneg_enks_esttcTPDzF9afT0Pq" alt="Embedded Image">

The addition of the diagonally polarized photon lets light through our system. We will explain this further below. The 45º filter broke down the vertically polarized photon into diagonal components. The diagonal component then include a horizontal component that gets passed through.
</p>

However, not all the light passes through from the source to the end. This is because when we break up a photon into it's superposed states, we lose some amount of light at each step. This seems **impossible.** A photon is by definition indivisible - how can we possibly subdivide something that can't be divided?

The answer ends up being that instead of say half a photon passing through, a single photon now passes through with 50% probability. I'm going to avoid a full discussion of this but you can read more about it [here](https://www.quantamagazine.org/the-born-rule-has-been-derived-from-simple-physical-principles-20190213/#:~:text=Einstein%2C%20Born%20said%2C%20had%20interpreted,the%20only%20logically%20consistent%20guess.).

---

### Why Light Didn't Appear Without a 45º Filter

So why didn't we get a photon when the 45º polarizer was not present?

Without the 45º polarizer, we aren't able to break the vertically polarized photon into diagonal components.

And if we're not able to do that, there's no horizontally polarized component when the photon hits the horizontal polarizer. So nothing get's through!

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1ZamvwdNyKgAgfWcMDX7YmCvPwZEu8Lht" alt="Embedded Image">

The vertically polarized photon has no horizontal component. So no light passes through.

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1WnQhQ8yL3G5d3jtdpRstbHbACUB4McX4" alt="Embedded Image">

The corner of the screen is entirely black as a result.

We've thus seen something really really interesting:

A single photon of light can be thought of as being composed of multiple photons. Another way of thinking about this is that a single photon can seemingly be multiple photons at once. This is a very real and visible example of the quantum physics idea of **superposition.**

Let us now see how this gives us the ability to build really powerful computers.

---

### Computers Made from Light

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1hSmKLpFTHt6Ts-x1BxQ8KMebRlGxLVkf" alt="Embedded Image">

An example of a real quantum computer built using photons. We won't be creating this but instead will focus on a toy example with polarizer lenses.

To build our computer, we will  start by understanding the the idea of a computer "bit".

**Bits**

For standard computers, we use bits to store memory. Bits can be 0 or 1 - nothing in-between.

Visually, you can think of it as being on one of two points (0 or 1) on this number line:

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1acKIRs7OtyST8wnPWgvaA4XuGkUHDrfW" alt="Embedded Image">

A standard computer bit can be in only one of two spots - 0 or 1.

**Photon Bits**

Now imagine we build a computer using photons, and we make "bits" out of the photons through the below process.

1. Check the photon. If it is **horizontally** polarized, call it a 0. We will draw this as the vector $\begin{bmatrix}0 \\ 1\end{bmatrix}$ (as it is horizontal).

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1soMal__Jaxt0AHWw9zPqCmSdjAUZjwu2" alt="Embedded Image">

2. Check the photon. If it is **vertically** polarized, call it a 1. We will draw this as the vector $\begin{bmatrix}1 \\ 0\end{bmatrix}$.

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=19G23H2ms9y8rdFx3rrw041PQDMQCLEL5" alt="Embedded Image">

The horizontal and vertical vectors clearly can be combined to reach any point in the 2D plane (i.e.$\begin{bmatrix}0 \\ 1\end{bmatrix}$ and $\begin{bmatrix}1 \\ 0\end{bmatrix}$ form a **basis** for $\mathbb{R^2}$).

Now what are all the points that can be composed of these two vectors and have a length of 1  (the polarization vector of the photon must have length 1)?

**The Unit Circle**

A circle of radius 1 centered at the origin is just the set of possible polarization vectors that have length 1, start at the origin, and can be seen as some combination of horizontal and vertical polarization.

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1RF5n2HmonnMQtGIPIVRc2WVKcTZNdQbS" alt="Embedded Image">

Any point on the unit circle is some combination of $\begin{bmatrix}0 \\ 1\end{bmatrix}$ (horizontally polarized photons) and $\begin{bmatrix}1 \\ 0\end{bmatrix}$ (vertically polarized photons).
</p>

Thus, any point on this circle can be thought of as representing a potential state of polarization for a photon (yes you can even have a negative amount of each polarization - at least prior to final measurement!).

Notice how many more options there are here vs. a standard bit which can just be at 0 and 1!
<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1RF5n2HmonnMQtGIPIVRc2WVKcTZNdQbS" alt="Embedded Image">

Our photon "bit" can occupy any point on the unit circle.
</p>
<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1acKIRs7OtyST8wnPWgvaA4XuGkUHDrfW" alt="Embedded Image">
A standard bit can only be one of those two points.

---

## Building a Quantum Computer with Photon Bits

Can we leverage the fact that this photon "bit" can occupy an entire circle while a bit can occupy only 2 points?

Yes! This is one of the ideas behind a quantum computer. Use the fact that a single photon "bit" can be in many states at once, we can store more information than what we could if photon was only in one of two states. We refer to such photon bits as "qubits"(short for quantum bits).

We are going to store information using the polarization of  photons and solve small computational problems with them.

How?

We are going to use the same setup as with our experiments. We are going to shoot out some photons (light) and then tilt the photons with polarizers to keep track of things.

## Problem We Will Solve

<p class='image-block'>
<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1BB92e8s1DXL2oYcvUgKe3-MkZAcFVqDe" alt="Embedded Image">

We will create an algorithm to determine whether or not the coin is biased.
</p>

Let's build this computer in the context of a concrete problem.

Suppose I give you a biased coin that is actually heads 75% of the time and tails 25% of the time. Can you come up with a way to prove it is biased? This problem was introduced and solved in a [paper](https://www.scottaaronson.com/qclec/5.pdf) by Professor Scott Aaronson (author of the popular [Shtetl Optimized](https://www.scottaaronson.com/blog/) blog).

Here's the Classical Solution:

1. Flip the coin a bunch of times. Count how many times you get heads and how many times you get tails.
2. Store the number of heads and tails you have got so far using bits.
3. Computational Needs:

Memory: Bits related to number of coin flips (need to record result per coin flip).

Here's the Quantum  Solution:

1. Use the angle of polarization of a photon to keep track of the ratio of heads to tails. If the ratio is far from 1:1, we are probably dealing with a biased coin.
2. Computational Needs:

Memory: Just 1 photon of light vs. many many bits in the classic problem.

---

## Solving the Problem

Let's now build a quantum computer using photons and light polarization to solve our problem.

### Intuition

Here's how our solution will work at a high level:

1. We are going to take a photon of horizontally polarized light.
2. When we get a Heads, we are going to rotate the polarization by a small positive angle.

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=112WTj5UzzyfPZi-slcB4sglHFvMX7xbU" alt="Embedded Image">

3. Conversely, when we get a Tails, we are going to rotate the polarization by a small negative angle.

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1ioy2MbDiC0-eaB7yOauDdk_MaSKqujXs" alt="Embedded Image">

We keep playing this game for many steps and stop if we see that the light is fully vertically polarized. At this point, we can predict that the coin is biased.

If we never get to vertically polarized light after some amount of steps, we predict the coin is unbiased.

### Biased Case

In the Biased Case, we eventually rotate the photon vertically and at that point stop flipping the coin and are fairly certain the coin is biased.

<p class='image-block'>
<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1PXBQd_1yFG9ZqqjJdZCMhzJZ5M3VvTT4" alt="Embedded Image">

In the biased case, we eventually rotate the photon's polarization so that it is points up (or alternatively points down if the bias is in the tails direction).
</p>

### Unbiased Case

In the Unbiased Case, we will be more likely to be stay closer to our original horizontal angle as many of the flips will cancel out.

<p class='image-block'>
<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=14jZ6-MzMVkk5LUiVxMaVZgCmT0AFMhab" alt="Embedded Image">

In the unbiased case, the final angle will be much closer to 0 leading to horizontally polarized light.
</p>

## Conducting the Experiment

Let's now see the experiment in action.

We will follow these steps:

1. Keep the phone screen on.

2. Place a horizontal polarizer on a region of the screen.
1. Flip the coin

2. If heads, place a filter rotated 3º
3. If tails, place a filter rotated -3º
1. Repeat this 50 times
2. Apply a horizontal polarizer
3. Check if light is coming out at the end or not!

4. If light is coming out, the light has elements of horizontal polarization and the coin is unbiased.
5. If not, the coin is largely vertically polarized and the coin is biased.

---

### Result Experiments

**Results on Biased Coin**

Below is an image showing my results on a biased coin. Note the yellow post it note indicates the orientation of polarizer. Here's what's happening:

1. With a biased coin, we keep tilting the polarizers and eventually end up orienting the the photons to be completely vertically polarized.
2. As a result, when we apply the horizontal polarizer at the end, **no light is able to pass.**

<p class='image-block'>
<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1H0t-qhPEXiG_pTLoW2sZJ5OVykIj1m_G" alt="Embedded Image">

At the end of the process, we apply a horizontal polarizer and see no light. Yes I did have only 3% battery life - I live on the edge.
</p>

**Results on Unbiased Coin**

Below is an image showing my results on an unbiased coin. Here's what's happening:

1. With an biased coin, we keep tilting the polarizers and eventually end up back at a horizontal polarization.
2. As a result, when we apply the horizontal polarizer at the end, **light is able to pass!**

<p class='image-block'>
<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1fVDeWPBbHyPT95XKlue-M3nuQJJjCsyO" alt="Embedded Image">

At the end of the process, we apply a horizontal polarizer and see light appear! Notice the signal strength in the top-left corner is visible.
</p>

### Caveats

There are a few details we are glossing over here to make this simpler. I'm going to list them here so that you can dig into them further.

1. The actual algorithm by Aaronson and Drucker has a smart way of determining when to check the polarization of light such that you don't overshoot 90º or -90º. You can see the full paper [here](https://www.scottaaronson.com/papers/qcoin13.pdf).
2. We can only rotate by a very small angle each time - if our angle is much larger we will lose light at each polarization step. Though technically if our angle is small enough we can ensure no light loss.
3. The current setup we have is not guaranteed a correct result. However, the fully realized version of this idea in the paper can essentially guarantee a correct result through optimal choice of a few parameters including  $\theta$ , the angle by which we rotate the filter.
4. We are very much not using one photon in the experiment (we are keeping our light on the entire time leading to lots of photons). However, in an idealized quantum computer you would be able to run this with just a single photon (and hence one qubit).

---

### How this is Better than a Normal Computer

So we've seen we can compute the entire result with our home setup! Not only that, we've been able to do it in a way that's actually not possible with a standard computer. Here's how:

Because our photon polarization can have a state anywhere along that unit circle, we can use the polarization angle to implicitly store how the number of heads vs. tails.

- If we have a lot more heads - the angle is far larger
- If we have  even an even amount - the angle will be closer to 0

Thanks to this, we are technically able to use just one photon of light to store all the information we need. This is as opposed to a number of bits proportional to the number of flips in the normal case!

**Scaling this to a real Quantum Computer**

Issues with this setup

- We are not using just one photon here. in an ideal setup, we would design our rig so that we just have one photon moving back and forth.
- Have to manually apply each transformation
    - Final computer will do this automatically.

---

## Conclusion

If you've made it this far, you've successfully seen how we can harness quantum properties to carry out interesting computations. You'd be surprised to learn that real quantum computers utilize similar ideas!

Just as we leveraged the fact that light can be polarized in multiple directions at once, many quantum computers utilize the fact that an electron can be spinning in multiple directions at once.

<p class='image-block'>
<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1Fk6PZchYz4gh-NO_ei27Ao7EUlwBA67Q" alt="Embedded Image">

Just as light can be polarized in multiple directions at once, an electron can spin in multiple orientations at once. Image source: https://commons.princeton.edu/josephhenry/modern-understanding/.
</p>

To perform computations on these qubits, we similarly rotate the orientation of these electron spins in interesting ways.

Today, quantum computers are achieving new heights and are already doing things most computers are incapable of doing. For instance, the quantum computing team at Google [released a paper in 2019](https://www.nature.com/articles/s41586-019-1666-5) discussing their result of achieving results in quantum computers not previously achievable with classical computers.

<p class='image-block'>
<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1Ysygvh5zRyczvxhc0kjFBG56Zx10tln6" alt="Embedded Image">

Google's quantum computer, Sycamore, achieved results that pushed the boundaries of computing. Image source: https://ai.googleblog.com/2019/10/quantum-supremacy-using-programmable.html
</p>

It's exciting to see where this field will go and hopefully through this post you were able to get a bit more intuition into how these computers work and how engineers around the world are building them!

---

## Sources and Further Reading/Watching

<strong>3Blue1Brown + Minute Physics video on light polarization</strong>
<iframe width="560" height="315" src="https://www.youtube.com/embed/zcqZHYo7ONs" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<br/>

<strong>Scott Aaronson Quantum Computing Lecture Notes</strong>

- All Notes[https://www.scottaaronson.com/blog/?p=3943](https://www.scottaaronson.com/blog/?p=3943)
- Specifically, see this lecture on Advice Coins: [https://www.scottaaronson.com/qclec/5.pdf](https://www.scottaaronson.com/qclec/5.pdf)
- Aaronson and Drucker paper on Advice Coins for Classical and Quantum Computation: [https://www.scottaaronson.com/papers/qcoin13.pdf](https://www.scottaaronson.com/papers/qcoin13.pdf)

<br/>

<strong>Google Sycamore Quantum Supremacy paper</strong>

- See here: [https://www.nature.com/articles/s41586-019-1666-5](https://www.nature.com/articles/s41586-019-1666-5)
<br/>

<strong>Richard Feynman Lectures on Quantum Electrodynamics</strong>
<iframe width="560" height="315" src="https://www.youtube.com/embed/LPDP_8X5Hug" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br/>
<strong>Ted Ed video on Schrodinger's Cat</strong>
<iframe width="560" height="315" src="https://www.youtube.com/embed/UjaAxUO6-Uw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br/>
<strong> Scientific American</strong>

Video from Scientific American going over how light polarization experiments helped us confirm the theory of quantum entanglement.
<iframe width="560" height="315" src="https://www.youtube.com/embed/Z34ugMy1QaA" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

