## Quick recap of experiment ideas

Last week I noticed that if you change up the solver tolerance, e.g. from 1f-4 to 5f-1, after training a vanilla DEQ on MNIST, the solver fails to maintain the same level of accuracy as during training. This week I worked on some visualizations to demonstrate this effect.


## Unstable steady states

Intuitively, the solver might reach a different steady state after we change up the tolerance, which is why we see the significant drop in accuracy. However, my
plotting and calculation experiments show that the solver **doesn't even find** a steady state after the tolerance change. Here is what that looks like


## PCA using solver during training


## PCA using solver after changing tolerance

![Imgur](https://imgur.com/npZpxGg)


## Some more calculations

A crude way to present the gif above in numbers is to calculate some numerical property of the DEQ iteration state. Here, I chose to simply print out the norm
of the features in each DEQ iteration. Let's compare the last few outputs of stable vs unstable steady states:

- Stable `Float32[252.54485, 251.9809, 251.49666, 250.67264, 250.55208, 249.5119, 248.81934, 248.43001, 246.85597]`
- Unstable `Float32[271.42923, 279.03033, 281.7822, 268.4024, 269.62033, 278.49048, 278.68335, 265.12357, 266.15347, 278.63004, 287.09998]`


It seems like there's a lot more fluctuation in the second row, which is why I called it "unstable steady states"
