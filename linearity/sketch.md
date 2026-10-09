In terms of **linear transformations**, linearity means one very specific thing:

$$
\boxed{T(a\mathbf u+b\mathbf v)=aT(\mathbf u)+bT(\mathbf v)}
$$

for any vectors \(\mathbf u,\mathbf v\) and scalars \(a,b\).

That single equation contains the whole idea. It says:

> **Transforming a linear combination gives the same result as transforming each piece separately and then taking the same linear combination.**

There are two properties hidden inside it:

$$
T(\mathbf u+\mathbf v)=T(\mathbf u)+T(\mathbf v)
$$

and

$$
T(c\mathbf u)=cT(\mathbf u).
$$

So a linear transformation preserves **addition** and **scalar multiplication**.

For example, suppose

$$
T(x,y)=
\begin{pmatrix}
2x\\
3y
\end{pmatrix}.
$$

Take

$$
\mathbf u=
\begin{pmatrix}1\\2\end{pmatrix},
\qquad
\mathbf v=
\begin{pmatrix}3\\1\end{pmatrix}.
$$

Then

$$
T(\mathbf u+\mathbf v)
=
T\begin{pmatrix}4\\3\end{pmatrix}
=
\begin{pmatrix}8\\9\end{pmatrix}.
$$

Separately,

$$
T(\mathbf u)+T(\mathbf v)
=
\begin{pmatrix}2\\6\end{pmatrix}
+
\begin{pmatrix}6\\3\end{pmatrix}
=
\begin{pmatrix}8\\9\end{pmatrix}.
$$

Same answer. That's linearity.

This also explains the matrix interpretation you've been using. If

$$
T(\mathbf x)=A\mathbf x,
$$

then

$$
A(a\mathbf u+b\mathbf v)
=
aA\mathbf u+bA\mathbf v.
$$

So every matrix transformation is linear.

And geometrically, this means something quite powerful. Suppose your basis vectors are

$$
\mathbf e_1,\mathbf e_2.
$$

Every vector can be written as

$$
\mathbf x=x_1\mathbf e_1+x_2\mathbf e_2.
$$

Once you know where the transformation sends the basis vectors,

$$
T(\mathbf e_1),\qquad T(\mathbf e_2),
$$

linearity forces

$$
\boxed{
T(\mathbf x)
=
x_1T(\mathbf e_1)+x_2T(\mathbf e_2)
}
$$

So the transformation has **no freedom left**. Knowing where the basis vectors go tells you where every vector goes.

That's why the columns of a matrix are the transformed basis vectors:

$$
A=
\begin{bmatrix}
|&|\\
T(\mathbf e_1)&T(\mathbf e_2)\\
|&|
\end{bmatrix}.
$$

There's another extremely useful consequence:

$$
T(\mathbf 0)=\mathbf 0.
$$

Because

$$
T(0\mathbf v)=0T(\mathbf v)=\mathbf 0.
$$

So a genuinely linear transformation **must leave the origin fixed**.

For example,

$$
T(x,y)=(2x,3y)
$$

is linear, but

$$
T(x,y)=(2x+1,3y)
$$

is not, because

$$
T(0,0)=(1,0)\neq(0,0).
$$

That second transformation contains a translation. It's **affine**, not linear.

This connects directly back to your ODE question. When we write

$$
L[y]=y''+p(x)y'+q(x)y,
$$

we can think of \(L\) as a transformation whose "vectors" are functions:

$$
y(x)\quad\longmapsto\quad L[y](x).
$$

It's linear because

$$
\boxed{
L[c_1y_1+c_2y_2]
=
c_1L[y_1]+c_2L[y_2]
}
$$

just like

$$
A(c_1\mathbf v_1+c_2\mathbf v_2)
=
c_1A\mathbf v_1+c_2A\mathbf v_2.
$$

So

$$
Ay=0
$$

in linear algebra and

$$
L[y]=0
$$

in differential equations are conceptually the **same kind of problem**: you're looking for the kernel/null space of a linear transformation.

That's the deeper reason homogeneous linear ODEs behave so much like linear algebra.

---

For a linear ODE operator

$$
L[y]=y''+p(x)y'+q(x)y,
$$

linearity gives

$$
L[c_1y_1+c_2y_2]
=
c_1L[y_1]+c_2L[y_2].
$$

Now suppose we have the nonhomogeneous equation

$$
L[y]=f.
$$

Pick one particular solution \(y_p\) such that

$$
L[y_p]=f.
$$

Then any other solution \(y\) satisfies

$$
L[y]=f.
$$

Subtract:

$$
L[y-y_p]
=
L[y]-L[y_p]
=
f-f
=
0.
$$

So

$$
y-y_p\in\ker L.
$$

Therefore,

$$
\boxed{y=y_p+y_h}
$$

where

$$
y_h\in\ker L.
$$

So the full solution set is

$$
\boxed{y_p+\ker L}.
$$

And that is literally an **affine subspace**: a vector subspace, \(\ker L\), shifted by \(y_p\).

It is the exact same theorem as for a linear system

$$
A\mathbf x=\mathbf b.
$$

If \(\mathbf x_p\) is one particular solution, then every solution is

$$
\boxed{\mathbf x=\mathbf x_p+\mathbf x_h}
$$

with

$$
A\mathbf x_h=0.
$$

So you can line them up:

$$
\begin{array}{ccc}
\text{Linear algebra} && \text{ODEs}\\[4pt]
A\mathbf x=\mathbf b && L[y]=f\\
A\mathbf x_h=0 && L[y_h]=0\\
\ker A && \ker L\\
\mathbf x_p+\ker A && y_p+\ker L
\end{array}
$$

The important subtlety is that the affine-subspace result works because \(L\) itself is a **linear transformation**. The equation does not need to be homogeneous. In fact, the interesting affine-space case is specifically when

$$
L[y]=f\neq0.
$$

When \(f=0\), the shift disappears:

$$
0+\ker L=\ker L,
$$

so the solution set is an actual vector subspace rather than merely an affine one.

This is also why whether \(f\) is a constant or depends on \(x\) makes no difference. You could have

$$
L[y]=7,
\qquad
L[y]=x^2,
\qquad
L[y]=\sin x,
$$

and as long as a particular solution exists, the solution set is still

$$
\boxed{y_p+\ker L}.
$$

So the real distinction is not "constant forcing vs variable forcing." It's:

$$
\boxed{\text{linear operator }L \quad\text{vs}\quad \text{nonlinear operator}.}
$$

