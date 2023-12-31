Welcome back! In the [last post](https://www.houseofwisdom.online/maths-courses/eigen-vectors) we derived Eigenvectors. In particular, we saw how useful they are in analyzing matrices we need to apply again and again.

In this post, we're going to dive into one of the most famous applications of Eigenvectors - the original PageRank algorithm that allowed Google to create the world's best search engine. PageRank was Larry Page's phD thesis while at Stanford. He spun out this amazing algorithm to redefine search and create one of the most iconic companies in the modern era. We're going to re-derive it here and see that it's just a simple application of Eigenvectors!

By the end of this post, you will:

1. Feel like you could have come up with PageRank yourself.
2. Understand how eigenvectors are central to PageRank.
3. See how central eigenvectors are to dynamic processes in general.

<hr />

### Making Friends

Ok let's build out our understanding of pagerank using a hypothetical scenario.

Let's say you just moved to a new city and you’re trying to make some new friends. You need to figure out which of your new friends to hang out with in your free time. But unfortunately you’re super busy and have very little free time!

So you need to rank all these potential friends to prioritize which ones to chill with.

<p class='image-block'>
<img src='https://cdn1.thr.com/sites/default/files/2012/04/anchorman_a.jpg' />

This could be you! Just need to find the friends...
</p>

In a moment of clarity you realize the following:

1. Friends you’re close with are probably going to hang out with people you’d like.
2. Someone everyone is friends with is probably someone you are going to be friends with.

You decide to use these two insights to create a scheme you call **FriendRank**.

<div class='highlight-block'>
FriendRank gives a potential friend a score (FriendScore) based on:

<ol>
<li>
How many people are friends with this person weighted by,
</li>
<li>
How close you are to the people who are friends with them.
</li>
</ol>
</div>

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1dw2eNtb4buXk2CMoAqm8CHfyATHN0glx" alt="Embedded Image">

In the above picture, how close you are to a person is shown by the size of the circle. To find your friend score for potential friend $F$, you just add up how close you are to $A$, $C$, and $D$.

Let’s write this down as a formula. Let’s say the strength of the friendship between you and some person $p$ is $FS(p)$. Let $Friends(p)$ be the set of friends of $p$.

<div class='highlight-block'>
The FS (FriendScore) for a potential friend Fred is:

$$
FS(Fred) = \sum_{p \in Friends(Fred)} FS(p)
$$

</div>

<hr />

#### Calculating Our First Friend Score

Let’s work through an example. Say you have 4 potential friends:

1. Jimmy (closeness score - 5)
2. Maya (closeness score - 9)
3. Lisa (closeness score - 8)
4. Fred (?)

In this world, you’re really close to Maya (with a score of 9) and Lisa (8) but only kinda close to Jimmy (5).

Only Jimmy and Maya are friends with Fred.

Graphically, this is:

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1ZtcLYWZRCC_Eiz0XbryZpZZU6xSEPzxk" alt="Embedded Image">

Only Jimmy and Maya claim to be friends with Fred. Lisa seems to be <a href='https://www.youtube.com/watch?v=ptmM-m7Cl8U'>tearing him apart</a>.
</div>

So:

$$
FS(Fred) = FS(Jimmy) + FS(Maya)
$$

$$
FS(Fred) = 5 + 9 = 14
$$

<hr />

#### Accounting For People who are Friends With Everyone

Not such a crazy idea right? You start this process and you realize one thing. Your really close friend Maya claims to  be friends with EVERYONE. You start wondering, "Hmm maybe I need to downweight Maya’s opinion because she doesn’t really seem to be that picky”.

This is easy - we just divide Maya’s weighting score by how many people she claims to be friends with. That way if Maya claims 100 friends, his weighting for each friend is divided by 100. So our formula is now:

<div class='highlight-block'>

$$
FS(Fred) = \sum_{p \in Friends(Fred)} FS(p) \cdot \frac{1}{NumFriends(p)}
$$
</div>

Going back to our example, our score becomes:

$$
FS(Fred) = \frac{FS(Jimmy)}{2} + \frac{FS(Maya)}{4}
$$

$$
FS(Fred) = \frac{5}{2} + \frac{9}{4} = 4.75
$$

Awesome!

Let’s now simplify this formula a little.

1. Let’s call the set of all friends $F$.
2. Let $IsFriends(p, Fred) = \begin{cases}
   1 & \text{if}\ \textrm{p calls Fred a friend} \\
   0 & \text{otherwise}
 \end{cases}$

Then we can simplify our earlier formula as shown below:

$$
FS(Fred) = \sum_{p \in Friends(Fred)} FS(p) \cdot \frac{1}{NumFriends(p)}
$$

<div class='highlight-block'>

$$
FS(Fred) = \sum_{p \in F} FS(p) \cdot \frac{IsFriends(p, Fred)}{NumFriends(p)}
$$

<div>
All the people who aren’t friends with Fred just get $0$ terms which gives us the same thing.
</div>
</div>

<hr />

#### So Who's Friends With Whom?

Ok this is looking great! You decide to go ahead and implement this scheme with your friends Bobby, Lauren, Daniel, Rony, and Saba. You start by asking all your friends to write down who they’re friends with! So you send them all the following email:

<blockquote>
<div>
From: parry.lage@boogle.com
</div>
<div>
To: Bobby, Lauren, Daniel, Rony, Saba
</div>
<div>
Subject: Who are your friends?
</div>
<br/>
<div>
My dearest "friends",
</div>
<br/>
<div>
I’m trying to rank you and all my other potential friends and need your help to do so. Below is a list of people. Please put a 1 next to their name if you call them your friend.
</div>
<div>
<br />
<table style='text-align: center;'>
<tr>
<th>Person</th>
<th>Friends?</th>
</tr>
<tr>
<td>Bobby</td>
<td>___</td>
</tr>
<tr>
<td>Lauren</td>
<td>___</td>
</tr>
<tr>
<td>Daniel</td>
<td>___</td>
</tr>
<tr>
<td>Rony</td>
<td>___</td>
</tr>
<tr>
<td>Saba</td>
<td>___</td>
</tr>
</table>
</div>
<br/>
<div>
Yours truly,
</div>
<div>
Parry Lage
</div>
<br />
<div>
P.S. Just because I'm sending you this email doesn't mean we're friends.
</div>
</blockquote>

So Saba sends you something like this:

<table style='text-align: center;'>
<tr>
<th>Person</th>
<th>IsFriends</th>
</tr>
<tr>
<td>Bobby</td>
<td>1</td>
</tr>
<tr>
<td>Lauren</td>
<td>1</td>
</tr>
<tr>
<td>Daniel</td>
<td>0</td>
</tr>
<tr>
<td>Rony</td>
<td>0</td>
</tr>
<tr>
<td>Saba</td>
<td>0</td>
</tr>
</table>

Looking good so far! You then remember you need to downweight Saba’s score by how many friends she claims to have. She’s claiming 2 friends here so we divide by 2 giving us:

<table style='text-align: center;'>
<tr>
<th>Person</th>
<th>IsFriends</th>
</tr>
<tr>
<td>Bobby</td>
<td style='background-color: lightgreen;'>1/2</td>
</tr>
<tr>
<td>Lauren</td>
<td style='background-color: lightgreen;'>1/2</td>
</tr>
<tr>
<td>Daniel</td>
<td style='background-color: lightgreen;'>0</td>
</tr>
<tr>
<td>Rony</td>
<td style='background-color: lightgreen;'>0</td>
</tr>
<tr>
<td>Saba</td>
<td style='background-color: lightgreen;'>0</td>
</tr>
</table>

Sweet.

You now decide to organize all your friends responses into a little table so that it’s easy to see. Each column of the table is a different friend. It looks like this (notice Saba's answers above are the last column in the table below):

<table style='text-align: center;'>
<tbody>
<tr>
<th></th>
<th>Bobby</th>
<th>Lauren</th>
<th>Daniel</th>
<th>Rony</th>
<th>Saba</th>
</tr>
<tr>
<td><strong>Bobby</strong></td>
<td>0</td>
<td>1</td>
<td>1/3</td>
<td>0</td>
<td style='background-color: lightgreen;'>1/2</td>
</tr>
<tr>
<td><strong>Lauren</strong></td>
<td>1/4</td>
<td>0</td>
<td>1/3</td>
<td>0</td>
<td style='background-color: lightgreen;'>1/2</td>
</tr>
<tr>
<td><strong>Daniel</strong></td>
<td>1/4</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td style='background-color: lightgreen;'>0</td>
</tr>
<tr>
<td><strong>Rony</strong></td>
<td>1/4</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td style='background-color: lightgreen;'>0</td>
</tr>
<tr>
<td><strong>Saba</strong></td>
<td>1/4</td>
<td>0</td>
<td>1/4</td>
<td>1</td>
<td style='background-color: lightgreen;'>0</td>
</tr>
</tbody>
</table>

This table is just a matrix, which we'll call $A$. The element $i,j$ in the matrix is

$$
A[i,j] = \frac{IsFriends(j, i)}{NumFriends(j)}
$$

For example, let's examine $A[1,5]$:

* Person $1$ is Bobby and Person $5$ is Saba.
* $IsFriends(5,1)$ is whether Saba claims to be friends with Bobby. We saw in her response she did, so $IsFriends(5,1) = 1$.
* $NumFriends(5)$ is the number of friends Saba has (2). Hence $NumFriends(5) = 2$.
* So $A[1, 5] = \frac{1}{2}$ just as it is in the table.

Notice additionally that $IsFriends$ is not reflexive! For instance, Rony may claim to be friends with Saba, but in the above example, Saba doesn't call Ron a friend.

Hence, $IsFriends(Ron, Saba) = 1$, but $IsFriends(Saba, Ron) = 0$.

<hr />

#### Adding Your Own Scores

You then decide you want to come up with an
initial guess for everyone's FriendScore!

There are some people you know better than others so this is really a guess for what your final FriendScore is for each of them. You write down the following and call it $FS_{0}$ - your initial FriendScore:

<table style='text-align: center;'>
<tr>
<th>Person</th>
<th>FriendScore</th>
</tr>
<tr>
<td>Bobby</td>
<td>1</td>
</tr>
<tr>
<td>Lauren</td>
<td>1</td>
</tr>
<tr>
<td>Daniel</td>
<td>1</td>
</tr>
<tr>
<td>Rony</td>
<td>1</td>
</tr>
<tr>
<td>Saba</td>
<td>1</td>
</tr>
</table>

<hr />

#### Combining Everyone's Opinion

<div class='image-block'>
<img src='https://i.guim.co.uk/img/static/sys-images/Arts/Arts_/Pictures/2012/12/19/1355935545255/Russell-Crowe-in-A-Beauti-009.jpg?width=620&quality=45&auto=format&fit=max&dpr=2&s=2d44f3a60cd54815a5658a8023be577d'/>
Omg this is a lot more work than I expected.
</div>

Ok we now have the following:

1. $A$ - a Matrix who's elements are $A[i,j] = \frac{IsFriends(j, i)}{NumFriends(j)}$.
2. $FS_0$ - An initial guess of everyone's FriendScore.

Now that we know who's friends with who, we can figure out who's really likely to be our friend.

We'd like to come up with a new FriendScore $FS_{1}$ based on this information.

How do we do that?

Recall from earlier our formula for Fred's FriendScore:

>$$
FS(Fred) = \sum_{p \in F} FS(p) \cdot \frac{IsFriends(p, Fred)}{NumFriends(p)}
$$

So similarly, we want to update our rankings, $FS_{1}$, for our friends to be:


| Person | FriendScore |
| :--: | :--: |
| Bobby | $\sum_{p \in F} FS(p) \cdot \frac{IsFriends(p, Bobby)}{NumFriends(p)}$ |
| Lauren | $\sum_{p \in F} FS(p) \cdot \frac{IsFriends(p, Lauren)}{NumFriends(p)}$ |
| Daniel | $\sum_{p \in F} FS(p) \cdot \frac{IsFriends(p, Daniel)}{NumFriends(p)}$ |
| Rony | $\sum_{p \in F} FS(p) \cdot \frac{IsFriends(p, Rony)}{NumFriends(p)}$ |
| Saba | $\sum_{p \in F} FS(p) \cdot \frac{IsFriends(p, Saba)}{NumFriends(p)}$ |

Let's shorten our notation:

1. Let $IF$ be $IsFriends$
2. Let $NF$ be $NumFriends$

Then Bobby’s ideal new ranking is:

$$
\sum_{p \in F} \frac{IF(p, Bobby)}{NF(p)} \cdot FS(p)
$$

This looks an awful lot like this dot product (go ahead and compute it!):

<div style='font-size: 17px;'>

$$
\begin{bmatrix} \frac{IF(Bobby, Bobby)}{NF(Bobby)} & \frac{IF(Lauren, Bobby)}{NF(Lauren)} & \frac{IF(Daniel, Bobby)}{NF(Daniel)} & \frac{IF(Rony, Bobby)}{NF(Rony)} & \frac{IF(Saba, Bobby)}{NF(Saba)} \end{bmatrix} \cdot \begin{bmatrix} FS(Bobby) \\ FS(Lauren) \\ FS(Daniel) \\ FS(Rony) \\ FS(Saba) \end{bmatrix}
$$
</div>

<hr />

#### Breaking Down the Dot Product - First Vector

Let's try and see if we have the two vectors in this dot product. Let's start with the first vector:

$$
\begin{bmatrix} \frac{IF(Bobby, Bobby)}{NF(Bobby)} & \frac{IF(Lauren, Bobby)}{NF(Lauren)} & \frac{IF(Daniel, Bobby)}{NF(Daniel)} & \frac{IF(Rony, Bobby)}{NF(Rony)} & \frac{IF(Saba, Bobby)}{NF(Saba)} \end{bmatrix}
$$

Where can we find this vector?

Remember the elements of $A$ are just $A[i,j] = \frac{IF(j, i)}{NF(j)}$. Let's look at $A$ again, substituting the first row of the matrix with the formula representation - we'll see that it's the same as this vector!


|  | Bobby | Lauren | Daniel | Rony | Saba |
| :--: | :--: | :--: | :--: | :--: | :--: |
| Bobby | $\frac{IF(Bobby, Bobby)}{NF(Bobby)}$ | $\frac{IF(Lauren, Bobby)}{NF(Lauren)}$ | $\frac{IF(Daniel, Bobby)}{NF(Daniel)}$ | $\frac{IF(Rony, Bobby)}{NF(Rony)}$ | $\frac{IF(Saba, Bobby)}{NF(Saba)}$ |
| Lauren |  | - | - | - | - |
| Daniel | - | - | - | - | - |
| Rony | - | - | - | - | - |
| Saba | - | - | - | - | - |

Great so we have the first vector in the dot product.

#### Breaking Down the Dot Product - Second Vector

Let's now see if we can get the second one:

$$
\begin{bmatrix} FS(Bobby) \\ FS(Lauren) \\ FS(Daniel) \\ FS(Rony) \\ FS(Saba) \end{bmatrix}
$$

You've already created this vector when you came up with your initial guesses **$FS_{0}$** in the following table:

<table style='text-align: center;'>
<tr>
<th>Person</th>
<th>FriendScore</th>
</tr>
<tr>
<td>Bobby</td>
<td>1</td>
</tr>
<tr>
<td>Lauren</td>
<td>1</td>
</tr>
<tr>
<td>Daniel</td>
<td>1</td>
</tr>
<tr>
<td>Rony</td>
<td>1</td>
</tr>
<tr>
<td>Saba</td>
<td>1</td>
</tr>
</table>

<div class='highlight-block'>

So we have both vectors of the dot product needed for finding $FS(Bobby)$.
<ol>
<li>The first vector is just the first row of $A$.</li>
<li>The second vector is $FS_{0}$.</li>
</ol>
</div>
<hr />

#### Matrix Multiplication To Find FriendScores

If we just multiply $A \cdot FS_{0}$ we compute this dot product and get $FS(Bobby)$ in the first row of the resulting vector.

$$
A \cdot FS_{0} = \begin{bmatrix} \sum_{p \in F} FS(p) \cdot \frac{IsFriends(p, Bobby)}{NumFriends(p)} \\ - \\ - \\ - \\ - \end{bmatrix} = \begin{bmatrix} FS(Bobby) \\ - \\ - \\ - \\ - \end{bmatrix}
$$

More generally, you'll find that the second row of this vector is exactly $FS(Lauren)$ etc, giving us:

$$
A \cdot FS_{0} = \begin{bmatrix} FS(Bobby) \\ FS(Lauren) \\ FS(Daniel) \\ FS(Rony) \\ FS(Saba) \end{bmatrix}
$$

<div class='highlight-block'>

So, if we call $FS_{1}$ the result of folding in the results of $A$ into your initial predictions, we get:

$$
A \cdot FS_{0} = FS_{1}
$$

</div>

<hr />

#### When Do We Stop?

Ok so we now have a super quick way of finding our next FriendScore. Just take our current guess, which we’ll call $FS_i$, multiply it by $A$, and obtain $FS_{i+1}$:

$$
FS_{i+1} = A \cdot FS_{i}
$$

Everytime we compute $A \cdot FS_{i}$, we are updating our guess of our Friend Score with the rest of our friends opinions.

When do we stop this process? We stop when $FS_{i+1}$ stops changing:

$$
FS_{i+1} = FS_{i} = FS^*
$$

<div class='highlight-block'>

At this point, which we call $FS^*$,

$$
A \cdot FS^* = FS^*
$$

Does this look like the following?

$$
Ax = \lambda x
$$

Yes!
This is exactly the formula for an eigenvector!
So the final solution $FS^*$, is an eigenvector of $A$!</strong>

<hr />

#### Seeing This Visually

How does $FS_i$ move to $FS^*$?
In many ways, the matrix $A$ pulls $FS_i$ towards its eigenvector $FS^*$.

There’s an awesome visualization of this [here](http://setosa.io/ev/eigenvectors-and-eigenvalues/) by setosa.io that I highly recommend you check out. Here’s an extract directly from their writeup. In the below image, $s1$ is an eigenvector of $A$. Notice how as we keep applying $A$ on $v$, we move closer to $s1$. In particular, the sequence $v$, $Av$, $A^2v$, ... eventually ends up directly on $s1$.

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1K7G1bNIn9i5fUAtzrh6oqogTXi8qN7hs" alt="Embedded Image">

As you keep applying $A$ on $v$, $v$ gets pulled towards the eigenvector $s_1$.

Similarly in FriendRank, as we keep multiplying $FS_{0}$ by $A$, we get the sequence $A \cdot FS_0$, $A^2 \cdot FS_0$, ... which eventually ends up on $FS^*$ - the eigenvector of $A$.

<hr />

#### From Friends to Pages

You’ve probably guessed at this point that you can switch the word friends to pages in the above and get PageRank! In the world of webpages:

1. One webpage claims to be “friends” with another if it links out to the webpage.
2. Google finds out who’s friends with who (our initial survey) by just crawling the web and finding out who links to who.
3. The number of "friends" a webpage claims to have is just the number of links present on the webpage.
4. We create the matrix $A$ by crawling the web. Once we have it, we find its eigenvector to get an estimate of the PageRanks.

<style>
.responsive-image {
max-width: 100%;
height: auto;
}
</style>

<img class="responsive-image" src="https://drive.google.com/uc?id=1Z8_M6ZD8jQXWZcZXNhQxEug0erXeWI5E" alt="Embedded Image">

To get PageRank, just replace people with pages.

Putting this together gives us a way of ranking all webpages on the internet for relevance!

I find it really cool how  PageRank models the abstract concept of webpages using simple insights into how we interact as humans.

A few quick asides:

1. The formula we've derived for PageRank is a **simplified** version of the actual one. To see the full formula, read the [original paper](http://ilpubs.stanford.edu:8090/422/1/1999-66.pdf) here.
2. Notice that PageRank is actually a next level pun. **Page**Rank was written by Larry **Page** about ranking web**pages** - well done Larry.

<hr />

### Conclusion

So we’ve seen that eigenvectors are at the heart of one of the most important algorithms of all time! More generally, whenever you see a linear function being applied again and again and again (Like $A$), you are without a doubt going to be looking for the eigenvectors of that linear function/matrix. The eigenvectors will tell you where that process ends!

I hope you enjoyed this unique and powerful application of eigenvectors. In the next post kernels, we're going to step back into Matrix Algebra. We'll learn about Kernels (or Nullspaces) and visually see how they help us immediately grasp what matrices do to their inputs.

