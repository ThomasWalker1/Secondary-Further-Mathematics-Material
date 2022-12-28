We can use matrices to do many things, in this section we will look at how they can be used to solve simultaneous equations and represent transformations. 

# Simultaneous Equations

We can encode simultaneous equations within a system of matrices and vectors, we can then use operations on these vectors to manipulate the system of equations with the intention to try an solve them.

$$\begin{matrix}a_{11}x_1+a_{12}x_2+\dots+a_{1n}x_n=b_1\\a_{21}x_1+a_{22}x_2+\dots+a_{2n}x_n=b_2\\\vdots\\a_{m1}x_1+a_{m2}x_2+\dots+a_{mn}x_n=b_m\end{matrix}$$
becomes
$$\begin{pmatrix}a_{11}&a_{12}&\dots&a_{1n}\\a_{21}&a_{22}&\dots&a_{1n}\\&&\vdots\\a_{m1}&a_{m2}&\dots&a_{mn}\end{pmatrix}\begin{pmatrix}x_1\\x_2\\\vdots\\x_n\end{pmatrix}=\begin{pmatrix}b_1\\b_2\\\vdots\\b_m\end{pmatrix}\implies\mathbf{Ax=b}$$

From this we can see that if $\mathbf{A}$ is invertible then we can solve for $\mathbf{x}$, $\mathbf{x=A^{-1}b}$. However, $\mathbf{A}$ is not always invertible.
In the case where $\mathbf{A}$ is invertible we say that $\mathbf{A}$ is non-singular and the system of linear equations has a unique solution. 
In the case where $\mathbf{A}$ is not invertible, we say that $\mathbf{A}$ is singular and the system of linear equations will not have a unique solution. 

# Transformations

When we multiply a vector by a matrix we end up with another vector. If we suppose this vector represents a point in space, then the matrix can be thought as transforming a point into another point, i.e. a transformation. 

Suppose we have a matrix $M$ and a vector $(x,y)^T$ with the image of this vector under the transformation $M$ given by $(x^{\prime},y^{\prime})^T=M(x,y)^T$.
We want to understand what the transformation $M$ really is, does it shift the vector, does it scaled the vector, does it rotate the vector etc?

To do this we are going to consider what it does to the unit vectors $(1,0)^T$ and $(0,1)^T$, the reason we do this is because $(x,y)^T=x(1,0)^T+y(0,1)^T$, so by the linearity of matrix multiplication $M(x,y)^T=xM(1,0)^T+yM(0,1)^T$.
$$\text{Let }M=\begin{pmatrix}a&b\\c&d\end{pmatrix}\text{ then }M(1,0)^T=(a,c)^T\text{ and }M(0,1)^T=(b,d)^T$$
Now we can imagine forming a unit square with point $(0,0), (1,0), (0,1)$ and $(1,1)$. From the above analysis we see that the transformation $M$ transforms this unit square into another quadrilateral with points $(0,0), (a,c), (b,d)$ and $(a+b, c+d)$ respectively. So recognizing the effect that $M$ has on this unit square will allow us to identify a transformation to $M$.

What we should note that any transformation represented by a matrix will transform the origin to itself as $M(0,0)^T=(0,0)^T$.

## Standard Results

We have some results for some standard transformations
- Rotation anticlockwise about the origin by...
  -  ...$90^{\degree}$ is represented by the matrix $\begin{pmatrix}0&-1\\1&0\end{pmatrix}$
  -  ...$180^{\degree}$ is represented by the matrix $\begin{pmatrix}-1&0\\0&-1\end{pmatrix}$
  -  ...$270^{\degree}$ is represented by the matrix $\begin{pmatrix}0&1\\-1&0\end{pmatrix}$
- Reflection in line...
  - ...$y=0$ is represented by the matrix $\begin{pmatrix}1&0\\0&-1\end{pmatrix}$
  - ...$x=0$ is represented by the matrix $\begin{pmatrix}-1&0\\0&1\end{pmatrix}$
  - ...$y=x$ is represented by the matrix $\begin{pmatrix}0&1\\1&0\end{pmatrix}$
  - ...$y=-x$ is represented by the matrix $\begin{pmatrix}0&-1\\-1&0\end{pmatrix}$
- Enlargement with centre at the origin and a scale factor of $k$ is represented by the matrix $\begin{pmatrix}k&0\\0&k\end{pmatrix}$

Now that we can relate a transformation to a matrix, we can now investigate the transformations by manipulating the matrix. For example, what does the determinant of the matrix tell us about the transformation?

## Properties of Transformations

The determinant of the matrix relates to the how the transformation preserves area and orientation. This is more clearly illustrated if we refer back to our unit square. Suppose we have a transformation represented by matrix $M$. 
- $\vert\det(M)\vert$ gives the area scale factor for the transformation, our unit square goes from having area $1$ to having area $\vert\det(M)\vert$
- If $\det(M)>0$, then the orientation of the points on our unit square is preserved (i.e. going from $(1,0)$ to $(1,1)$ to $(0,1)$ would take us in a anticlockwise direction before and after the transformation), whereas if $\det(M)<0$ then the orientation is not preserved (i.e. going from the image of the points of $(1,0)$ to $(1,1)$ to $(0,1)$ would now take us in a clockwise direction).


Note in the above discussion we point aside the case when $\det(M)=0$, let us explore that now.
We know that a matrix $M$ having determinant $0$ means that is not invertible. Therefore, if we let $M$ represent a transformation, this means that once we apply the transformation we cannot reverse it (we must be losing some information during the transformation). If we blindly extend our results from above that suggests that the determinant is analogous to an area scale factor, this means that the result of applying the transformation $M$ to the unit square is a shape with area $0$. Let us consider an example then in order to justify are thoughts. 

Let $M=\begin{pmatrix}0&0\\0&1\end{pmatrix}$, clearly $\det(M)=0$. When applied to the unit square $(1,0)$ is mapped to $(0,0)$ and $(0,1)$ is mapped to itself. So we can see that $M$ maps everything parallel to the $x$-axis and onto the $y$-axis. So the unit square is mapped to a line, which has area $0$, and we cannot possibly think about reversing this transformation as infinitely many points are mapped to the same point. For instance, $(x,0)$ is mapped to the origin for any $x\in\mathbb{R}$, we are losing information about the $x$ coordinate for each point. 

## Composing Transformations

We have investigated a single transformation, but what if we want to compose transformations? Luckily we have the following result. If $A$ and $B$ are matrices representing two transformations, then $C=BA$ is a matrix representing the transformation of $A$ followed by $B$ (Note the ordering). 

We should take a moment to see that this make sense. We know that to transform a vector $v$ by transformation $A$ we calculate, $Av$ to give another vector. If we then wish to apply transformation $B$ we have to calculate $B(Av)= BAv$, so indeed this make sense. 

From this we can see that if we want to undo a transformation $A$, we apply the transformation given by $A^{-1}$ as $A^{-1}A=I$, so the composition of these two transformations gives the identity transformation as desired.

## Further Example of Matrix Transformations

### Rotations

We can generalize the rotation matrices we saw above to matrices that represent rotations through angle $\theta$ anticlockwise about the origin. Such a transformation is represented by
$$\begin{pmatrix}\cos(\theta)&-\sin(\theta)\\\sin(\theta)&\cos(\theta)\end{pmatrix}$$
To construct this matrix all we have to do is to consider the effect of such a rotation on the points $(1,0)$ and $(0,1)$.

### Stretches

$\begin{pmatrix}c&0\\0&1\end{pmatrix}$ represents a stretch with scale factor $c$ parallel to the $x$-axis.
Similarly, $\begin{pmatrix}1&0\\0&d\end{pmatrix}$ represents a stretch with scale factor $d$ parallel to the $y$-axis.

### Shears

This is a transformation moving points parallel to an axis, with points further away from the axis moving a greater distance. 

$\begin{pmatrix}1&0\\k&1\end{pmatrix}$ represents a shear with the $y$-axis invariant and mapping $(1,0)$ to $(1,k)$. $\begin{pmatrix}1&k\\0&1\end{pmatrix}$ represents a shear with the $x$-axis invariant and mapping $(0,1)$ to $(k,1)$.

## Invariance

We have seen that the origin is always mapped to itself, we say that the origin is invariant under any linear transformations. Is this the only invariant point? The answer to this question most definitely depends on the transformation in question. As I hope it is clear to see that for a rotation the origin is the only such point, but for a reflection we have an entire line of such points. 

Let us try an formalize the notion of invariant points so that we can investigate it further. 

Suppose we have a transformation represented by a matrix $M$, a point is invariant under this transformation if
$$M\begin{pmatrix}x\\y\end{pmatrix}=\begin{pmatrix}x\\y\end{pmatrix}$$
This is a system of simultaneous equations that we can solve, the solution of which will be the set of invariant points under the transformation.

Let us extend the idea of invariant points further, and consider an invariant line. That is, for any point on the line its image will remain on the line. Take the example of a shear that keeps the $x$-axis invariant, then any line parallel to the $x$-axis would be an invariant line. We should note that an invariant line is a weaker notion than a line of invariant points, as in the later each point must be mapped back to itself whereas in the latter each point needs only to be mapped to another point on the line. 


