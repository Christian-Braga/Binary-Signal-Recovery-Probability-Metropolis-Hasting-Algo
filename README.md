Abstract. The scope of the present project is to illustrate how to recover a binary signal from noisy observations
using Markov Chain Monte Carlo techniques.
Binary signal recovery via maximum likelihood estimate
Let X ∈Rm×d be a random sensing matrix with i.i.d. entries sampled from N(0,1). Let ξ ∈Rm
be a noise vector, independent of X, with i.i.d. entries sampled from N(0,1).
Take Θ = {0,1}d (signal space) and let θ ∈Θ (signal) be chosen uniformly at random and be
independent of the pair (X,ξ).
The measurement vector y∈Rm is generated as
y= Xθ+ ξ.
We want to recover the unknown vector θ using Markov Chain Monte Carlo techniques, given the
observations (X,y). We are interested in the case when d is large. We recover θ by finding the
maximum likelihood estimate.
ˆ
In the present setting, the maximum likelihood estimate of θ is given by the value
maximizes the likelihood function
θ ∈Θ that
L(X,y; θ) = exp{−1
2 (y−Xθ)T(y−Xθ)}
(2π)m/2 ,
given the observations (X,y). Here the superscript T represents the transpose operation. We
can equivalently cast the question in the form of a minimization problem. Indeed, the maximum
ˆ
likelihood estimate of θ is given by the value
θ∈Θ that minimizes the function
H(X,y; θ) = (y−Xθ)T(y−Xθ),
given the observations (X,y).
Metropolis-Hastings algorithm
Let β >0 be a fixed real parameter. We construct the Metropolis-Hastings (discrete-time) Markov
chain on the state space Θ, with stationary distribution
πβ(θ) = e−βH(X,y;θ)
, with Zβ=
e−βH(X,y;θ)
.
Zβ
θ∈Θ
Observe that the probability distribution πβ concentrates on the maximum likelihood estimate
as β →+∞. Therefore, if we choose β suﬃciently large and we run the chain for a large number
ˆ
N of steps, we can take the state visited at time N as the maximum likelihood estimate
θ.
The following algorithm produces the first N steps θ1,...,θN of the Metropolis-Hasting chain on Θ.
Input: Output: value of the parameter β;
number of steps N;
¯
initial state
θ∈Θ;
trajectory of the Metropolis-Hastings chain starting at
¯
θ;
Procedure
Step 1. Set θ0 =
¯
θ.
Step 2. For t= 1,2,...,N−1:
1. pick i uniformly at random in {1,2,...,d};
2. let the proposed state be θ∗∈Θ, with entries
θ∗(j) =
θt−1(j) if j ̸= i
1−θt−1(j) if j= i (j = 1,2,...,d);
3. set
θt =
          
θ∗ with probability min 1,
θt−1 with probability 1−min 1,
e−βH(X,y;θ∗ )
e−βH(X,y;θt−1 )
e−βH(X,y;θ∗ )
e−βH(X,y;θt−1 ).
Project
ˆ
By implementing the Metropolis-Hastings algorithm above, we determine an estimate
θ of a signal
θ∈Θ for any given realization of (X,y). To check the quality of our estimate, we analyze the mean
squared error
E= E (
ˆ
θ−θ)T(
ˆ
θ−θ),
where the expectation is over θ and (X,y), for diﬀerent values of m (number of measurements).
Fix d= 10. For every 1 ≤m≤15, compute the mean squared error. Plot Eas a function of mand
comment on the characteristics of your plot. What is the minimum value ofm
d required to reliably
recover θ?
Remark. The mean squared error Ecan be estimated by exploiting the law of large numbers. Let
ˆ
M denote the number of independent realizations of (θ,X,y). Moreover, let
θ(j) be the maximum
likelihood estimate of the j-th signal θ(j), obtained by the j-th run of the Metropolis-Hastings
algorithm, given (X(j),y(j)). If M is suﬃciently large (use M of order 104), then we have the
approximation
E≈ 1
M
M
j=1
ˆ
θ(j) −θ(j) T ˆ
θ(j) −θ(j)
.
References
[1] Levin D.A. and Peres Y., Markov chains and mixing times, Volume 107, American Mathematical
Society, 2017
[2] Ross S.M., Simulation, Academic Press, 2006
