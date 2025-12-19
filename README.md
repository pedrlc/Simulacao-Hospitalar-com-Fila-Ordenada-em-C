##  Sobre o projeto

Este projeto implementa uma **fila de prioridade ordenada** utilizando **listas simplesmente encadeadas** na linguagem **C**.

A estrutura é aplicada em uma **simulação de atendimento hospitalar**, onde cada paciente possui um nível de prioridade. Pacientes com maior valor de prioridade são posicionados mais próximos ao início da fila, garantindo que sejam atendidos antes dos demais.

O objetivo do projeto é demonstrar, de forma prática, o uso de **estruturas de dados**, **alocação dinâmica de memória** e **organização lógica de dados** em um cenário próximo ao mundo real.

---
##  Contexto acadêmico

Projeto desenvolvido como atividade prática da disciplina de **Estruturas de Dados**, com foco em:
- Listas encadeadas
- Ponteiros
- Alocação dinâmica de memória
- Organização de código em arquivos `.h` e `.c`
- Implementação manual de estruturas abstratas de dados

---
##  Estrutura do projeto

```bash
.
├── main.c        # Arquivo principal
├── fila.h        # Interface da fila de prioridade
├── fila.c        # Implementação da fila de prioridade
└── README.md
```
---
## Como compilar e executar:   
Utilize o gcc para compilar o projeto.   

```bash
gcc main.c fila.c -o fila_prioridade
./fila_prioridade
```   

---
##  Implementação da Fila de Prioridade (fila.c)

A lógica principal do projeto está concentrada no arquivo `fila.c`, responsável pela manipulação da fila ordenada por prioridade.

A função de inserção garante que os pacientes sejam posicionados corretamente, mantendo sempre os de maior prioridade mais próximos do início da fila.   


### 🔁 Lógica de inserção ordenada

- Se a fila estiver vazia, o paciente é inserido como primeiro elemento.
- Caso o novo paciente possua prioridade maior que a do primeiro da fila, ele se torna o novo início.
- Caso contrário, a lista é percorrida até encontrar a posição correta, garantindo a ordenação por prioridade.

### Exemplo da função de inserção

```c
void inserir(FilaPrioridade* f, char nome[], int prioridade) {
    No* novo = malloc(sizeof(No));
    strcpy(novo->nome, nome);
    novo->prioridade = prioridade;

    if (f->inicio == NULL || prioridade > f->inicio->prioridade) {
        novo->prox = f->inicio;
        f->inicio = novo;
    } else {
        No* atual = f->inicio;
        while (atual->prox != NULL && atual->prox->prioridade >= prioridade) {
            atual = atual->prox;
        }
        novo->prox = atual->prox;
        atual->prox = novo;
    }
}
``` 

A remoção sempre ocorre no início da fila, garantindo que o paciente com maior prioridade seja atendido primeiro.

----
# Autor   

Pedro Lucas (pedrlc)
Estudante de Engenharia de Software GitHub: https://github.com/pedrlc
Linkedin: www.linkedin.com/in/pedro-lucas-lopes-monteiro