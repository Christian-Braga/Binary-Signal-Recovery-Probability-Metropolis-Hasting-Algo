<h2>AIM OF THE PROJECT</h2>
The aim of this project was to solve the binary signal recovery problem using Markov Chain Monte Carlo (MCMC) techniques, specifically the Metropolis-Hastings algorithm, to estimate a binary signal from noisy observations. 

<h2>WHERE DOES THE BINARY SIGNAL RECOVERY PROBLEM OCCUR?</h2>
Binary signal recovery is used across various industries to reconstruct signals affected by noise or incomplete data some examples:

- Telecommunications: In digital communications, signals transmitted over noisy channels can become corrupted. Binary signal recovery techniques, such as error detection and correction (e.g., Hamming codes), help recover the original data, ensuring reliable communication in systems like mobile and satellite networks.

- Astronomy: Observing celestial objects is often hindered by noise and interference. Binary signal recovery helps in extracting meaningful data from noisy measurements taken by telescopes, improving the detection of stars, galaxies, and other distant objects in the universe.

- Financial Technology (FinTech): In financial markets, binary signal recovery aids in identifying "buy" or "sell" decisions from noisy or incomplete market data. This improves the precision of high-frequency trading algorithms and helps traders make informed decisions in volatile environments.

<h2>Why Use Metropolis-Hastings for Binary Signal Recovery?</h2>
The Metropolis-Hastings algorithm was chosen because it is well-suited for the discrete nature of the problem. The signal space Θ consists of binary vectors, meaning that traditional machine learning techniques, which generally work in continuous spaces (like gradient-based methods), are not appropriate. In contrast, Metropolis-Hastings allows us to explore a discrete space, making it ideal for binary signal recovery.
Moreover, Markov Chain Monte Carlo methods like Metropolis-Hastings are particularly useful when the optimization landscape is complex or non-convex, which is often the case in high-dimensional spaces like the one considered here. Traditional optimization techniques might struggle with such landscapes, leading to poor estimates.

<h2>Brief Explanation of the Metropolis-Hastings Algorithm</h2>
The Metropolis-Hastings algorithm is a Markov Chain Monte Carlo method used to sample from a probability distribution when direct sampling is difficult. The algorithm constructs a Markov chain with a desired stationary distribution (in our case, the distribution concentrating around the maximum likelihood estimate). At each step, the algorithm proposes a new state, which is accepted with a certain probability depending on how much it improves the likelihood of the current state. If the new state is accepted, the chain moves to it; otherwise, it stays at the current state.
In this project, we generate new binary signal candidates by flipping one bit at random in the current signal and deciding whether to accept this new candidate based on its likelihood. Over many iterations, this process allows us to explore the state space of possible signals and concentrate on the most likely solutions.

