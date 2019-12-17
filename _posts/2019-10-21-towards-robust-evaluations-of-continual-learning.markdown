---
layout: post
title: "Towards Robust Evaluations of Continual Learning"
date: 2019-10-21 13:32:20 +0300
authors : Sebastian Farquhar, Yarin Gal
description: My summary of this paper
img: robust_eval.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Sebastian Farquhar, Yarin Gal, Continual Learning]
---

## Motivation

* Recent research work relate the problem of continual learning to increasing the dataset difficulty.
* Current experimental set-ups and evaluations are misleading as they are biased towards prior focused approaches.
* Need to encourage continual strategies that work when all the fundamental desideratum are enforced and not just a subset of them.


## Contributions 

* Thorough analysis of flaws in existing evaluations used by our community.
* Empirically show that current evaluations are biased towards prior focused approaches.
* Propose fundamental desiderata for future evaluations of continual learning strategies.
* Can be applied irrespective of the dataset.
* Propose new experimental set ups to overcome the issues of exiting ones.


## Proposed Desiderata
#### - Core Desiderata
* **A: Cross-task resemblance** : Data for new task must resemble from old task enough to produce confident predictions of old classes sometimes early in training. Permuted MNIST violates this property.
* **B: Shared output head**
* **C: No test time assumed task labels**
* **D: No unconstrained re-training on old tasks**
* **E: More than two tasks** : The more the number of tasks that a CL strategy can deal with, the better.

#### - Other desiderata
* Unclear task demarcation
* Continuous tasks
* Overlapping tasks
* Long task sequences
* Time/Compute/Memory constraints
* Strict privacy guarantees


## Critical analysis of existing evaluations

* Permuted MNIST doesn't represent real world scenarios for continual learning as it violates desiderata A.
* Multi-headed version of split MNIST requires knowledge of the task and classes in eah task apriori.
* Prior based approaches tend to perform much better in multi-headed versions than in single headed versions.
* Two task transfer is not a realistic evaluation in continual learning as algorithms might fail with more number of tasks.


## Empirical analysis of existing evaluations
* Experiments considering all the five core desiderata show that prior focussed methods suffer the most.
* Missing any desiderata can lead to blindspots in the evaluation pipeline.
* Model uncertainity can be used to detect task changes.
* Training time and accuracy must be traded off. Memory can be treated like time here.

## Insights and Conclusion

* Current evaluations are misleading as they are biased towards prior focussed approaches.
* Continual learning strategies should be evaluated by taking into consideration all the proposed core five desiderata. Single-headed split MNIST is the most simplistic experiment set-up.


<!-- ![I and My friends]({{site.baseurl}}/assets/img/we-in-rest.jpg)



>Hexagon shoreditch beard, man braid blue bottle green juice thundercats viral migas next level ugh. Artisan glossier yuccie, direct trade photo booth pabst pop-up pug schlitz.



* Hexagon shoreditch beard
* Intelligentsia narwhal austin
* Literally meditation four
* Microdosing hoodie woke

-->
