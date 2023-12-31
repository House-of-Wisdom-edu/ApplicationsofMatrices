In the last few posts, we've focused heavily on [matrices](https://www.houseofwisdom.online/maths-courses/matrices) and their [applications](https://www.houseofwisdom.online/maths-courses/pagerank). In this post, we're going to use matrices to learn about Kernels.

The Kernel of a function is the set of points that the function sends to $0$. Amazingly, once we know this set, we can immediately characterize how the matrix (or linear function) maps its inputs to its outputs.

I hope that by the end of this post you will:

1. Understand what a Kernel of a function is and how it helps us understand a function better.
2. Realize that the inverses of output points are always some translation of the Kernel (for linear functions).
3. See that there are many pretty patterns and coincidences that flow out of the properties of linear functions.

### Functions Across Spaces

In previous posts, we noticed how matrices are just linear functions. We found that the matrices we studied just rotate or stretch a vector in some way.

<div class='image-block'>
<img src='https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CocoaDrawingGuide/Art/scaling_2x.png'>
An example of a function that stretches its input. Source: http://developer.apple.com.
</div>

But we only studied square matrices (i.e. 2x2 or 3x3 matrices). What happens when our matrices aren’t square?

Let’s start with a 2x3 matrix that represents a linear function $f$. Let's study a function $f$ defined by the matrix $F$:

$$
F = \begin{bmatrix} 2 & 1 & 0 \\ 0 & 1 & 3 \end{bmatrix}
$$

What happens if I apply this matrix on a vector $v = \begin{bmatrix} 3 \\ 2 \\ 1 \end{bmatrix}$?

Let's find out:

$$
\begin{aligned}
F v &= \begin{bmatrix} 2 & 1 & 0 \\ 0 & 1 & 3 \end{bmatrix} \begin{bmatrix} 3 \\ 2 \\ 1 \end{bmatrix} \\
F v &= \begin{bmatrix} 8 \\ 5 \end{bmatrix}
\end{aligned}
$$

In other words, $f(\begin{bmatrix} 3 \\ 2 \\ 1 \end{bmatrix}) = \begin{bmatrix} 8 \\ 5 \end{bmatrix})$.

So $f$ effectively takes a point in 3 Dimensions, ($\begin{bmatrix}3 \\ 2 \\ 1\end{bmatrix}$) and sends it to a point in 2 Dimensions ($\begin{bmatrix} 8 \\ 5 \end{bmatrix}$). We can see this below:

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1H3Jrxv8uQJ7HrBSVRyWeFivR6X598GDc" alt="Embedded Image">

$f$ maps points from $R^3$ to $R^2$.

We interact with functions that take points from 3D to 2D all the time. For instance, everytime you take a picture with a camera you are taking a 3D space (the world you see), and collapsing it onto a 2D space (the camera sensor).

<div class='image-block'>
<img src='https://upload.wikimedia.org/wikipedia/commons/thumb/3/3b/Pinhole-camera.svg/1200px-Pinhole-camera.svg.png'>
A camera converts a 3D object (the tree) into a 2d representation (image). Source: Wikipedia.
</div>

The input space for $f$ is $R^3$ and the output space is $R^2$. More formally, we write this as:

$$
f: R^3 \rightarrow R^2
$$

### Losing Information

Returning to the example of cameras, when we take pictures, we squash a 3D world onto a 2D sensor. In the process, we lose some amount of information primarily related to depth.

Specifically, points that are far away will appear close to each other even though they may be quite distant.
Eventually, points infinitely far away on the horizon all *collapse* onto the same point. We can see this in the example image below.

<div class='image-block'>
<img src='https://images.unsplash.com/photo-1554976757-606d486f5d92?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2204&q=80' />

Notice how the pillars above appear closer and closer together even though they are staying the same distance apart. We have lost information about the distance between this pillars when converting to 2D. Image source: Unsplash.
</div>

So just like a camera, will our function also "lose" some information when it moves points from 3D to 2D? Will it *collapse* multiple points from the input to the same point in the output?

<hr />

### The Kernel - Set of Points that Map to 0

To answer this, let's start by seeing all the points $v = \begin{bmatrix} v_1 \\ v_2 \\ v_3 \end{bmatrix}$ that map onto the origin of the output space - $\begin{bmatrix} 0 \\ 0 \end{bmatrix}$. This gives us a good starting point for understanding which points from our input hit the same point in the output.

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1tSjeuWg6WjlGEFGn4fXI_O4XdysM_tJ7" alt="Embedded Image">

Which points map to $\begin{bmatrix}0 \\ 0\end{bmatrix}$?

We want to solve:

$$
\begin{aligned}
Fv &= \begin{bmatrix} 0 \\ 0 \end{bmatrix} \\
\begin{bmatrix} 2 & 1 & 0 \\ 0 & 1 & 3 \end{bmatrix} \begin{bmatrix} x \\ y \\ z \end{bmatrix} &= \begin{bmatrix} 0 \\ 0 \end{bmatrix}
\end{aligned}
$$

Carrying out this multiplication, we see this is satisfied when:

$$
2x + y = 0
$$

$$
y + 3z = 0
$$

<div class='highlight-block'>

Solving this for each variable in terms of $y$, we find:

$$
\begin{aligned}
x &= -\frac{y}{2} \\
z &= -\frac{y}{3}
\end{aligned}
$$

So, $f^{-1}(\begin{bmatrix} 0 \\ 0\end{bmatrix})$ is a line parameterized by:

$$
\begin{aligned}
x &= -\frac{t}{2} \\
y &= t \\
z &= -\frac{t}{3} \\
\end{aligned}
$$

for some $t \in R$.

</div>

This line is shown below. Some points on this line are:
$v_1 = \begin{bmatrix} 0 \\ 0 \\ 0 \end{bmatrix}$,
$v_2 = \begin{bmatrix} -3 \\ 6 \\ -2 \end{bmatrix}$, $v_3 = \begin{bmatrix} -4.5 \\ 9 \\ -3 \end{bmatrix}$.

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1MMN2SYUvtB32sUa5uGzDEAerl4ujnGLQ" alt="Embedded Image">

The Kernel of $f$ is the set of points that $f$ maps to $0$. In this case, it forms a line.

<div class='highlight-block'>
There’s a term for this set - <strong>the Kernel</strong>. We call it the Kernel because this set of vectors maps to the origin, or the core, of the output space.
</div>

In our specific case, the Kernel is a line. When $f$ maps this line to the point $0$, we lose information about the line - in the output space, the points on the line are no longer distinguishable.

Returning to our camera analogy, this is similar to how all points on the horizon are no longer distinguishable after the conversion from 3D to 2D. <strong>Thus, you can think of the Kernel as a quick way to see how the function compresses or loses information.</strong>

#### Terminology Aside

Let's get some more quick terminology out of the way before proceeding. We're going to use the following terms:

1. **Image** - the set of outputs of the function (i.e. everything in $f(x)$). The image of a point $x$ is just $f(x)$.
2. **Pre-Image** - the set of inputs for the function (i.e. the $x$ in $f(x)$). The pre-image of a point $y$ is just $f^{-1}(y)$.

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1psDWHBbaphhn1yaXvrst2HeR2YpaekPo" alt="Embedded Image">

In the above example, the function $f$ maps the oval (Pre-Image) on the left to the point (Image) on the right.

### Translations of the Kernel - Mapping to $\begin{bmatrix} 1 \\ 1 \end{bmatrix}$

We found the set of points that map to $\begin{bmatrix} 0 \\ 0 \end{bmatrix}$ (i.e. the pre-image of the origin). We call this set the Kernel or $K$ for short.

Can we now similarly find the set of points that map to $\begin{bmatrix} 1 \\ 1 \end{bmatrix}$?

<div class='highlight-block'>
We're going to do this to show something really cool:
<ul>
<li>

Once you know the pre-image of $\begin{bmatrix} 0 \\ 0 \end{bmatrix}$, it's super simple to find the pre-image of $\begin{bmatrix} 1 \\ 1 \end{bmatrix}$ or any other point for that matter.

</li>
</ul>
</div>

<hr />

#### Finding the pre-image

Let's start by finding the points that maps to $\begin{bmatrix} 1 \\ 1 \end{bmatrix}$ as before.

$$
\begin{aligned}
F v &= \begin{bmatrix} 1 \\ 1 \end{bmatrix} \\
\begin{bmatrix} 2 & 1 & 0 \\ 0 & 1 & 3 \end{bmatrix} \begin{bmatrix} x \\ y \\ z \end{bmatrix} &= \begin{bmatrix} 1 \\ 1 \end{bmatrix}
\end{aligned}
$$

Solving for each variable, we find that this is just the line defined by:

$$
\begin{aligned}
x &= \frac{1-t}{2} \\
y &= t \\
z &= \frac{1-t}{3}
\end{aligned}
$$

for some $t \in R$.

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1Puy0G7bc9zgMAwVbIHptqRZyGsKEl_UE" alt="Embedded Image">

$f^{-1}(\begin{bmatrix}1 \\ 1 \end{bmatrix})$ is the set of points that $f$ maps to $\begin{bmatrix} 1 \\ 1 \end{bmatrix}$. This is also a line. Notice how similar it is to the line for $K$.
</div>
Some valid point are:

$v = \begin{bmatrix} 0 \\ 1 \\ 0 \end{bmatrix}$, $v = \begin{bmatrix} -3 \\ 7 \\ -2 \end{bmatrix}$.

**This line looks awfully similar to the line for $K$ doesn't it?**

Let's see them both on the same graph. Notice that they're parallel to each other!

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1nc2gPcRmxBkXlGJCPGjyBUTpdXIsILwt" alt="Embedded Image">

Notice that $f^{-1}(\begin{bmatrix}1 \\ 1\end{bmatrix})$ is parallel to $K$. In other words, $f^{-1}(\begin{bmatrix}1 \\ 1\end{bmatrix})$ is just $K$ shifted over.

<hr />

#### Translating the Kernel

So what's the relation between the two lines we plotted above - $f^{-1}(\begin{bmatrix}1 \\ 1\end{bmatrix})$ and $K = f^{-1}(\begin{bmatrix} 0 \\ 0 \end{bmatrix})$?

<strong>$f^{-1}(\begin{bmatrix} 1 \\ 1 \end{bmatrix})$ is just a translation of $K$.</strong>

It is a translation by any vector $v \in f^{-1}(\begin{bmatrix}1 \\ 1\end{bmatrix})$.

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1-QjdP3LFgpo_yFuQAHGh7b_ejAw2F5kl" alt="Embedded Image">

Adding $K$ to $v$ gives us the full pre-image, $f^{-1}(\begin{bmatrix} 1 \\ 1 \end{bmatrix})$.
</div>

Or said another way,

<div class='highlight-block'>

$$
\begin{aligned}
f^{-1}(\begin{bmatrix}1 \\ 1\end{bmatrix}) = v + K & \text{, for any $v \in f^{-1}(\begin{bmatrix}1 \\ 1\end{bmatrix})$} \\
\end{aligned}
$$

</div>

This seems kind of too good to be true. Is it? Let's test it out!

1. Let's take a point $k \in K$. For instance, $k = \begin{bmatrix} -3 \\ 6 \\ 2 \end{bmatrix}$.
2. Let's take a $v \in f^{-1}(\begin{bmatrix} 1 \\ 1 \end{bmatrix})$ like $v = \begin{bmatrix} 0 \\ 1 \\ 0 \end{bmatrix}$.

What's $f(k + v)$?

$$
\begin{aligned}
f(k + v) &= f(\begin{bmatrix} -3 \\ 6 \\ 2 \end{bmatrix} + \begin{bmatrix} 0 \\ 1 \\ 0 \end{bmatrix}) \\
&= f(\begin{bmatrix} -3 \\ 7 \\ 2 \end{bmatrix}) \\
&= F \begin{bmatrix} -3 \\ 7 \\ 2 \end{bmatrix} \\
&= \begin{bmatrix} 2 & 1 & 0 \\ 0 & 1 & 3 \end{bmatrix} \begin{bmatrix} -3 \\ 7 \\ 2 \end{bmatrix} \\
&= \begin{bmatrix} 1 \\ 1 \end{bmatrix}
\end{aligned}
$$

So it is indeed the case here that $f(k+v)$ is $\begin{bmatrix}1 \\1 \end{bmatrix}$!

<hr />

### All Translations of the Kernel are Pre-Images

Ok there's something kind of mind blowing going on here:

1. We took one point in $f^{-1}(\begin{bmatrix} 1 \\ 1 \end{bmatrix})$.
2. We added $K$ to it.
3. And suddenly we got **ALL** of $f^{-1}(\begin{bmatrix} 1 \\ 1 \end{bmatrix})$!

In fact this is true more generally!

<div class='highlight-block'>

If you give me <strong>ANY</strong> point that maps to some point $f(v)$, say $v$, then I can find <strong>ALL</strong> the points that map to $f(v)$ by just adding $v+K$.
</div>

<hr />

### Breaking Down Why

Let's break the above statement down into two parts.

1. First, we're saying that given some $v$, all points in the set $v+K$ will map to the same place as $v$ (i.e. $f(v) = f(v+K)$).
2. Next, these are ALL the points that map to $f(v)$. Or, every point that maps to $f(v)$ must be in the set $v+K$.

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1K_7O_SlEAiPqiY2VLlRDGkZkBh3S_g_I" alt="Embedded Image">

The first statement (left hand side) simply states that all points on the line $v+K$ must map to $f(v)$. The second statement says that if a point maps to $f(v)$, like $A$, and $B$ above, then they must also fall on the line $v+K$.

Let's prove each of the above statements more formally, starting with the first.

##### 1. all points in the set $v+K$ will map to the same place as $v$

A more formal way of saying this is:

$$
f(v+K) = f(v) \text{, for any } v \in R^3
$$

Let's break down why this is true. Take any $k \in K$ (in the kernel). Then,

$$
\begin{aligned}
f(v+k) &= f(v) + f(k) & \text{Since $f$ is a linear function} \\
f(v+k) &= f(v) + 0 & \text{Since } k \in K\\
f(v+k) &= f(v)
\end{aligned}
$$

The below video shows this visually.

<div class='image-block'>
<iframe src="https://player.vimeo.com/video/330255721?quality=720p" width="640" height="564" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>
<div>

By decomposing $v+k$ into $v$, and $k$, we see that $f(v+k) = f(v)$.
</div>
</div>

Additionally, given this is true for some $v+k$, <strong>this is true for all points on the line $v+K$</strong>. The reason is that the different amounts of $K$ all contribute nothing different and it's only the value of $v$ that matters to $f$. This is shown below:

<style>
.video-container {
position: relative;
padding-bottom: 66.25%; /* 16:9 aspect ratio */
height: 0;
overflow: hidden;
max-width: 900px; /* Adjust the maximum width as desired */
margin: 0 auto; /* Center the video horizontally */
}

.video-container iframe {
position: absolute;
top: 0;
left: 0;
width: 100%;
height: 100%;
}
</style>

<div class="video-container">
<iframe src="https://player.vimeo.com/video/331617105?quality=720p" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>
</div>

Any point in $K$, such as $k$, $k'$, and $k''$, does not change the result of $f$. Hence, $f(v+K) = f(v)$.
</div>
</div>

Let's now move to the next statement.

<hr />

##### 2. Every point that maps to $f(v)$ must be in the set $v+K$

Essentially, this is saying that there can be no point $w$ such that $w$ maps to $f(v)$ but is not in $v+K$.

Let's prove this.

Choose any $v, w$ such that $f(v) = v'$ and $f(w) = v'$. We wish to show that $w \in v+K$.

1. Let $w' = w - v$.
2. Then $f(w') = f(w - v) = f(w) - f(v) = 0$.
3. Hence $w' \in K$ (as all points that map to $0$ are in $K$).
4. Thus, $v + w' \in v +K$.
5. Since $v+w' = v + w - v = w$,  $w \in v +K$.

So we've successfully proved our two points!

<hr />

### The Relation Between Translations of $K$ and Points in the Image

We've already seen something really cool - every translation of $K$ is the full pre-image of a point in $f$.

Now is there any relation between how far apart two translations of $K$ are (say $v+K$ and $w+K$) and how far apart their images are ($f(v)$, $f(w)$)?

Yes!

<div class='highlight-block'>

If $v+K$ and $w+K$ are $v'$ apart, their images will be $f(v')$ apart!

<br />

</div>

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1fSpefXn6ZoRF8WROxmDhEfbg8teSOlyn" alt="Embedded Image">

If $v+K$ and $w+K$ are $v'$ apart, their images will be $f(v')$ apart.
</div>

Why is this the case? It again follows pretty simply:

$$
\begin{aligned}
w+K &= v+K + v'+K & \text{Since $w+K$ and $v+K$ are $v'$ apart} \\
w+K &= v+v' + K & \text{ } \\
f(w+K) &= f(v+v'+K) & \text{apply $f$} \\
f(w) &= f(v+v') & \text{Since $f(w+K) = f(w)$} \\
f(w) &= f(v) + f(v') & \text{Hence f(v') apart}
\end{aligned}
$$

<hr />

### Overall Space

Let's now take a step back and view what's happening in the overall space.

Every point in the image can be seen as the image of some translation of $K$. As we move $K$ around, we get new points in the image!

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1KQjOvR95xlBrtAnhu0u0rgrf9LL7O1DS" alt="Embedded Image">

<hr />

### Conclusion

We've now seen some really cool things that you may not have noticed before:

1. Every matrix is a linear function and that linear function will have some **kernel** $K$ that maps to $0$.
2. All pre-images of output points are just going to be <strong>translations of $K$</strong>.
3. If $v'$ is the distance between the translations of $K$, $f(v')$ is the distance between their images.

The last point actually leads us to the first isomorphism theorem of group theory. This broadly states that the relation between the sets of pre-images of a special type of function known as a homomorphism (in our case $f$) is the exact same as the relation between the set of output points (we'll go into this in the next blog post!).

There are many practical uses of this knowledge but I wanted to share it for simpler reasons.  Sometimes math is just pretty - it has all these cool properties that fit together so nicely that you can't help but enjoy seeing them.

For example:

1. Who would have thought that all the pre-image sets are just translations of each other?
2. Or that the relation between these pre-image sets mirrors the relation between the points in the image?

I hope you enjoyed getting a taste of some abstract algebra and I'll see you in the next post!

