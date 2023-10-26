
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
