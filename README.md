# Sequencial

## Compilar

```bash
g++ -O2 -std=c++17 -o mult mult.cpp
```

## Executar

```bash
./mult <tamanhoDaMatriz>
```

---

# Paralelo MPI - Divisao e Conquista

A versao MPI usa uma arvore binaria completa de processos. Cada processo recebe um
bloco de linhas da matriz A, decide se divide o bloco entre dois filhos ou se
conquista o problema calculando localmente, e devolve o bloco correspondente de C
para o pai.

O programa aceita quantidades no formato de arvore binaria completa. Para seguir
os testes pedidos no enunciado, use principalmente:

```text
1, 3, 7, 15, 31
```

## Compilar

```bash
mpic++ -O2 -std=c++17 -o mult_mpi mult_mpi.cpp
```

## Executar localmente

```bash
mpirun -np <numeroDeProcessos> ./mult_mpi <tamanhoDaMatriz>
```

Exemplos:

```bash
mpirun -np 7 ./mult_mpi 2048
```

## Executar no LAD/Atlantica

```bash
srun -N 2 -n <numeroDeProcessos> ./mult_mpi <tamanhoDaMatriz>
```

Onde:

- `-N`: numero de nodos reservados.
- `-n`: numero total de processos MPI.
