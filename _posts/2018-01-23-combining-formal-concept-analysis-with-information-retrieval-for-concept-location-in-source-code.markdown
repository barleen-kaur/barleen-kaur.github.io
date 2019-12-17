---
layout: post
title: Combining formal concept analysis with Information retrieval for concept location in source code
date: 2018-01-23 13:32:20 +0300
authors : Denys Poshyvanyk, Andrian Marcus
description: My summary of this paper
img: lattice.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Denys Poshyvanyk, Andrian Marcus, NLP, FCA, Software]
---

## Motivation

Information retrieval is used to generate the list of potential source code modules, which a
developer might be interested in changing, in order to fix the bugs. In most cases, the resultant list is large enough for a developer to first search through sequentially to locate the concept of interest. This also overloads the developers to refine their queries multiple times to get smaller result sets. This paper outlines the importance of merging Formal concept analysis (FCA) and Latent semantic indexing (LSI) in order to locate the concept in source code with minimized programmer’s effort.


## Assumptions
* Only identifiers and comments are used as representation of source code.
* The objects(documents) can be grouped by shared attributes.
* Penalizing terms which are present in list of unselected documents will help in choosing
better attributes.


## Proposed Solution
The process of concept location is divided into multiple stages:
* **Building the corpus**: On the basis of the level of granularity set by the developers,
comments and identifiers extracted from the source code are parsed to build the corpus
in the form of documents such that each document represents a module.
* **Corpus Indexing**: Each document in the corpus, represented in the vector space, is
indexed using LSI securing the semantic relationship of comments and identifiers in the
source code.
* **Defining the queries**: Terms used by the developers are matched with the vocabulary of
the source code. If a term has no match found, then words having similar semantics are
suggested.
* **Ranking documents**: Documents in the source code are ranked in order of decreasing
similarity scores with respect to developer’s query.
* **Selection of descriptive attributes**: Attributes(terms) shared by the first n documents inthe ranked list are selected.
* **Applying FCA**: A concept lattice structure is formed from the set of n highly ranked
documents and the shared attributes. Each node in the lattice has a descriptive label
which corresponds to an attribute and the list of documents sharing that attribute.
* **Analyzing the results**: User traverses through the lattice to locate the concept or
redefines his query.


## Evaluation
The authors have evaluated their research work using Eclipse as a platform.
Using methods as the level of granularity, the documents in the source code of eclipse are
preprocessed and indexed using LSI as mentioned in the methodology.
The authors have introduced two evaluation metrics:
* Lattice distillation factor(LDF): degree of improvements made in precision with the
concept lattice over ranking list of documents.
* Lattice browsing capacity(LBC): percentage of nodes in the concept lattice that a user
needs to explore in order to locate the first occurrence of concept.
* The authors studied the effect of varying the number of documents (n) chosen from the ranked list and number of shared attributes (k) on the ease of locating concept in case of two bugs in eclipse. Experimental results show significant improvement in the field of concept location through lattice structure with LDF reaching 318%.


## Possible threats to Validity of the proposed solution

* Finding the optimal value of number of documents (n) and shared attributes(k):
Deciding on the factors n, k so that the results are optimized is important as in the
paper, results show that the authors couldn’t generate any desired results in case of 80
documents for bug #25457.
* Evaluation was done taking just two bugs into account. Their approach should have
been evaluated on more software platforms and different program architectures.
* The proposed solution is highly dependent on how the developer frames the query.
* In order to fix a bug, multiple modules of source code can be involved. So, if the
groupings of objects based on shared attributes represented as nodes in the lattice is
incorrect, then the validity of proposed solution is doubtful.
* Considering only comments and identifiers as representatives of the source code is a
possible threat.


## Limitations/Extensions

* This work should have been evaluated on more software platforms and different
program architectures.
* Building rules/algorithms for deciding the optimal number of documents to choose
from the ordered list and which shared attributes to consider in order to build the
concept lattice.
* Ranked list is used only for the purpose of selecting the documents. In addition to this, it
should also be used to position the documents in the lattice.
* Making standards/possible suggestions on how queries should be formulated.
* A developer still has to reframe his query if he doesn’t get the desired results in one go.
* Involving more features other than comments and identifiers and examining the results.


## Limitations/Extensions

* This work has shown a promising direction in the field of software engineering by
speeding the process of locating concept by clubbing techniques of formal concept
analysis and information retrieval.
* Features can be clubbed together and represented in the form of lattice structures
which can expedite the process of information retrieval.
* Provided insights on how to choose evaluation measures like Lattice distillation
factor(LDF) and Lattice browsing capacity(LBC) in such domain problems.



<!-- ![I and My friends]({{site.baseurl}}/assets/img/we-in-rest.jpg)



>Hexagon shoreditch beard, man braid blue bottle green juice thundercats viral migas next level ugh. Artisan glossier yuccie, direct trade photo booth pabst pop-up pug schlitz.



* Hexagon shoreditch beard
* Intelligentsia narwhal austin
* Literally meditation four
* Microdosing hoodie woke

-->

