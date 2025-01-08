# Genetic Algorithms

## Terminology

- **Chromosome:** A candidate solution to the problem being solved.
  - It's often represented as a string of values (e.g., a binary string).
- **Gene:** A unit of heredity, representing a specific part of the chromosome.
  - It's located at a specific **locus** on the chromosome.
- **Allele:** The specific value of a gene.
  - For example, if a gene represents eye color, its alleles could be "blue," "brown," or "green." In binary chromosomes, alleles are typically 0 or 1.

- **Locus:** The position of a gene on a chromosome.
- **Genotype:** The complete genetic makeup of an individual (the entire chromosome or set of chromosomes).
- **Phenotype:** The observable characteristics of an individual, resulting from the interaction of its genotype with the environment.
  - GAs primarily focus on manipulating the genotype, not directly the phenotype.
- **Haploid:** Organisms with one set of unpaired chromosomes.
- **Diploid:** Organisms with chromosomes arranged in pairs. Most sexually reproducing organisms are diploid.
- **Population:** A set of chromosomes (candidate solutions) in a particular generation of a GA.
- **Fitness:** A measure of how well a chromosome solves the problem.
  - A higher fitness value indicates a better solution.
- **Fitness Function:** A function that assigns a fitness value to each chromosome in the population.
  - It's the objective function that the GA tries to optimize.
  - Should **correlate to the goal**, and **efficent to compute**
- **Selection:** The process of choosing chromosomes allowed to reproduce.
  - Uses **selection operator**
- **Crossover (Recombination):** Combines parts of two parent chromosomes to create offspring, mimicking sexual reproduction.
- **Mutation:** Introduces small, random changes in the offspring's chromosomes.
- **Inversion:** Reverses the order of a sequence of genes within a chromosome.
  - Rarely used in GAs
- **Translocation:** Cuts part of the chromosome and move it to a different location.
  - Rarely used in GAs

## Evolution Theory

- Marcoscope Evolution (Darwinian): Natural selection & Survival of the fittest
- Microscope Evolution (Neo-Darwinism)
  - Genes are **transfer unit** of heredity
  - An individual is a **selection unit**
  - The population is the **envolving unit**

## DNA Structure

- Four nitrogenous bases:
  - Adenine (A)
  - Guanine (G)
  - Cytosine (C)
  - Thymine (T)

- Nitrogenous bases are held together by hydrogen bonds
  - $A=T$
  - $G \equiv C$

- 3 nitrogenous bases code a 1 amino acid
  - The coding is **universal**
  - But GAs do not have universal code

## Computation Appeal

- **Parallelism**: each individual is accessed independently
- **Adaptability**: survival of the fittest to the environment
- **Optimisation**: only optimal ones survive

## Basic GAs

1. **Initialization:**
    *   Define the chromosome representation.
    *   Create an initial population of random chromosomes.
    *   Set genetic operator parameters (crossover rate, mutation rate).
    *   Define the fitness function.

2. **Evaluation:**
    *   Calculate the fitness of each chromosome using the fitness function.

3. **Selection:**
    *   Select chromosomes from the population to be parents based on their fitness.
    *   **Roulette Wheel Selection:** The $i_{\text{th}}$ chromosome will be selected $N_i = \frac{f_i}{\bar f}$ times. (its own fitness score divided by avergae fitness score and then rounded to integer)
    
4. **Crossover:**
    *   Apply the crossover operator to the selected parent pairs, creating offspring.

5. **Mutation:**
    *   Apply the mutation operator to introduce small random changes in the offspring.

6. **Replacement:**
    *   Replace the old population (or a portion of it) with the new offspring, forming the next generation.

7. **Termination:**
    *   Repeat steps 2-6 until a termination criterion is met (e.g., maximum number of generations reached, satisfactory fitness level achieved, or no significant improvement in fitness).

## Schema Theorem

### Concepts

*   **Schema:** A template that describes a subset of chromosomes with similarities at certain positions.
    *   Composed of fixed values and wildcards (\*)

*   **Order of a Schema:** The number of fixed positions (non-wildcards) in the schema.
*   **Defining Length of a Schema:** The distance between the first and last fixed positions.
*   **Schema Theorm:** Highly-fit, short-defining-length and low-order schemas increase exponentially in frequency in successive generations. 

### Computation

- Probability of destroying a schema $H$ due to crossover: $p_c^d(H) = p_c \frac{\delta(H)}{l - 1}$

- Probability of destroying a schema $H$ due to mutation: $p_m^d(H) = p_m \frac{O(H)}{l}$

- Probability of survival: $p_s(H)=1-p_c^d(H)-p_m^d(H)$

- Expected frequency in successive generations: $m(H,t+1) \ge m(H,t) \cdot \frac{f(H,t)}{\bar f(t)} \cdot p_s(H)$

Where:

*   $p_c$: Probability of crossover.
*   $\delta(H)$: Defining length of schema $H$.
*   $l$: Chromosome length.
*   $O(H)$: Order of schema $H$.
*   $p_m$: Probability of mutation.
*   $m(H,t)$ represents the number of chromosomes matching schema $H$ at generation $t$.
*   $f(H,t)$ represents the mean fitness of chromosomes matching schema $H$ at generation $t$.
*   $\bar f(t)$ represents the mean fitness of individuals in the population at generation $t$.

