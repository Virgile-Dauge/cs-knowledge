# Approche initiale

```python
from __future__ import annotations
import sys
import math
import re
from dataclasses import dataclass, field

import itertools
import collections

from typing import List
from typing import Iterable, Any

@dataclass
class State:
    """Class for keeping track of the state of the game."""
    stones: tuple[int] = field(default_factory=tuple)
    pos: int = 0
    spelled: str = ''
    code: str = ' ABCDEFGHIJKLMNOPQRSTUVWXYZ'
  
    def apply_one(self, action:str) -> State:
        if action == '<':
            return State(self.stones, self.pos-1 if self.pos > 0 else 29)  

        if action == '>':
            return State(self.stones, (self.pos+1)%30)  

        if action == '+':
            return State(self.stones[:self.pos]
                         +tuple([(self.stones[self.pos]+1)%27])
                         +self.stones[self.pos+1:],
                         self.pos)
        if action == '-':
            return State(self.stones[:self.pos]
                         +tuple([(self.stones[self.pos]-1) if self.stones[self.pos] > 0 else 26])
                         +self.stones[self.pos+1:],
                         self.pos)

        if action == '.':
            return State(self.stones, self.pos,
                         self.spelled + self.code[self.stones[self.pos]])
        return self

    def apply(self, actions:str) -> State:
        state = self
        for a in actions:
            state = state.apply_one(a)
        return state

    def inc_or_dec(self, target:int, i: int) -> str:
        value = self.stones[i]
        if target==value:
            return '.'
        elif target>value:
            inc = target-value
            dec = value+27-target

        else:
            inc = 27-value+target
            dec = value-target

        if inc <= dec:
            return '+'*inc + '.'
        else:
            return '-'*dec + '.'

    def left_or_right(self, i:int) -> str:
        target = i
        value = self.pos  

        if target==value:
            return ''

        elif target>value:
            inc = target-value
            dec = value+29-target+1

        else:
            inc = 29-value+target
            dec = value-target  

        if inc <= dec:
            return '>'*inc
        else:
            return '<'*dec 

    def closest(self, target: int) -> str:
        #print('Cible :', target, '=', self.code[target], file=sys.stderr, flush=True)
        #print([str(i)+' H '+self.left_or_right(i) +' V '+ self.inc_or_dec(target, i) for i, value in enumerate(self.stones)], file=sys.stderr, flush=True)
        sol = [self.left_or_right(i) + self.inc_or_dec(target, i) for i, value in enumerate(self.stones)]
        #print('Possibilities :', file=sys.stderr, flush=True)
        #print([self.left_or_right(i) for i, value in enumerate(self.stones)], file=sys.stderr, flush=True)
        #print(len(sol), sol, file=sys.stderr, flush=True)
        return sorted(sol, key=len)[0]

    def __str__(self) -> str:
        return 'State ' + ''.join([self.code[i] for i in self.stones]) + '\n' + str(self.stones)

  
magic_phrase = input()
n=4
s = set()
dup = {}
print('+>-[<.>-]')
l = [magic_phrase[i:i+n] for n in reversed(range(2, len(magic_phrase)//2)) for i in range(0, len(magic_phrase), n) ]
#print(l, file=sys.stderr, flush=True)
#windows = [set([magic_phrase[i:i+n] for i in range(len(magic_phrase))]) for n in range(2, len(magic_phrase)//2)]
#print(dup, file=sys.stderr, flush=True)

state = State(tuple([0]*30), code=' ABCDEFGHIJKLMNOPQRSTUVWXYZ') 

to_do = [state.code.index(c) for c in magic_phrase]
print(magic_phrase, file=sys.stderr, flush=True)
print(to_do, file=sys.stderr, flush=True)

res = []
for t in to_do:
    greedy_pick = state.closest(t)
    res += [(state.code[t], greedy_pick)]
    state = state.apply(greedy_pick)
    #print(res[-1], file=sys.stderr, flush=True)
    #print(state, file=sys.stderr, flush=True) 

#print(''.join([s for c, s in res]))
```



# Approche boucles

Pour les CodinGamers experts, nous avons ajouté les **boucles** ! Vous pouvez passer cette partie tant que vous n'avez pas vraiment essayé le reste.  
  
Ces instructions supplémentaires sont également disponibles :

-   **\[** : Si la rune courante est un espace, toutes les instructions jusqu'au **\]** correspondant sont ignorées, sinon l'exécution continue normalement.
-   **\]** : Si la rune courante est un espace, l'exécution continue normalement, sinon les instructions à partir du **\[** précédent correspondant sont exécutées.

Les boucles offrent la possibilité d'exécuter plus d'instructions tout en produisant une solution plus courte.  
  
Par exemple, **AAAAAAAAAAAAAAAAAAAAAAAAAA** (A x26) a pour solution **+..........................** et aussi **+>-[<.>-]** 

## Qu'en faire ?

1) Reset vertical : **[-]** ou **[+]**, va incrémenter ou décrémenter la valeur jusqu'à arriver à l'espace.
2) Déplacement horizontal jusqu'au prochain espace **[<]** ou **[>]**.
3) Répéter une où plusieurs lettres comme le A de l'exemple **+>-[<.>-]**. Ici, une case sert de compteur, et les autres stockent le mot à répéter.
**+>++>-[<<.>.>-]** va répéter 26 fois AB

```python
from __future__ import annotations
import sys

from dataclasses import dataclass, field
from typing import List


@dataclass
class BrainStonesGame:
    stones: List[int] = field(default_factory=list)
    index : int = 0
    code: str = ' ABCDEFGHIJKLMNOPQRSTUVWXYZ'

    def setup_letter(self, letter: str) -> str:
        """ Renvoie la séquence de commandes nécessaires pour atteindre la lettre"""
        target = self.code.index(letter)
        i = self.index # if not index is None else self.index

        value = self.stones[i]
        self.stones[i]=target

        if target==value:
            return ''
        if target > value:
			inc = target-value
            dec = value+len(self.code)-target
        else:
            inc = len(self.code)-value+target
            dec = value-target

        print(letter, '+'*inc if inc <= dec else '-'*dec,file=sys.stderr)
        return '+'*inc if inc <= dec else '-'*dec

    def setup_word_repetition(self, word:str, n:int) -> str:
        #r = '[-]>'
        r=''
        for letter in word:
            r+=self.setup_letter(letter)+'>'
            self.index+=1
        r+=self.setup_letter(self.code[n])
        r+='['+'<'*len(word)+'.>'*len(word)+'-]'
        #r+='[<<[<]>[.>]>-]'
        self.index += len(word)
        return r

  

print(input(),file=sys.stderr)
bsg = BrainStonesGame([0]*30)
print(bsg.setup_word_repetition('ABCDEFGHIJKLMNOPQRSTUVWXYZA', 11))
```

```python
' ABCDEFGHIJKLMNOPQRSTUVWXYZ'.index(' ')
```

```python
5 % 2
```

```python
5 // 2
```