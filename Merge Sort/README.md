# Merge Sort

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [Merge Sort](#merge-sort)
	- [Algoritmo Merge Sort](#algoritmo-merge-sort)
	- [Obeservações](#obeservações)
	- [Implementações do Mergesort](#implementações-do-mergesort)

<!-- /code_chunk_output -->

O merge sort, ou ordenação por mistura, é um exemplo de algoritmo de ordenação por comparação do tipo dividir-para-conquistar.

Sua ideia básica consiste em Dividir(o problema em vários subproblemas e resolver esses subproblemas através da recursividade) e Conquistar(após todos os subproblemas terem sido resolvidos ocorre a conquista que é a união das resoluções dos subproblemas). [Wikipédia](https://pt.wikipedia.org/wiki/Merge_sort/)

> ![Merge sort gif](https://upload.wikimedia.org/wikipedia/commons/c/c5/Merge_sort_animation2.gif)



## Algoritmo Merge Sort

A idéia básica do Merge Sort é criar uma sequência ordenada a partir de duas outras também ordenadas. Para isso, o algoritmo Merge Sort divide a sequência original em pares de dados, agrupa estes pares na ordem desejada; depois as agrupa as sequências de pares já ordenados, formando uma nova sequência ordenada de quatro elementos, e assim por diante, até ter toda a sequência ordenada.

- Algoritmo:

	Os três passos úteis dos algoritmos dividir-para-conquistar, que se aplicam ao Merge Sort são:

	1. **Dividir**: Dividir os dados em subsequências pequenas;
Este passo é realizado recursivamente, iniciando com a divisão do vetor de n elementos em duas metades, cada uma das metades é novamente dividida em duas novas metades e assim por diante, até que não seja mais possível a divisão (ou seja, sobrem n vetores com um elemento cada).
	2. **Conquistar**: Classificar as duas metades recursivamente aplicando o merge sort;
	3. **Combinar**: Juntar as duas metades em um único conjunto já classificado.
Para completar a ordenação do vetor original de n elementos, faz-se o merge ou a fusão dos sub-vetores já ordenados.

	A desvantagem do Merge Sort é que requer o dobro de memória, ou seja, precisa de um vetor com as mesmas dimensões do vetor que está sendo classificado.

## Obeservações

> ![Exemplo de execução do merge sort](https://upload.wikimedia.org/wikipedia/commons/thumb/c/cc/Merge-sort-example-300px.gif/220px-Merge-sort-example-300px.gif)
>
> Exemplo de execução do merge sort.

- É possível implementar o merge sort utilizando somente um vetor auxiliar ao longo de toda a execução, tornando assim a complexidade de espaço adicional igual a Θ(n log n).
- É um algoritmo estável na maioria das implementações, em que elas podem ser iterativas ou recursivas.
- É possível também implementar o algoritmo com espaço adicional Θ(1).
- Algoritmo Criado por Von Neumann em 1945.

**Desvantagens**

- Utiliza funções recursivas;
- Gasto extra de memória. O algoritmo cria uma cópia do vetor para cada nível da chamada recursiva, totalizando um uso adicional de memória igual a Θ(n log n).
## Implementações do Mergesort

- **Pseudocódigo**

```
função mergesort (vetor a)
	se (n == 1) retornar a

	vetor l1 = a[0] ... a[n/2]
	vetor l2 = a[n/2 + 1] ... a[n]

	l1 = mergesort(l1)
	l2 = mergesort(l2)

	retornar mesclar(l1, l2)
fim da função mergesort

função mesclar (vetor a, vetor b)
	vetor c

	enquanto (a e b têm elementos)
		if (a[0] > b[0])
			adicionar b[0] ao final de c
			remover b[0] de b
		senão
			adicionar a[0] ao final de c
			remover a[0] de a
		enquanto (a tem elementos)
			adicionar a[0] ao final de c
			remover a[0] de a
		enquanto (b tem elementos)
			adicionar b[0] ao final de c
			remover b[0] de b
		retornar c
fim da função mesclar
```

- **Código em C**

```C
void merge(int vetor[], int comeco, int meio, int fim){
	int com1 = comeco, com2 = meio + 1, comAux = 0, tam = fim - comeco + 1;
	int *vetAux;
	vetAux = (int *)malloc(tam * sizeof(int));

	while (com1 <= meio && com2 <= fim){
		if (vetor[com1] < vetor[com2]){
			vetAux[comAux] = vetor[com1];
			com1++;
		}else{
			vetAux[comAux] = vetor[com2];
			com2++;
		}
		comAux++;
	}

	while (com1 <= meio){ // Caso ainda haja elementos na primeira metade
		vetAux[comAux] = vetor[com1];
		comAux++;
		com1++;
	}

	while (com2 <= fim){ // Caso ainda haja elementos na segunda metade
		vetAux[comAux] = vetor[com2];
		comAux++;
		com2++;
	}

	for (comAux = comeco; comAux <= fim; comAux++){ // Move os elementos de volta para o vetor original
		vetor[comAux] = vetAux[comAux - comeco];
	}

	free(vetAux);
}

void mergeSort(int vetor[], int comeco, int fim){
	if (comeco < fim){
		int meio = (fim + comeco) / 2;

		mergeSort(vetor, comeco, meio);
		mergeSort(vetor, meio + 1, fim);
		merge(vetor, comeco, meio, fim);
	}
}
```

- **Código em C++**

```C
void merge(int *saida, int *auxiliar, int inicio, int meio, int fim){
	int i, j, k;
	i = inicio;
	j = meio + 1;
	k = inicio;
	while (i <= meio && j <= fim){
		if (auxiliar[i] < auxiliar[j]){
			saida[k] = auxiliar[i];
			i++;
		}else{
			saida[k] = auxiliar[j];
			j++;
		}
		k++;
	}

	while (i <= meio){
		saida[k] = auxiliar[i];
		i++;
		k++;
	}

	while (j <= fim){
		saida[k] = auxiliar[j];
		j++;
		k++;
	}
	// Copia os elementos que foram ordenados para o auxiliar
	for (int p = inicio; p <= fim; p++)
		auxiliar[p] = saida[p];
}

void mergeSort(int *saida, int *auxiliar, int inicio, int fim){
	if (inicio < fim){
		int meio = (inicio + fim) / 2;
		mergeSort(saida, auxiliar, inicio, meio);
		mergeSort(saida, auxiliar, meio + 1, fim);
		merge(saida, auxiliar, inicio, meio, fim);
	}
}
```

- **Outra implementação em C++**

```C
void Juntar(int vetor[], int ini, int meio, int fim, int vetAux[]){
	int esq = ini;
	int dir = meio;
	for (int i = ini; i < fim; ++i){
		if ((esq < meio) and ((dir >= fim) or (vetor[esq] < vetor[dir]))){
			vetAux[i] = vetor[esq];
			++esq;
		}else{
			vetAux[i] = vetor[dir];
			++dir;
		}
	}
	// copiando o vetor de volta
	for (int i = ini; i < fim; ++i){
		vetor[i] = vetAux[i];
	}
}

void MergeSort(int vetor[], int inicio, int fim, int vetorAux[]){
	if ((fim - inicio) < 2)
		return;

	int meio = ((inicio + fim) / 2);
	MergeSort(vetor, inicio, meio, vetorAux);
	MergeSort(vetor, meio, fim, vetorAux);
	Juntar(vetor, inicio, meio, fim, vetorAux);
}

void MergeSort(int vetor[], int tamanho){ // função que o usuario realmente chama
	// criando vetor auxiliar
	int vetorAux[tamanho];
	MergeSort(vetor, 0, tamanho, vetorAux);
}
```

- **Código em Python**

```py
def mergeSort(lista):

	if len(lista) > 1:

		meio = len(lista)//2
		#também é valido: meio = int(len(lista)/2)

		listaDaEsquerda = lista[:meio]
		listaDaDireita = lista[meio:]

		mergeSort(listaDaEsquerda)
		mergeSort(listaDaDireita)

		i = 0
		j = 0
		k = 0

		while i < len(listaDaEsquerda) and j < len(listaDaDireita):

			if listaDaEsquerda[i] < listaDaDireita[j]:
				lista[k]=listaDaEsquerda[i]
				i += 1
			else:
				lista[k]=listaDaDireita[j]
				j += 1
			k += 1

		while i < len(listaDaEsquerda):

			lista[k]=listaDaEsquerda[i]
			i += 1
			k += 1

		while j < len(listaDaDireita):
			lista[k]=listaDaDireita[j]
			j += 1
			k += 1
	return lista
```

---
[>> Voltar ao topo >>](#merge-sort)