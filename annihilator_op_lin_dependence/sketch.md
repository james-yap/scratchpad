We want to show that two functions of the form

\[
f(x) = e^{ax}
\]

are linearly independent as long their values of \(a\) are different.

We could do this using the Wronskian, but it is educational to use a separate technique here called the Annihilator-Operator Method.

We first define the linear operator \(L\) such that \(L\) satifies the following properties of linearity:

\[
\operatorname{L}[a] + \operatorname{L}[b] = \operatorname{L}[a + b]
\]

\[
c\operatorname{L}[a] = \operatorname{L}[ca]
\]

Combining the properties:

\[
x\operatorname{L}[a] + y\operatorname{L}[b] = \operatorname{L}[xa + yb]
\]

For a homogeneous linear \(n\)th-order DE 

\[
a_n y^{(n)}(x) + a_{n-1} y^{(n - 1)}(x) + \cdots + a_1 y^{\prime}(x) + a_0 y(x) = 0
\qquad \text{(1)}
\]

trying 

\[
y(x)=e^{rx}
\]

observe that

\[
y^{(n)}=r^ne^{rx}
\]

substituting into Eq. (1): 

\[
a_n r^ne^{rx} + a_{n-1} r^{n-1} e^{rx} + \cdots + a_1 r e^{rx} + a_0 e^{rx} = 0
\] 

\[
e^{rx}(a_nr^n+a_{n-1}r^{n-1}+\cdots+a_1r+a_0) = 0
\qquad \text{(2)}
\]

Since \(e^{rx}\neq 0\) \(\forall {x, r}\), Eq. (1) and Eq. (2) only holds when the polynomial 

\[
\operatorname{P}(r):=a_nr^n+a_{n-1}r^{n-1}+\cdots+a_1r+a_0=0
\]

We convert \(P(r)\) into factorized form 

\[
\operatorname{P}(r)=a_n((r-r_1)(r-r_2)\cdots(r-r_n))
\]

Since by the Fundamental Theorem of Algebra, every nonconstant polynomial of degree \(n\) has exactly \(n\) complex roots, counting multiplicities.

In this proof, we assume the auxiliary equation has \(n\) distinct real roots.

The following functions of \(x\) are solutions to Eq. (1):

\[
c_1e^{r_1x},c_2e^{r_2x},\cdots,c_ne^{r_nx}
\]

To prove that these functions are linearly independent, we must show that

\[
c_1e^{r_1x}+c_2e^{r_2x}+\cdots+c_ne^{r_nx}=0
\qquad \text{(3)}
\]
implies

\[
c_1=c_2=\cdots=c_n=0
\]
We will attempt this by annihilating every other term save for one, which forces the corresponding coefficient to be 0. Then, the proof is complete if we can independently repeat this procedure for every term.

Knowing that \(D\) is the differentiation operator, we reformulate Eq. (1) by applying \(P(D)\):

\[
\operatorname{P}(\operatorname{D})=a_n((\operatorname{D}-r_1)(\operatorname{D}-r_2)\cdots(\operatorname{D}-r_n))
\]

If we exclude a particular root \(k\) 

\[
\operatorname{P}_k(r)=a_n((r-r_1)(r-r_2)\cdots(r-r_{k-1})(r-r_{k+1})\cdots(r-r_n))
\]

Then define

\[
\operatorname{L}_k:=\operatorname{P}_k(D)
\]
This is the most important step. We've just created a new differential equation 

\[
\operatorname{L}_k(y)=0
\]

whose order is \(n-1\). Consequently, assuming the leading coefficient is nonzero, its solution space has dimension \(n-1\), one dimension smaller than the \(n\)-dimensional solution space of the original equation.


Applying \(L_k\) to Eq. (3), and by linearity:

\[
\operatorname{L}_k(c_1e^{r_1x}+c_2e^{r_2x}+\cdots+c_ne^{r_nx})=\operatorname{L}_k(0)
\]

\[
\operatorname{L}_k(c_1e^{r_1x})+\cdots+\operatorname{L}_k(c_ne^{r_nx})=0
\]

\[
c_1\operatorname{L}_k(e^{r_1x})+\cdots+c_n\operatorname{L}_k(e^{r_nx}) = 0
\]

At this point, 

\[
\operatorname{L}_k(e^{r_1x})= \cdots = \operatorname{L}_k(e^{r_nx})=0
\]

except

\[
L_k(e^{r_kx})\neq0
\]

because \(r_k\) is not a root of the auxiliary equation, and so \(e^{r_kx}\) is not a solution to the homogeneous equation \(L_k(y)=0\). This forces \(c_k=0\).

The key idea: \(k\) was arbitrarily chosen. Applying \(L_k\) to Eq. (3) does not change the equality, so if we repeat this process for all values of \(k\in\{1,\ldots,n\}\), we can prove that Eq. (3) forces

\[
c_1=c_2\cdots=c_n=0
\]

The equations are linearly independent.
