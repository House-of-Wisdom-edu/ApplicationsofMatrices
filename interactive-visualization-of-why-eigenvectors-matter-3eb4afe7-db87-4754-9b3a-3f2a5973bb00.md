You've probably heard the word eigenvectors hundreds of times in class and have been asked to calculate it hundreds more. But why is this concept so central in Linear Algebra? Why is it that we study the eigenvector of a matrix so often?

In this post, we'll see how Eigenvectors help us immediately understand what a linear function will do to an input. We'll do so by playing with an interactive visualization that allows us to see just that.

### Quick Refresher

<p class='image-block'>
<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1YO9qsPZD6hwyi5r3RFbtY1D4gfDSZ8fk" alt="Embedded Image">

Here, applying $A$ on its eigenvector $v$ leades to a new vector $\lambda v$ is in the same direction as $v$. Image Source: Wikipedia.
</p>

Let's do a quick refresher to begin with. The eigenvector of a linear function $A$ is just the vector $v$ s.t. $Av = \lambda v$ for some constant $\lambda$ which we call the eigenvalue. At a high level, the eigenvector is just a dimension along which the linear function only stretches its input (for real valued eigenvalues).

This is great and all but what can we do once we find an Eigenvector? What does it tell us about the underlying Matrix?

### Linear Functions Pull Inputs Towards the Dominant Eigenvector

Let's start with an example. Take the following linear function:

$$
A = \begin{bmatrix}3 & 2 \\ 1 & 4\end{bmatrix}
$$

Let's see what happens when we apply $A$ repeatedly on the input $\begin{bmatrix} 0 \\ 1\end{bmatrix}$.

{% comming soon!! %}

To play with this visualization, do the following:

1. Drag the slider to increase the number of times we apply $A$.
2. Notice how the output vector tilts towards $v_1$, an eigenvector of $A$.

So just by knowing an eigenvector of $A$ (namely the dominant eigenvector), we can get a sense of what $A$ does -  $A$ **pulls** its input towards the axis of the dominant eigenvector.

How is this happening? And why is it only towards one eigenvector?

### Breaking Up the Input With an Eigenbasis

You'll be surprised to see that this behavior comes very naturally from the properties of linear functions.  Let's see this with an example.

Let's keep the same matrix/linear function $A = \begin{bmatrix}3 & 2 \\ 1 & 4\end{bmatrix}$, and analyze applying $A$ three times on the input $v = \begin{bmatrix} 0 \\ 1 \end{bmatrix}$ (i.e. $A^3v$).

<p class='image-block'>
<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1cCcT1JpStCMk3qabikMAd0wG0JnDgQaE" alt="Embedded Image">

In the standard way, we'd just use standard matrix multiplication to find $A^3v.$
</p>

The standard way to do this is to simply follow the rules of multiplication and carry out $A(A(A(v))).$ But instead, let's do this a different way using eigenvectors.

<p class='image-block'>
<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1ee3PH492ikmdJqcHfQrGQXq_VMmJU9rk" alt="Embedded Image">

In the following discussion we will split $v$ into a linear combination of $A$'s eigenvectors. We then apply $A^3$ to each of these pieces and combine the result.
</p>

We know that that any vector $v$ can be written as the sum of the eigenvectors of $A$. After all, eigenvectors are linearly independent and form a basis for the space (if the matrix $A$ is diagonalizable, which it is). If $v_1$ and $v_2$ are the eigenvectors of $A,$ we can break up $v$ as:

$v = c_1 \cdot v_1 + c_2 \cdot v_2$ for some constants $c_1$ and $c_2.$

<p class='image-block'>
<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1yosuaCCDJ3kOrfzWYkvLMDCJpTlwByOo" alt="Embedded Image">

We first split $v$ into its eigenvector subcomponents.
</p>

When we have this representation, we can then rethink $A^3v$ as:

$$
A^3v = A^3(c_1 \cdot v_1 + c_2 \cdot v_2)
$$

or more simply:

$$
A^3v = c_1 \cdot A^3v_1 + c_2\cdot A^3v_2
$$

<p class='image-block'>
<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=174l0146ucu7UYcWqjc9ZpUwqb1NbF_yM" alt="Embedded Image">

We then carry out $A^3v_1$ and $A^33v_2.$
</p>

We then carry out the computation of $A^3v_1$ and $A^3v_2$. Thanks to $v_1$ and $v_2$ being eigenvectors, we have:

$$
A^3v_1 = \lambda_1^3v_1
$$

$$
A^3v_2 = \lambda_2^3v_2
$$

<p class='image-block'>
<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1lqTbYzL-r6HrdfnA_hj7OzB1llXE7nI2" alt="Embedded Image">

We finally combine the results to get $A^3v.$
</p>

We then finally combine the results to get $A^3v.$ We find:

$$
A^3v = c_1 \lambda_1^3v_1 + c_2 \lambda_2^3v_2
$$

### Dominant Eignevalues and Eigenvectors

Now, what happens when $|\lambda_1|$ is larger than $|\lambda_2|$ (i.e. there exists a dominant eigenvalue)? In this example, $\lambda_1 = 5$ and $\lambda_2 = 2.$ Let's now display what it would look like to carry out $A^3v$ when we have this difference in eigenvalues.

The interaction below shows this setup:

<br/>
<br/>

{% include eigenvectors.html %}

<br/>
<br/>

1. Drag the slider to increase or decrease the number of times we apply $A$ on $v.$
2. Notice how "Output Eigenvector 1" and "Output Eigenvector 2" change at different rates.
3. Notice how "Final Output Vector" tilts towards "Output Eigenvector 1" as you drag the slider to the right.

We thus see that when there's one eigenvalue larger than the other ($|\lambda_1| > |\lambda_2|$), the linear function pushes its inputs towards the eigenvector associated with that large eigenvalue ("Output EigenVector One"). The more times we apply $A$, the larger this effect.

Note this "push" effect will only happen towards this eigenvector with the largest eignevalue - not any of the other eigenvectors.

### Why this happens

This tilt towards "Output Vector One" happens due to exponential growth. $\lambda_1^x$ grows much faster than $\lambda_2^x$. As such the more times we apply $A$ ($x$ in our exponentials), the bigger the difference between $\lambda_1^x$ and $\lambda_2^x.$ Hence the $v_1$ term has much more weight in the final sum. This increasing difference is shown in the plot below.

<p class='image-block'>
<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1CGMOjwitFU01lc2dTjMw3O-pUp0MqBny" alt="Embedded Image">

Due to the power of exponentials, the dominant eigenvector will play a bigger and bigger role the more times we apply A. Notice how the distance between the two expontial functions increases with x.
</p>

## Conclusion

So, just using the properties of linear functions, we are able to see why eigenvectors are so important. They show us where a linear function will "push" its inputs.

If you've enjoyed this post on eigenvectors, check out the following additional posts on the topic I've written:

1. [You could have come up with eigenvectors. Here's how.](https://www.dhruvonmath.com/2019/02/25/eigenvectors/)
2. [How Eigenvectors Power PageRank - the algorithm behind Google Search.](https://www.dhruvonmath.com/2019/03/20/pagerank/)

Thanks for reading!

### Caveat

1. Everything I've discussed is for real eigenvalues.
2. This only applies for matrices that are diagonalizable.

#### Credits

Thanks to Luis Serrano, Rouzbeh Shirvani, and Pranav Ramkrishnan for feedback.

