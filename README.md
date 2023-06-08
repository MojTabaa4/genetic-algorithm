# Genetic Algorithm Sudoku Solver

This project implements a genetic algorithm to solve a Sudoku puzzle.

## Overview

The project consists of the following main parts:

1. Defining genes and chromosomes
2. Making the first generation
3. Fitness function
4. Crossover and mutation
5. Implementing the genetic algorithm

## Defining Genes and Chromosomes

A gene represents a row of the Sudoku puzzle and is a permutation of the set {1,2,3,4,5,6,7,8,9}. A chromosome consists
of 9 genes, each gene representing a row of the actual Sudoku puzzle. The `make_gene` function creates a gene, while
the `make_chromosome` function creates a chromosome.

## Making First Generation

The `make_population` function creates a population of a specified size. Each member of the population is a Sudoku
puzzle represented as a chromosome.

## Fitness Function

The fitness function calculates how "fit" a chromosome (puzzle) is based on the following criteria:

- For each column: subtract (number of times a number is seen) - 1 from the fitness for that number
- For each 3x3 square: subtract (number of times a number is seen) - 1 from the fitness for that number

The higher the fitness, the closer the puzzle is to being solved.

## Crossover and Mutation

The crossover function takes two chromosomes as input and makes two new chromosomes by combining them. This crossover
function decides the parent of each gene separately, so the result is independent of the location of the genes.


The mutation function applies a random change to a chromosome with a specified probability. In this case, the mutation
function randomly changes a gene in a chromosome.

```python
def mutation(ch, pm, initial):
    for i in range(9):
        x = rndm.randint(0, 100)
        if x < pm * 100:
            ch[i] = make_gene(initial[i])
    return ch
```

## Implementing The Genetic Algorithm

The genetic algorithm consists of the following steps:

1. Read the puzzle from the input file.
2. Create the initial population.
3. Calculate the fitness of each chromosome.
4. Select the mating pool from the current population.
5. Generate the offspring from the mating pool using crossover and mutation.
6. Replace the current population with the offspring.
7. Repeat steps 3-6 for a specified number of generations.

