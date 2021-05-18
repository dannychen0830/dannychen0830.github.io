[home](./index.html)  |  [research](./research.html)  |  [notes](./notes.html)  |  [reading list](./reading_list.html)  |  [stories](./story.html)  |  [miscellaneous](./miscellaneous.html)

## Research

As mentioned before, my interest lies in stochastic things. I have also developed a new-found appreciation for statistical mechanics, or just physics in general, and its applications in computation and modeling. For the specifics, perhaps the [reading list](./reading_list.html) would paint a clearer picture. 

Below, I have listed a (few) project(s) that I have been working on recently.

### Quantum-Inspired Computation

"Quantum-Inspired" is nothing but a broad term describing algorithms that are, well, inspired by _things in the quantum world_ in some way. There are two that I am closely working with. The first was by Ewin Tang. She came up with an algorithm that, given a preference matrix, provide recommendations for a specific user in time poly-logarithmic to the input size. This result is quite mind-blowing if you look at the Kerenidis and Prakash's quantum algorithm for recommendation systems -- which also runs in time poly-logarithmic to the input size. This disproves the suspicion that quantum computers give exponential speed up over classical computers for solving machine learning problems (there are probably more complexity-theoretic nuance to this statement, so don't take cite me here). This is quantum-inspired in the sense that the algorithms. My favorite quantum-inspired work from her (and collaborators) is the improved linear regression via stochastic gradient descent (the sparsity arguments are ... really nice). 


**References:**

> Tang, Ewin. "A quantum-inspired classical algorithm for recommendation systems." Proceedings of the 51st Annual ACM SIGACT Symposium on Theory of Computing. 2019.
> 
> Kerenidis, Iordanis, and Anupam Prakash. "Quantum Recommendation Systems." 8th Innovations in Theoretical Computer Science Conference (ITCS 2017). Schloss Dagstuhl-Leibniz-Zentrum fuer Informatik, 2017.
>
> Gilyén, András, Zhao Song, and Ewin Tang. "An improved quantum-inspired algorithm for linear regression." arXiv preprint arXiv:2009.07268 (2020).
> 
> Hibat-Allah, Mohamed, et al. "Variational Neural Annealing." arXiv preprint arXiv:2101.10154 (2021).
