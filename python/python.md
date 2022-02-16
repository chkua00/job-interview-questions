# Python Interview Questions

### 1. Student Majors
A university's Office of Admission keeps track of student majors. Each student can have a single major. Below is an example of how their system stores students, majors, and how it manipulates them:
``` python
students = [("Allen Anderson", "Computer Science"),
            ("Edgar Einstein", "Engineering"),
            ("Farrah Finn", "Fine Arts")]
     
def add_new_student(students, name, major):
    students.append((name, major))

def update_student(students, index, name, major):
    students[index] = (name, major)

def find_students_by_name(students, name):
    return [student for student in students if name in student[0]]

def get_all_majors(students):
    return [student[1] for student in students]
```
What can be concluded from the code snippet above?

**Solution:**
``` python
```



### 2. File Owners
Implement a group_by_owners function that:

- Accepts a dictionary containing the file owner name for each file name.
- Returns a dictionary containing a list of file names for each owner name, in any order.

For example, for dictionary {'Input.txt': 'Randy', 'Code.py': 'Stan', 'Output.txt': 'Randy'} the group_by_owners function should return {'Randy': ['Input.txt', 'Output.txt'], 'Stan': ['Code.py']}.

**Solution:**
``` python
"""
10 min

Implement a group_by_owners function that:

    Accepts a dictionary containing the file owner name for each file name.
    Returns a dictionary containing a list of file names for each owner name, in any order.

For example, for dictionary {'Input.txt': 'Randy', 'Code.py': 'Stan', 'Output.txt': 'Randy'}
the group_by_owners function should return {'Randy': ['Input.txt', 'Output.txt'], 'Stan': ['Code.py']}.


    def group_by_owners(files):
        return None

    files = {
        'Input.txt': 'Randy',
        'Code.py': 'Stan',
        'Output.txt': 'Randy'
    }
    print(group_by_owners(files))
"""

from collections import defaultdict


def group_by_owners(files):
    owners = defaultdict(list)
    for file, owner in files.items():
        owners[owner].append(file)
    return owners


files = {
    'Input.txt': 'Randy',
    'Code.py': 'Stan',
    'Output.txt': 'Randy'
}
print(group_by_owners(files))
```



### 3. Ice Cream Machine
Implement the IceCreamMachine's scoops method so that it returns all combinations of one ingredient and one topping. If there are no ingredients or toppings, the method should return an empty list.

For example, IceCreamMachine(["vanilla", "chocolate"], ["chocolate sauce"]).scoops() should return [['vanilla', 'chocolate sauce'], ['chocolate', 'chocolate sauce']].

**Solution:**
``` python
"""
10 min

Implement the IceCreamMachine's scoops method so that it returns all
combinations of one ingredient and one topping. If there are no ingredients or
toppings, the method should return an empty list.

For example,
IceCreamMachine(["vanilla", "chocolate"], ["chocolate sauce"]).scoops()
should return
[['vanilla', 'chocolate sauce'], ['chocolate', 'chocolate sauce']].


    class IceCreamMachine:

        def __init__(self, ingredients, toppings):
            self.ingredients = ingredients
            self.toppings = toppings

        def scoops(self):
            pass

    machine = IceCreamMachine(["vanilla", "chocolate"], ["chocolate sauce"])
    print(machine.scoops()) #should print[['vanilla', 'chocolate sauce'], ['chocolate', 'chocolate sauce']]
"""

from itertools import product


class IceCreamMachine:

    def __init__(self, ingredients, toppings):
        self.ingredients = ingredients
        self.toppings = toppings

    def scoops(self):
        return [list(p) for p in product(self.ingredients, self.toppings)]


if __name__ == "__main__":
    machine = IceCreamMachine(["vanilla", "chocolate"], ["chocolate sauce"])
    print(machine.scoops()) #should print[['vanilla', 'chocolate sauce'], ['chocolate', 'chocolate sauce']]
```



### 4. Merge Names
Implement the unique_names method. When passed two lists of names, it will return a list containing the names that appear in either or both lists. The returned list should have no duplicates.

For example, calling unique_names(['Ava', 'Emma', 'Olivia'], ['Olivia', 'Sophia', 'Emma']) should return a list containing Ava, Emma, Olivia, and Sophia in any order.

**Solution:**
``` python
"""
10 min

Implement the unique_names method. When passed two arrays of names, it will
return an array containing the names that appear in either or both arrays.
The returned array should have no duplicates.

For example, calling unique_names(['Ava', 'Emma', 'Olivia'], ['Olivia', 'Sophia', 'Emma'])
should return an array containing Ava, Emma, Olivia, and Sophia in any order.


    def unique_names(names1, names2):
        return None

    names1 = ["Ava", "Emma", "Olivia"]
    names2 = ["Olivia", "Sophia", "Emma"]
    print(unique_names(names1, names2)) # should print Ava, Emma, Olivia, Sophia
"""

from itertools import chain


def unique_names(names1, names2):
    return list(set(chain(names1, names2)))


names1 = ["Ava", "Emma", "Olivia"]
names2 = ["Olivia", "Sophia", "Emma"]
print(unique_names(names1, names2))     # should print Ava, Emma, Olivia, Sophia
```



### 5. Quadratic Equation
Implement the function find_roots to find the roots of the quadratic equation: ax2 + bx + c = 0. The function should return a tuple containing roots in any order. If the equation has only one solution, the function should return that solution as both elements of the tuple. The equation will always have at least one solution.

The roots of the quadratic equation can be found with the following formula: A quadratic equation.

For example, find_roots(2, 10, 8) should return (-1, -4) or (-4, -1) as the roots of the equation 2x2 + 10x + 8 = 0 are -1 and -4.

**Solution:**
``` python
```



### 6. Binary Search Tree
Binary search tree (BST) is a binary tree where the value of each node is larger or equal to the values in all the nodes in that node's left subtree and is smaller than the values in all the nodes in that node's right subtree.

Write a function that, efficiently with respect to time used, checks if a given binary search tree contains a given value.

For example, for the following tree:

- n1 (Value: 1, Left: null, Right: null)
- n2 (Value: 2, Left: n1, Right: n3)
- n3 (Value: 3, Left: null, Right: null)

Call to contains(n2, 3) should return True since a tree with root at n2 contains number 3.

**Solution:**
``` python
"""
15 min


Binary search tree (BST) is a binary tree where the value of each node is larger
or equal to the values in all the nodes in that node's left subtree and is
smaller than the values in all the nodes in that node's right subtree.

Write a function that, efficiently with respect to time used, checks if a given
binary search tree contains a given value.

For example, for the following tree:

    n1 (Value: 1, Left: null, Right: null)
    n2 (Value: 2, Left: n1, Right: n3)
    n3 (Value: 3, Left: null, Right: null)

Call to contains(n2, 3) should return True since a tree with root at n2 contains number 3.


    import collections

    Node = collections.namedtuple('Node', ['left', 'right', 'value'])

    def contains(root, value):
        pass

    n1 = Node(value=1, left=None, right=None)
    n3 = Node(value=3, left=None, right=None)
    n2 = Node(value=2, left=n1, right=n3)

    print(contains(n2, 3))
"""

import collections

Node = collections.namedtuple('Node', ['left', 'right', 'value'])


def contains(root, value):
    if root is None:
        return False
    elif root.value == value:
        return True
    elif root.value >= value:
        return contains(root.left, value)
    else:
        return contains(root.right, value)


n1 = Node(value=1, left=None, right=None)
n3 = Node(value=3, left=None, right=None)
n2 = Node(value=2, left=n1, right=n3)

print(contains(n2, 3))
```



### 7. Song
A playlist is considered a repeating playlist if any of the songs contain a reference to a previous song in the playlist. Otherwise, the playlist will end with the last song which points to None.

Implement a function is_repeating_playlist that, efficiently with respect to time used, returns true if a playlist is repeating or false if it is not.

For example, the following code prints "True" as both songs point to each other.
``` python
first = Song("Hello")
second = Song("Eye of the tiger")
    
first.next_song(second)
second.next_song(first)
    
print(first.is_repeating_playlist())
```

**Solution:**
``` python
"""
15 min

A playlist is considered a repeating playlist if any of the songs contain
a reference to a previous song in the playlist. Otherwise, the playlist will end
with the last song which points to None.

Implement a function is_repeating_playlist that, efficiently with respect to
time used, returns true if a playlist is repeating or false if it is not.

For example, the following code prints "True" as both songs point to each other.

    first = Song("Hello")
    second = Song("Eye of the tiger")

    first.next_song(second);
    second.next_song(first);

    print(first.is_repeating_playlist())




    class Song:
        def __init__(self, name):
            self.name = name
            self.next = None

        def next_song(self, song):
            self.next = song

        def is_repeating_playlist(self):
            return None

    first = Song("Hello")
    second = Song("Eye of the tiger")

    first.next_song(second);
    second.next_song(first);

    print(first.is_repeating_playlist())
"""


class Song:
    def __init__(self, name):
        self.name = name
        self.next = None

    def next_song(self, song):
        self.next = song

    def is_repeating_playlist(self):
        """
        :returns: (bool) True if the playlist is repeating, False if not.
        """
        playlist = {self}
        song = self.next
        while song:
            if song in playlist:
                return True
            else:
                playlist.add(song)
                song = song.next
        return False


first = Song("Hello")
second = Song("Eye of the tiger")

first.next_song(second)
second.next_song(first)

print(first.is_repeating_playlist())
```



### 8. Two Sum
Write a function that, when passed a list and a target sum, returns, efficiently with respect to time used, two distinct zero-based indices of any two of the numbers, whose sum is equal to the target sum. If there are no two numbers, the function should return None.

For example, find_two_sum([3, 1, 5, 7, 5, 9], 10) should return a single tuple containing any of the following pairs of indices:

- 0 and 3 (or 3 and 0) as 3 + 7 = 10
- 1 and 5 (or 5 and 1) as 1 + 9 = 10
- 2 and 4 (or 4 and 2) as 5 + 5 = 10

**Solution:**
``` python
"""
30 min

Write a function that, when passed a list and a target sum, returns, efficiently
with respect to time used, two distinct zero-based indices of any two of the
numbers, whose sum is equal to the target sum. If there are no two numbers,
the function should return None.

For example, find_two_sum([3, 1, 5, 7, 5, 9], 10) should return a single tuple
containing any of the following pairs of indices:

* 0 and 3 (or 3 and 0) as 3 + 7 = 10
* 1 and 5 (or 5 and 1) as 1 + 9 = 10
* 2 and 4 (or 4 and 2) as 5 + 5 = 10


def find_two_sum(numbers, target_sum):
    # :param numbers: (list of ints) The list of numbers.
    # :param target_sum: (int) The required target sum.
    # :returns: (a tuple of 2 ints) The indices of the two elements whose sum is equal to target_sum
    return None

print(find_two_sum([3, 1, 5, 7, 5, 9], 10))
"""


def find_two_sum(numbers, target_sum):
    """
    :param numbers: (list of ints) The list of numbers.
    :param target_sum: (int) The required target sum.
    :returns: (a tuple of 2 ints) The indices of the two elements whose sum is equal to target_sum
    """
    taken = {}
    for i, num in enumerate(numbers):
        diff = target_sum - num
        if diff in taken:
            return i, taken[diff]
        taken[num] = i
    return None


print(find_two_sum([3, 1, 5, 7, 5, 9], 10))
```



### 9. Pipeline
As part of a data processing pipeline, complete the implementation of the pipeline method:

- The method should accept a variable number of functions, and it should return a new function that accepts one parameter arg.
- The returned function should call the first function in the pipeline with the parameter arg, and call the second function with the result of the first function.
- The returned function should continue calling each function in the pipeline in order, following the same pattern, and return the value from the last function.

For example, pipeline(lambda x: x * 3, lambda x: x + 1, lambda x: x / 2) then calling the returned function with 3 should return 5.0.

**Solution:**
``` python
"""
10 min

As part of a data processing pipeline, complete the implementation of
the pipeline method:

* The method should accept a variable number of functions, and it should return
  a new function that accepts one parameter arg.
* The returned function should call the first function in the pipeline with
  the parameter arg, and call the second function with the result of the first function.
* The returned function should continue calling each function in the pipeline
  in order, following the same pattern, and return the value from the last function.

For example, pipeline(lambda x: x * 3, lambda x: x + 1, lambda x: x / 2) then
calling the returned function with 3 should return 5.0.


    def pipeline(*funcs):
        def helper(arg):
            pass
        return helper

    fun = pipeline(lambda x: x * 3, lambda x: x + 1, lambda x: x / 2)
    print(fun(3)) #should print 5.0
"""


def pipeline(*funcs):
    def helper(arg):
        for f in funcs:
            arg = f(arg)
        return arg

    return helper


fun = pipeline(lambda x: x * 3, lambda x: x + 1, lambda x: x / 2)
print(fun(3))  # should print 5.0
```


### 10. League Table
The LeagueTable class tracks the score of each player in a league. After each game, the player records their score with the record_result function. 

The player's rank in the league is calculated using the following logic:

- The player with the highest score is ranked first (rank 1). The player with the lowest score is ranked last.
- If two players are tied on score, then the player who has played the fewest games is ranked higher.
- If two players are tied on score and number of games played, then the player who was first in the list of players is ranked higher.

Implement the player_rank function that returns the player at the given rank.

For example:
``` python
table = LeagueTable(['Mike', 'Chris', 'Arnold'])
table.record_result('Mike', 2)
table.record_result('Mike', 3)
table.record_result('Arnold', 5)
table.record_result('Chris', 5)
print(table.player_rank(1))
```
All players have the same score. However, Arnold and Chris have played fewer games than Mike, and as Chris is before Arnold in the list of players, he is ranked first. Therefore, the code above should display "Chris".

**Solution:**
``` python
"""
20 min


The LeagueTable class tracks the score of each player in a league. After each
game, the player records their score with the record_result function.

The player's rank in the league is calculated using the following logic:

* The player with the highest score is ranked first (rank 1). The player with the lowest score is ranked last.
* If two players are tied on score, then the player who has played the fewest games is ranked higher.
* If two players are tied on score and number of games played,
  then the player who was first in the list of players is ranked higher.

Implement the player_rank function that returns the player at the given rank.

For example:

table = LeagueTable(['Mike', 'Chris', 'Arnold'])
table.record_result('Mike', 2)
table.record_result('Mike', 3)
table.record_result('Arnold', 5)
table.record_result('Chris', 5)
print(table.player_rank(1))

All players have the same score. However, Arnold and Chris have played fewer
games than Mike, and as Chris is before Arnold in the list of players, he is
ranked first. Therefore, the code above should display "Chris".


    from collections import Counter
    from collections import OrderedDict

    class LeagueTable:
        def __init__(self, players):
            self.standings = OrderedDict([(player, Counter()) for player in players])

        def record_result(self, player, score):
            self.standings[player]['games_played'] += 1
            self.standings[player]['score'] += score

        def player_rank(self, rank):
            return None

    table = LeagueTable(['Mike', 'Chris', 'Arnold'])
    table.record_result('Mike', 2)
    table.record_result('Mike', 3)
    table.record_result('Arnold', 5)
    table.record_result('Chris', 5)
    print(table.player_rank(1))
"""

from collections import Counter
from collections import OrderedDict


class LeagueTable:
    def __init__(self, players):
        self.standings = OrderedDict([(player, Counter()) for player in players])

    def record_result(self, player, score):
        self.standings[player]['games_played'] += 1
        self.standings[player]['score'] += score

    def player_rank(self, rank):
        ranks = [(-counter['score'], counter['games_played'], i, name)
                 for i, (name, counter) in enumerate(self.standings.items())]

        return sorted(ranks)[rank-1][3]


table = LeagueTable(['Mike', 'Chris', 'Arnold'])
table.record_result('Mike', 2)
table.record_result('Mike', 3)
table.record_result('Arnold', 5)
table.record_result('Chris', 5)
print(table.player_rank(1))
```


### 11. Sorted Search
Implement function count_numbers that accepts a sorted list of unique integers and, efficiently with respect to time used, counts the number of list elements that are less than the parameter less_than.

For example, count_numbers([1, 3, 5, 7], 4) should return 2 because there are two list elements less than 4.

**Solution:**
``` python
"""
Implement function count_numbers that accepts a sorted list of unique integers and, 
efficiently with respect to time used, counts the number of list elements 
that are less than the parameter less_than.

For example, count_numbers([1, 3, 5, 7], 4) should return 2 
because there are two list elements less than 4.
"""

from bisect import bisect_left


def count_numbers(sorted_list, less_than):
    return bisect_left(sorted_list, less_than)


if __name__ == "__main__":
    sorted_list = [1, 3, 4, 5, 7]
    print(count_numbers(sorted_list, 4)) # should print 2
```


### 12. Train Composition
A TrainComposition is built by attaching and detaching wagons from the left and the right sides, efficiently with respect to time used.

For example, if we start by attaching wagon 7 from the left followed by attaching wagon 13, again from the left, we get a composition of two wagons (13 and 7 from left to right). Now the first wagon that can be detached from the right is 7 and the first that can be detached from the left is 13.

Implement a TrainComposition that models this problem.

**Solution:**
``` python
```


### 13. Route Planner
As a part of the route planner, the route_exists method is used as a quick filter if the destination is reachable, before using more computationally intensive procedures for finding the optimal route.

The roads on the map are rasterized and produce a matrix of boolean values - True if the road is present or False if it is not. The roads in the matrix are connected only if the road is immediately left, right, below or above it.

Finish the route_exists method so that it returns True if the destination is reachable or False if it is not. The from_row and from_column parameters are the starting row and column in the map_matrix. The to_row and to_column are the destination row and column in the map_matrix. The map_matrix parameter is the above mentioned matrix produced from the map.

For example, for the given rasterized map, the code below should return True since the destination is reachable:

``` python
map_matrix = [
    [True, False, False],
    [True, True, False],
    [False, True, True]
];

route_exists(0, 0, 2, 2, map_matrix)
```

**Solution:**
``` python
```

