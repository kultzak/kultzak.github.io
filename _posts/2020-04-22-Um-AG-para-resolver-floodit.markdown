---
layout: post
title:  "Um algoritmo genético para resolver o jogo flood-it"
date:   2022-10-31 10:00:01 -0300
categories: floodit algoritmo-genetico
tags: [floodit, algoritmo genetico]
lang: pt-br
ref: gen_flood
---


Flood-it é um jogo desenvolvido por **Jan Wolter** [https://unixpapa.com/](https://unixpapa.com/) e consiste em um tabuleiro NxN com quadrados de cores diferentes, o objetivo é preencher o tabuleiro inteiro com uma única cor colorindo a região de inundação com uma cor vizinha e dessa forma fundindo à região de inundação todos os seus quadrados adjacentes da mesma cor. O jogo original nos dá um número limitado de operações de inundação (mudanças de cor) como parâmetro para vencer o jogo.

![floodit](https://raw.githubusercontent.com/kultzak/kultzak.github.io/master/_assets/images/floodit_unpp.webp)

<div class="divider"></div>

O número mínimo de operações de inundação é um problema NP-dificil para o número_de_cores >= 3 tornando o jogo uma boa oportunidade para testar e aferir a eficiência de algoritmos.

Meu primeiro contato com o flood-it foi em um exercício na universidade onde o professor nos deu a restrição de tempo (máximo de um minuto de processamento para apresentar uma resposta) e a linguagem (C). A dica era jogarmos sozinhos e buscarmos intuitivamente a melhor estratégia. Revisitando o projeto, decidi manter essas restrições, melhorar a interface usando ncurses e incluir mais resolvedores baseados em diferentes algoritmos para construir um pequeno benchmark restrita a este problema, na forma de um desafio pessoal.

<div class="divider"></div>

Uma boa estratégia de jogo é sempre tentar alcançar o quadrado mais distante da região inundada. E a solução ótima pode ser obtida usando o algoritmo A* ao custo de sua complexidade exponencial de memória. Naquela época como eu estudava Algoritmos Genéticos, escolhi um deles como minha primeira abordagem.

Um algoritmo genético é uma estratégia baseada na seleção natural para resolver problemas de otimização. Ele otimiza uma **população com indivíduos que representam soluções***, onde as soluções são codificadas como conjuntos de parâmetros chamados genes, especificamente ao considerar o flood-it uma solução é uma seqüência de cores, essas cores podem ser indexadas por número onde cada número representa um gene.

Considerando uma solução representada como uma seqüência de números, podemos criar uma população inicial selecionando aleatoriamente números(cores) na intervalo de números que o tabuleiro oferece. Uma seqüência aleatória de números não nos dá nenhuma garantia de que o tabuleiro será inundado, portanto é necessário verificar a cada novo gene adicionado ao indivíduo se o tabuleiro foi inundado.

Construindo...