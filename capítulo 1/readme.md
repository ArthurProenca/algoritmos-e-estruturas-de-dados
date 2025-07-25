# Medida de tempo de execução de um programa

Podemos medir o tempo de execução de um programa de duas formas:

<ol>
    <li> Um algoritmo particular</li>
	<li> Uma classe de algoritmos</li>
</ol>

Para o caso 1, analisaremos o número de vezes que cada parte de um algoritmo será executada seguida da quantidade de memória necessária.

Para o caso 2, partimos de uma gama de algoritmos do caso 1 e escolheremos qual melhor resolve um determinado problema.

> Se é possível, no passo 2, escolher um algoritmo de **menor custo possível** (menor número de execuções e memória), conseguiremos portanto a **medida da dificuldade** do algoritmo em resolver o problema.

Não se pode usar o tempo de execução de um computador real para determinar a qualidade de um algoritmo. Um exemplo de isso ser uma má prática se encontra na ampla gama de possibilidades de computadores com diferentes processadores, compiladores e até mesmo na qualidade de manutenção.

> Portanto, para medir a complexidade de um algoritmo podemos idealizar uma função _f_ tal que _f(n)_ é a medida do <u>tempo necessário</u> para o algoritmo resolver um problema de tamanho n. f(n) pode ser escrita também para medir a <u>complexidade de espaço</u> de um algoritmo se a utilizarmos para saber a quantidade de memória necessária para resolver um problema de tamanho n.

Imagine um programa que recebe uma lista de inteiros e pega o maior valor possível da lista. Ele pode ser implementado em f(n) mas também pode ser implementado em f(n - 1) em complexidade de tempo para garantir o estado **ótimo**. Para se tornar um f(n - 1), basta sempre iniciarmos o maior valor com o primeiro item da lista. Fazer isso é possível e não viola a integridade do programa. Vejamos o exemplo:

```java
public int valorMaximo(int[] valores) {
	int valorMaximo = valores[0];
	for(int i = 1; i < valores.length; i++) {
		if(valores[i] > valorMaximo) {
			valorMaximo = valores[i];
		}
	}
	return valorMaximo;
}
```

A função valorMaximo poderia ser escrita com o contador i do for iniciado em 0. Porém, não seria uma solução ótima pois ela pode ser ainda menor se sempre começarmos o valorMaximo com o primeiro item do array de valores. Portanto, serão necessárias n - 1 iterações no mínimo (sendo n o tamanho do array de valores).

## Comportamento assintótico de funções

Se considerarmos sempre problemas pequenos (ou seja, de n pequeno), nunca nos preocuparemos com a complexidade do algoritmo. Porém, quando lidamos com problemas maiores (algo próximo do infinito), podemos estimar o comportamento dessa função de uma forma assintótica.

> Se estamos estimando de forma assintótica uma função, estamos trabalhando com a notação O.

Podemos analisar segmentos com a notação. Por exemplo, se trabalharmos com o processamento de uma matriz. Para processar toda uma matriz quadrada, precisaremos percorrer todas as linhas e todas as colunas n\*n vezes. Na notação big-O (O), descreveremos algo como O(f(n)\*f(n)), que pode ser resumido em O(f(n²)) ou simplesmente O(n²).

### Tabela de complexidade de algoritmo

Abaixo, uma tabela simulando entradas de n para valores de 1, 10, 100, 1000 e 1000000. Perceba que a melhor complexidade do algoritmo varia com as entradas, tendo como a "melhor complexidade média" a O(log n).

| Complexidade | Nome                 | n = 1 | n = 10    | n = 100    | n = 1.000     | n = 1.000.000     |
| ------------ | -------------------- | ----- | --------- | ---------- | ------------- | ----------------- |
| O(1)         | Constante            | 1     | 1         | 1          | 1             | 1                 |
| O(log n)     | Logarítmica (base 2) | 0     | ~3.32     | ~6.64      | ~9.97         | ~19.93            |
| O(n)         | Linear               | 1     | 10        | 100        | 1.000         | 1.000.000         |
| O(n log n)   | Linearítmica         | 0     | ~33       | ~664       | ~9.970        | ~19.930.000       |
| O(n²)        | Quadrática           | 1     | 100       | 10.000     | 1.000.000     | 1.000.000.000.000 |
| O(n³)        | Cúbica               | 1     | 1.000     | 1.000.000  | 1.000.000.000 | 1e+18             |
| O(2^n)       | Exponencial          | 2     | 1.024     | ~1.27e+30  | ~1.07e+301    | Inviável          |
| O(n!)        | Fatorial             | 1     | 3.628.800 | ~9.33e+157 | ~4.02e+2567   | Inviável          |


> Estimar exatamente a complexidade de um algoritmo dependerá de uma série de fatores. Portanto, é comum que o processamento adicional para tornar um algoritmo O(n) em O(log n) torne o tempo de espera maior à depender das circunstâncias. Sempre escolha o mais adequado para cada problema.

