#### Description:
Wikipedia article on Pascal's Triangle: http://en.wikipedia.org/wiki/Pascal's_triangle

Write a function that, given a depth (n), returns a single-dimensional array representing Pascal's Triangle to the n-th level.

For example:

```
pascalsTriangle 4 == [1,1,1,1,2,1,1,3,3,1]
```

#### Solution:  

```Haskell
module Codewars.Kata.PascalsTriangle where

pascalsTriangle :: Int -> [Int]
pascalsTriangle n
  | n == 1 = [1]
  | otherwise = last ++ [1] ++ (zipWith (+) temp $ drop 1 temp)++ [1]
    where last = pascalsTriangle (n-1)
          temp = drop (sum [0..n-2]) last
```
