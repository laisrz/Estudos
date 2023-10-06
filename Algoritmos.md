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

  ### Big O notation

  Big O notation refere-se ao número de operações que um determinado algoritmo terá que fazer no pior cenário possível até solucionar o problema.
  No caso da busca binária, O(log n). 
  Isso significa que em um conjunto de tamanho (n), o número de operações necessárias no pior caso possível para encontrar a solução é de log n.
  Quanto maior a base de dados, então, melhor a performance da busca binária em relaçãoo à busca simples. 
  A busca simples tem um Big O(n), o que significa que o número de operações, no pior cenário, equivale ao tamanho da base de dados (n).
  * Busca binária tem um Big O(log n)















  
