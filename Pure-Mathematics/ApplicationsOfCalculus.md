# Maclaurin Series

We can approximate functions using polynomials that match the function's derivatives at a given point. Let us consider polynomial approximations to functions by matching derivatives at the origin.

Let $f$ be some function we aim to approximate by a polynomial $g(x)=a_0+a_1x+a_2x^2+\dots$, we can take $g$ to have any degree (potentially infinite) we like. 

Matching the $0^{\text{th}}$-derivative: $f(0)=g(0)\implies a_0=f(0)$

Matching the $1^{\text{st}}$-derivative: $f^{\prime}(0)=g^{\prime}(0)\implies a_1=f^{\prime}(0)$

Matching the $2^{\text{nd}}$-derivative: $f^{\prime\prime}(0)=g^{\prime\prime}(0)\implies a_2=\frac{f^{\prime\prime}(0)}{2}$

$$\vdots$$

Matching the $i^{\text{th}}$-derivative: $f^{i}(0)=g^{i}(0)\implies a_i=\frac{f^{i}(0)}{i!}$

If $f$ permits us to take infinitely many derivatives, we can construct the Maclaurin Series for the function $f(x)$:

$$f(x)=\sum_{i=0}^{\infty}\frac{f^{i}(0)}{i!}x^i$$

Furthermore, we require the value of the derivative to be defined at the point $x=0$. $log(x)$ is not defined at $x=0$ and so it's Maclaurin Series doesn't exist. Also, not that the Maclaurin Series may not converge for all values of $x$. In other words, their is a radius of values around the centre ($x=0$) for which this approximation makes sense. This will become clear as we consider some examples.
 
We can establish the Maclaurin Series for some standard functions:
- $e^x=1+x+\frac{x^2}{2!}+\dots+\frac{x^r}{r!}+\dots$, for all $x$
- $\log(1+x)=x-\frac{x^2}{2}+\dots+\frac{(-1)^{r+1}x^r}{r}+\dots$, for $-1<x\leq 1$
- $sin(x)=x-\frac{x^3}{3!}+\frac{x^5}{5!}-\dots+\frac{(-1)^rx^{2r+1}}{(2r+1)!}+\dots$, for all $x$
- $cos(x)=1-\frac{x^2}{2!}+\frac{x^4}{4!}-\dots+\frac{(-1)^rx^{2r}}{(2r)!}+\dots$, for all $x$
- $(1+x)^n=1+nx+\frac{n(n-1)}{2!}+\dots+\frac{n(n-1)\dots(n-r+1)}{r!}x^r+\dots$, for $\vert x\vert<1$ and $n\in\mathbb{N}$

## Extensions

As we have seen these polynomial approximations have a region in which they make sense and outside this region our series doesn't converge so is not useful for us. Suppose that we want to estimate the a function but is Maclaurin Series is not valid at this point? We have a few potential ways to solve this issue which we will explore now.

Suppose we aim to approximate the function $f(x)$ near the point $x=a$. This problem is equivalent to the problem of estimating $f(x-a)$ near the point $x=0$, which we know how to do thanks to the notion of Maclaurin series outlined above (we have seen this already as above we consider the Maclaurin expansion for $log(1+x)$ rather than $log(x)$).
Equally, we could consider a different polynomial approximation to $f$ that instead of matching derivative at $x=0$, it matches derivatives at $x=a$. This idea leads to a polynomial approximation given by
$$f(x)=\sum_{i=0}^{\infty}\frac{f^{i}(a)}{i!}(x-a)^i$$
which is called the Taylor Series for the function $f$.

# Improper Integrals

We have several types of improper integrals
1. The domain of integration is infinite
2. The integrand diverges to infinity or is undefined within the domain of integration


Let us consider the first type, which includes integrals such as $\int_a^{\infty}f(x)dx$. To evaluate this we need to consider the behavior as we approach $\infty$ as a limit (i.e. does the integral converge or diverge). In other words we compute
$$\lim_{b\to\infty}\int_a^{b}f(x)dx = \lim_{b\to\infty}(I(b))-I(a)$$

We say the improper integral converges if the limit is finite, and diverges otherwise.

For the second type of improper integral we are considering the case where the integrand is undefined at some point within the domain of integration, for example $\int_0^1\log(x)$. We note that the domain of integration can be either finite or infinite (in which case it would also be an improper integral in the first sense). 

Suppose $f(x)$ is not defined at $x=k$, where $a\leq k\leq b$, then
$$\int_a^bf(x)dx=\lim_{c\to k}\int_a^cf(x)dx+\lim_{c\to k}\int_c^bf(x)dx$$

To say that this improper integral exists we need both of these limits to be finite.

To highlight the last remark consider the following example:
Does the integral $\int_{-\infty}^{\infty}\frac{x}{1+x^2}dx$, exist? If so, what is its value?

This integral is has a domain of integration that diverges at both endpoints, to work around this issues we note that $\int_{-\infty}^{\infty}\frac{x}{1+x^2}=\int_{-\infty}^{0}\frac{x}{1+x^2}+\int_{0}^{\infty}\frac{x}{1+x^2}$, each of these integrals is improper in first sense we discussed.
$$\int_{-\infty}^{\infty}\frac{x}{1+x^2}=\lim_{a\to-\infty}\int_{a}^{0}\frac{x}{1+x^2}+\lim_{b\to\infty}\int_{0}^{b}\frac{x}{1+x^2}$$
$$=\lim_{a\to-\infty}\bigg[\frac{1}{2}\log(1+x^2)\bigg]_a^0+\lim_{b\to\infty}\bigg[\frac{1}{2}\log(1+x^2)\bigg]_0^b=-\infty+\infty$$

Now it may be tempting to say that this means that the integral is equal to $0$, but we have to be a bit more cautious than that when it comes to dealing with infinites. Using the reasoning that $-\infty+\infty=0$ can lead to some problems as I will now show.

Consider this, choose any $y\in\mathbb{R}^{>0}$ and then let $x^*=\sqrt{e^y-1}$. Then we follow a similar process as above but this time we split the integral in the following way instead, $\int_{-\infty}^{\infty}\frac{x}{1+x^2}=\int_{-\infty}^{-x^*}\frac{x}{1+x^2}+\int_{-x^*}^{x^*}\frac{x}{1+x^2}+\int_{x^*}^{\infty}\frac{x}{1+x^2}$. We note now that we have two improper integrals, but one proper integral which we can evaluate.

$$\int_{-\infty}^{\infty}\frac{x}{1+x^2}=\lim_{a\to-\infty}\int_{a}^{x^*}\frac{x}{1+x^2}+\int_{-x^*}^{x^*}\frac{x}{1+x^2}+\lim_{b\to\infty}\int_{x^*}^{b}\frac{x}{1+x^2}$$
$$=-\infty+\bigg[\frac{1}{2}\log(1+x^2)\bigg]_{-x^*}^{x^*}+\infty = -\infty+y+\infty$$

So we see that if we are willing to say that $-\infty+\infty=0$ we can make our initial integral be equal to any positive real number, which clearly does not make sense! Therefore, in this case we must say that the improper integral does not exist. 

# Revolving Curves

We call a curve that is rotated about the $x$-axis or $y$-axis a solid of revolution, the volume of which is called the volume of revolution.

Suppose we have a curve $y=f(x)$:
- When rotated about the $x$-axis the volume of revolution between $x=a$ and $x=b$ is given by $V=\pi\int_a^by^2dx$
- When rotated about the $y$-axis the volume of revolution between $x=a$ and $x=b$ is given by $V=\pi\int_a^bx^2dx$

If we want to find the volume of revolution ($V$) between two curves $f(x)$ and $g(x)$ when we rotate about the $x$-axis we calculate $V=\pi\int_a^b((g(x))^2-f(x)^2)dx$. Where $x=a$ and $x=b$ are the points where the curves intersect. 

If the curves are defined parametrically as$x=f(t)$ and $y=g(t)$, then to calculate the volume of revolution between parameter values $t_1$ and $t_2$ we calculate...
- ... $V=\pi\int_{t_1}^{t_2}y^2\frac{dx}{dt}dt$ when we revolve about the $x$-axis
- ... $V=\pi\int_{t_1}^{t_2}x^2\frac{dy}{dt}dt$ when we revolve about the $y$-axis 

## Derivation

We will now get some intuition on why we have these results. For this we will consider the case where we have a curve $y=f(x)$ and we revolve it about the $x$-axis and we are interested in the solid's volume of revolution between the points $x=a$ and $x=b$.

Let $x^*\in(a,b)$, we can approximate the volume of the solid near $x^*$ by consider a cylinder of small width, say $\delta x$. The volume of this cylinder would be $V=(\pi f(x^*)^2)\delta x$. We can imagine approximating the entire volume of interest by partitioning the interval into such cylinders each of width $\delta x$, which leads to
$$V\approx (\pi f(a)^2)\delta x+(\pi f(a+\delta x)^2)\delta x+\dots+(\pi f(b-2\delta x)^2)\delta x+(\pi f(b-\delta x)^2)\delta x$$
To get a better approximation for $V$ we would need to make $\delta x$ smaller, so we can think of taking the limit $\delta x\to 0$ of this above expression to get our $V$. In doing so we arrive at the integral result stated above. 

# Mean Value

For a function $f(x)$, between $x=a$ and $x=b$ the mean value of the function is given by
$$\frac{1}{b-a}\int_a^bf(x)dx$$

## Intuition

Suppose that the mean value of our function $f$ in this interval $(a,b)$ is $M$. Then what the above tells us is that $M(b-a)=\int_a^bf(x)dx$. We can look at this geometrically as a rectangle with base matching the size of our interval having an area equal to the area under the curve within that interval. We know such an $M$ will exist and lie between the maximum and minimum value of the function within that interval. We can imagine sliding the height of the rectangle upward, when it is at the minimum point of the function the rectangle lies completely under the curve and when we reach the maximum value of the function, the curve lies completely within our rectangle. So at some point along that sliding scale the area of the rectangle must have equaled the area under the curve, this height is our value $M$. From this we can see how $M$ can interpreted as the "average height" over our function across this interval. 
