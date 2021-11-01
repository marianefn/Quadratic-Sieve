# Quadratic Sieve factorization algorithm

This code was implemented in the context of the thesis "Study of Quadratic Sieve factorization algorithm" by Dantouri Maria Nefeli with the help of Professor Konstantinos Draziotis. 

The Quadratic Sieve factorization algorithm (QS) was the fastest factorization algorithm until the invention of the Number Field Sieve (NFS) in 1993. For integers with less than 110 decimal digits, QS remains the fastest, and it is considerably simpler than NFS.


### Algorithm

$\bf{\text{input}}$ $n,B$ 

$\bf{\text{output}}$ Prime factors of $n$ 


${\bf 1}.$ $S\leftarrow \{-1,2,p_2,...,p_t\}$ such that legendre $(n,p_i)=1$ and $p_2<p_3<\dots<p_t\leq B$

${\bf 2}.$ $m \gets \lfloor \sqrt n \rfloor$

${\bf 3}.$ Collect $t+1$ pairs $(a_i,b_i)$, $x = 0, \pm1, \pm2 \cdots$. $i\gets 1$. While $i \le t+1,$ do:

${\quad \quad \bf 3.1}.$ $b=q(x)=(x+m)^2-n$. Check if b is $B$-smooth. If not, pick new $x$

${\quad \quad \bf 3.2}.$ If $b$ is $B$-smooth and $b \prod_{j=1}^t {p_j}^{e_{ij}}$, then $a_i\gets (x+m), b_i\gets b$, and $u_i=(u_{i1},u_{i2},\cdots,u_{it})$, where $u_{ij}=e_{ij} \mod 2$ for $1\le j \le t$

${\quad \quad \bf 3.3}.$ $i\gets i+1$

${\bf 4}.$ With linear algebra find a non-empty subset $T \subseteq \{1,2,\cdots.t+1\}$, such that $\sum_{i\in T} u_i = 0$

${\bf 5}.$ $x=\prod_{i\in T} a_i \mod n$

${\bf 6}.$ For each $j, 1\leq j \leq t, l_j = (\sum_{i\in T} e_{ij}/2)$

${\bf 7}.$ $y=\prod_{j=1}^t {p_j}^{l_j}\mod n$ 

${\bf 8}.$ If $x\equiv \pm y \mod n$, find another subset $T$ and go to step 5.

${\bf 9}.$ $d=\gcd(x-y,n)$ and return $d$
