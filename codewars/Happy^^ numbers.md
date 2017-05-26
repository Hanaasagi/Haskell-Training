#### Description:

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers, while those that do not end in 1 are unhappy numbers (or sad numbers) (Wikipedia).

For example number 7 is happy because after a number of steps the computed sequence ends up with a 1: `[7,49,97,130,10,1]`

while 3 is not, and would give us an infinite sequence.

```
[3,9,81,65,61,37,58,89,145,42,20,4,16,37,58,89,145,42,20,4,16,37 ...
```

Write a function that takes n as parameter and return true if and only if n is an happy number.

Happy coding!

#### Solution:

```Haskell
module IsHappy where


digit :: Integer -> [Integer]
digit 0 = []
digit n = q : digit r
  where (r, q) = (n `quotRem` 10)


happyNum :: Integer -> [Integer] -> Bool
happyNum 1 ls = True
happyNum x ls = if nx `elem` ls then False else happyNum nx nls
  where
    nls = x:ls
    nx = sum . map (^2) . digit $ x

isHappy :: Integer -> Bool
isHappy x = happyNum x []
```

#### Better Solution:  

```Haskell
module IsHappy where

import Data.Char (digitToInt)

isHappy :: Int -> Bool
isHappy 1 = True
isHappy 4 = False
isHappy x = isHappy $ sum $ map (^2) $ map digitToInt $ show x
```
