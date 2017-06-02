#### Description:

Write a function that returns all of the sublists of a list or Array.

Your function should be pure; it cannot modify its input.

Example:

```
power [1,2,3]
-- => [[], [1], [2], [1, 2], [3], [1, 3], [2, 3], [1, 2, 3]]
```

For more details regarding this, see the power set entry in wikipedia.


#### Solution:

```Haskell
module Power where

power :: [a] -> [[a]]
power [] = [[]]
power (x:xs) = [x:sub | sub <- remain] ++ remain
  where remain = power xs
```
