# Problema: escrever um algoritmo que ache os top K termos em um texto

Dado um texto "a b b c d a b", ache K termos com mais ocorrência. Retorno os termos.
Para o exemplo de texto dado, o resultado seria uma lista ["a", "b"] se K = 2

A ordem de retorno da lista não importa, mas se vc quiser ordenar da que tem maior número ocorrências pra de menor ocorrência, fica como extra

Ao final, explique:

1. Complexidade de tempo
2. Complexidade de espaço

## Solução:
```
def search(text, k):
    text = (text.lower()).split(" ")

    hash_table = {}

    for word in text:
        if word not in hash_table:
            hash_table[word] = 1
        else:
            hash_table[word] = hash_table[word] + 1

    hash_table = sorted(hash_table.items(), key=lambda x:x[1], reverse=True)
    search_k = [x[0] for x in hash_table[:k]]
    return search_k
```
### Complexidade de tempo: O(n)
A complexidade de tempo é equivalente à maior complexidade de tempo executada pelo algoritmo. Nesse caso, é O(nlogn) porque é a complexidade da função sorted().

### Complexidade de espaço: O(n)
A complexidade de espaço também é equivalente à maior complexidade de espaço requerida pelo algoritmo. No caso é O(n) que é tanto a complexidade do espaço usado para o dicionário hash_table, quanto a complexidade esperada pela execução da função sorted().
