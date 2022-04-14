In this tutorial, I present Generative Flow Networks [1, 2, 3, 4, 5, 6], which is a model recently developed by researchers from [MILA](https://mila.quebec/) (Quebec Artificial Intelligence Institute). The main goal of this tutorial is to show how GflowNets can be implemented. I will just present the general idea, then an implementation on tree synthetic tasks : Hyper-grid environment, sequence and image generation.

I also present in the introduction, alternative methods such as : 
* Inverse Transform Sampling, Acceptance-Rejection and Important Sampling
* MCMC methods : Metropolis-Hasting, Gibbs sampling and Metropolis-adjusted Langevin 

This tutorial is divided into 4 parts (4 notebooks) :

1. Introduction
2. Implementation : Hypergrid environment
3. Implementation : Image Generation, GAN
4. Implementation : Sequence Generation

# References
```
[1] @article{
  DBLP:journals/corr/abs-2106-04399,
  author    = {Emmanuel Bengio and Moksh Jain and Maksym Korablyov and Doina Precup and Yoshua Bengio},
  title     = {Flow Network based Generative Models for Non-Iterative Diverse Candidate Generation},
  journal   = {CoRR},
  volume    = {abs/2106.04399},
  year      = {2021},
  url       = {https://arxiv.org/abs/2106.04399},
  eprinttype = {arXiv},
  eprint    = {2106.04399},
  timestamp = {Fri, 11 Jun 2021 11:04:16 +0200},
  biburl    = {https://dblp.org/rec/journals/corr/abs-2106-04399.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}

[2] @article{
  DBLP:journals/corr/abs-2111-09266,
  author    = {Yoshua Bengio and Tristan Deleu and Edward J. Hu and Salem Lahlou and Mo Tiwari and Emmanuel Bengio},
  title     = {GFlowNet Foundations},
  journal   = {CoRR},
  volume    = {abs/2111.09266},
  year      = {2021},
  url       = {https://arxiv.org/abs/2111.09266},
  eprinttype = {arXiv},
  eprint    = {2111.09266},
  timestamp = {Mon, 22 Nov 2021 16:44:07 +0100},
  biburl    = {https://dblp.org/rec/journals/corr/abs-2111-09266.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}

[3] @article{
  DBLP:journals/corr/abs-2201-13259,
  author    = {Nikolay Malkin and Moksh Jain and Emmanuel Bengio and Chen Sun and Yoshua Bengio},
  title     = {Trajectory Balance: Improved Credit Assignment in GFlowNets},
  journal   = {CoRR},
  volume    = {abs/2201.13259},
  year      = {2022},
  url       = {https://arxiv.org/abs/2201.13259},
  eprinttype = {arXiv},
  eprint    = {2201.13259},
  timestamp = {Wed, 02 Feb 2022 15:00:01 +0100},
  biburl    = {https://dblp.org/rec/journals/corr/abs-2201-13259.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}

[4] @article{
  DBLP:journals/corr/abs-2202-01361,
  author    = {Dinghuai Zhang and Nikolay Malkin and Zhen Liu and Alexandra Volokhova and Aaron C. Courville and Yoshua Bengio},
  title     = {Generative Flow Networks for Discrete Probabilistic Modeling},
  journal   = {CoRR},
  volume    = {abs/2202.01361},
  year      = {2022},
  url       = {https://arxiv.org/abs/2202.01361},
  eprinttype = {arXiv},
  eprint    = {2202.01361},
  timestamp = {Wed, 09 Feb 2022 15:43:35 +0100},
  biburl    = {https://dblp.org/rec/journals/corr/abs-2202-01361.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}

[5] @article{Deleu2022BayesianSL,
  title={Bayesian Structure Learning with Generative Flow Networks},
  author={Tristan Deleu and Ant'onio G'ois and Chris Emezue and Mansi Rankawat and Simon Lacoste-Julien and Stefan Bauer and Yoshua Bengio},
  journal={ArXiv},
  year={2022},
  volume={abs/2202.13903}
}

[6] @article{
  Jain2022BiologicalSD,
  title={Biological Sequence Design with GFlowNets},
  author={Moksh Jain and Emmanuel Bengio and Alex Garc{\'i}a and Jarrid Rector-Brooks and Bonaventure F. P. Dossou and Chanakya Ajit Ekbote and Jie Fu and Tianyu Zhang and Micheal Kilgour and Dinghuai Zhang and Lena Simine and Payel Das and Yoshua Bengio},
  journal={ArXiv},
  year={2022},
  volume={abs/2203.04115}
}

[7] MCMC and Bayesian Modeling, 2017, Martin Haugh, Columbia University
http://www.columbia.edu/~mh2078/MachineLearningORFE/MCMC_Bayes.pdf

[8] Bayesian Modeling and Inference Lecture, April 5, 2010, Monte Carlo Sampling, Michael I. Jordan and Sagar Jain
https://people.eecs.berkeley.edu/~jordan/courses/260-spring10/lectures/lecture17.pdf

[9] Professor Karl Sigman's Lecture Notes on Simulation, http://www.columbia.edu/~ks20/4404-Sigman/Simulation-Sigman.html
``` 