# Algoritmos
* Bibliografia: BARGHAVA, Aditya. Grokking Algorithms. Edição digital.

## Binary search

  Algoritmos de busca binária consistem em uma série de instruções para pesquisa de um item em um conjunto de itens a partir da divisão do conjunto de itens em subconjuntos.
  O objetivo é dividir o conjunto de itens pela metade e descartar metade desses itens até achar o item pesquisado ou descartar todos os dados e concluir que o item não faz parte do conjunto.

  Só é possível fazer uma busca binária em uma lista ordenada.

  Por exemplo, ao pesquisar uma palavra em um dicionário. O primeiro passo seria abrir o dicionário ao meio e verificar se a palavra se encontra naquela página.
  Caso contrário, verificar se a palavra pesquisada se encontra na metada anterior ou posterior do dicionário.
  Assim, descartamos metade do dicionário e continuamos a pesquisa com a metade restante.
  Considerando apenas essa metade restante, devemos abrir de novo ao meio e verificar se a palavra se encontra ali.
  Caso contrário, procederemos conforme os passos anteriores, sempre descartando metade dos itens, até achar a palavra pesquisada.

  Exemplo de algoritmo em Python:

  ```
    # low and high keep track of which part of the list you'll search in.
    low = 0
    high = len(list) - 1

    # While you haven't narrowed it down to one element
    while low <= high:
      # check the middle element
      mid = (low + high) // 2
      guess = list[mid]
      # Found the item.
      if guess == item:
        return mid
      # The guess was too high.
      if guess > item:
        high = mid - 1
      # The guess was too low.
      else:
        low = mid + 1

    # Item doesn't exist
    return None
```
### Binary Search Tree

Uma árvore de busca binária (BST) é uma árvore em que todos os nós seguem as seguintes propriedades:

  * A raiz tem o maior valor na subárvore esquerda;
  * A raiz tem o menor valor na subárvore direita;
  * Cada subárvore esquerda é formada por nós com valores menores que a raiz;
  * Cada subárvore direita é formada por nós com valores maiores que a raiz.

![BST](img/bst.png)

Vamos encontrar a maior chave na árvore que é menor que um determinado número `n`.

Primeiro, vamos pensar na BST. A maior chave na árvore que é menor que `n` é o nó mais à direita na subárvore esquerda de `n`.

```python
func FindLargestSmallerKey(rootNode *Node, num int) int {
  largestSmaller := -1

  node := rootNode

  for node != nil {
      if node.key < num {
          largestSmaller = node.key
          node = node.right
      } else {
          node = node.left
      }
  }

  return largestSmaller
}
```

* Toda vez que vemos que a chave é menor que nosso n, começamos a encontrar nosso maior menor na subárvore direita;
* Toda vez que vemos que a chave é maior que nosso n, começamos a encontrar nosso maior menor na subárvore esquerda;
* Seguindo esse raciocínio, encontraremos a maior chave menor no nó mais à direita da subárvore esquerda sem compará-la com nenhuma chave anterior.

  ### Big O notation

  Big O notation refere-se ao número de operações que um determinado algoritmo terá que fazer no pior cenário possível até solucionar o problema.
  No caso da busca binária, O(log n).
  Isso significa que em um conjunto de tamanho (n), o número de operações necessárias no pior caso possível para encontrar a solução é de log n.
  Quanto maior a base de dados, então, melhor a performance da busca binária em relaçãoo à busca simples.
  A busca simples tem um Big O(n), o que significa que o número de operações, no pior cenário, equivale ao tamanho da base de dados (n).
  * Busca binária tem um Big O(log n)

## Arrays and Lists

Arrays e Listas são formas de armazenar dados na memória.
Na array, os dados são armazenados de forma contígua. A vantagem é que isso permite que os dados sejam acessados de forma aletória, ou seja, permite uma leitura rápida dos dados. A desvantagem é que a inserção e deleção de dados na array é mais lenta que nas listas, porque em último caso é preciso mover a array inteira para outro lugar na memória. Como na array os dados são armazenados de forma contígua, ao inserir um novo dado, se não houver espaço na memória no endereço contíguo imediato ao fim da array, toda ela deverá ser movida para um novo endereço.

Já nas listas (linked lists), os dados não são armazenados de forma contígua, mas sim de acordo com o espaço livre de memória, e isso é feito ao armazenar junto com o dado o endereço do próximo item da lista. Isso permite que as inserções e deleções sejam rápidas, Big O(1), já que é só inserir o novo dado ao final da lista ou fazer com que um item aponte para outro endereço de memória para deletar itens. Mas a desvantagem é que a velocidade de leitura é menor do que nas arrays, porque as listas não permitem acesso aleatório. Assim, a velocidade de leitura tem Big O(n).

  ```
    Velocidades de execução:
              Arrays    Listas
    Leitura    O(1)      O(n)
    Inserção   O(n)      O(1)
    Deleção    O(n)      O(1)
```

A partir de arrays e linked lists, é possível construir estruturas de dados mais complexas que permitem manipular um grande volume de dados com maior otimização em leitura, inserção e deleção.

Por exemplo, é possível utilizar um modelo híbrido de array e listas, em que em uma array de 26 elementos (A-Z), cada elemento aponta para uma linked list. Dessa forma, a inserção e deleção terá a mesma velocidade das listas, O(1), mas a leitura será mais rápida do que em uma linked list convencional.

## Selection sort

* Para aplicar uma busca binária em uma estrutura de dados, esta precisa estar ordenada. A selection sort é uma das formas de ordenação de dados.
* Na selection sort, o conjunto de dados é varrido de forma a achar o valor mais baixo (ou mais alto) e adicioná-lo a outro conjunto de dados, ou colocá-lo no início do conjunto. Feito continuamente até o final do conjunto, ao final ele estará ordenado.
* Big 0(n^2): a cada varrição, checa-se n, depois n-1, n-2, n-3... elementos. Ou seja n + (n-1) + (n-2)...+1 = n * (1/2 * n).
  Como constantes são ignoradas no cálculo do Big O: n^2.

  Exemplo de algoritmo em Python

```
      * Para encontrar o menor valor em uma array:
        def findSmallest(arr):
            # Stores the smallest value
            smallest = arr[0]
            # Stores the index of the smallest value
            smallest_index = 0
            for i in range(1, len(arr)):
                if arr[i] < smallest:
                smallest_index = i
                smallest = arr[i]
            return smallest_index


  * Para ordenar a array:
         def selectionSort(arr):
            newArr = []
            for i in range(len(arr)):
                # Finds the smallest element in the array and adds it to the new array
                smallest = findSmallest(arr)
                newArr.append(arr.pop(smallest))
            return newArr
```

## Recursion

* Recursão é um mecanismo de programação em que uma função chama a si mesma.
* Para que a função não seja executada infinitamente, usa-se um base case.
* Base case: define quando a função deverá retornar
* Recursive case: define os termos em que a função deverá chamar a si mesma.
* Embora seja uma solução mais clara e elegante, ela não necessariamente trará ganhos de desempenho.
* Como todas as chamadas da função ficarão na pilha de chamadas até que se chegue ao base case, usar recursão consome bastante a memória.

### Call Stack

* As funções, quando chamadas, vão para a call stack (pilha de chamadas).
* Quando uma função é chamada dentro de outra função, ela fica "empilhada" em cima da função anterior.
* Conforme as funções retornam, elas são retiradas da call stack.
* Muitas funções em processamento podem ocupar muita memória.

### Algoritmo de binary search com recursão

```
  def search(x, list):
  mid = (len(list) - 1)// 2
  if x == list[mid]:
      return x
  elif x > list[mid]:
      return search(x, list[mid+1 :])
  else:
      return search(x, list[: mid-1])
```



















