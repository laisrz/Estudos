Desafio Change (Python) do Exercism

```python
def find_fewest_coins(coins, target):
    if target < 0:
        raise ValueError("target can't be negative")
    if target == 0:
        return []
    if target < coins[0]:
        raise ValueError("can't make target with given coins")
        

    def coins_to_be_given(coins, target):
        ''' calculate number of coins by dividing the target by the first element in the list of coins given. Use recursion to go through the list of coins by reducing the list one element at time. Populates a new list (coins_used) with the coins used to get to the target'''
    
        if target == 0 or (len(coins) == 1 and target % coins[0] != 0):
            return

        number_of_coins = target // coins[0]
        
        if number_of_coins > 0:
            coins_used.extend([coins[0] for number in range(number_of_coins)])
            
        return coins_to_be_given(coins[1:], target - (coins[0] * number_of_coins))
        
    min_coins_used = list()
    
    for num in range(len(coins), 0, -1):
        '''for loop used to also run the coins_to_be_given function with a the list of coins limited to lower numbers, as this may result in less coins needed'''
        coins_used = []
        new_coins = coins[:num]
        coins_to_be_given(new_coins[::-1], target)
        if len(min_coins_used) == 0 or len(coins_used) < len(min_coins_used):
            min_coins_used = coins_used.copy()


    
    if len(min_coins_used) == 0:
        raise ValueError("can't make target with given coins")


    return min_coins_used[::-1]
```
