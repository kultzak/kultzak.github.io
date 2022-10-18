---
layout: post
title:  "A genetic algorithm to solve the game flood-it"
date:   2020-04-22 10:00:01 -0300
categories: floodit genetic-algorithm
tags: [floodit, genetic algorithm]
lang: en
ref: gen_flood
---

Flood-it is a game developed by **Jan Wolter** [https://unixpapa.com/](https://unixpapa.com/)  and consists of an NxN board with squares of different colors, the objective is to fill the whole board with a single color by coloring the flooding region with a neighbor color and that way merging to the flooding region all its adjacent squares of the same color. The original game gives us a limited number of flood operations(color changes) as a parameter to beat the game.

![floodit](https://raw.githubusercontent.com/kultzak/kultzak.github.io/master/_assets/images/floodit_unpp.webp)

<div class="divider"></div>

The minimum number of flooding operations is NP-hard for number_of_colors >= 3 making the game a good opportunity to test algorithms
and benchmark its efficiency.

My first contact with flood-it was in a college exercise, the professor gave us the constraint of time (maximum of one minute of processing to present an answer) and the language (C). The tip was to play by ourselves and search intuitively for the best strategy we could find. Revisiting the project, I decided to keep those constraints, improve the interface using ncurses, and include more solvers based on different algorithms to construct a small benchmark restricted to this problem, more as a personal challenge.

<div class="divider"></div>

A good game strategy is always trying to reach the farthest square from the flooding region. And the optimal solution can be obtained using A* algorithm at the cost of its exponential memory complexity. Back then I was studying Genetic Algorithms, so I use one as my first approach.

Continue.....
