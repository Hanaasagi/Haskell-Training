#### Description
In the following 6 digit number:

```
283910
```

91 is the greatest sequence of 2 digits.

Complete the solution so that it returns the largest five digit number found within the number given.. The number will be passed in as a string of only digits. It should return a five digit integer. The number passed may be as large as 1000 digits.

Adapted from ProjectEuler.net

#### Solution

```Haskell
module LargestDigits where

digit5 :: String -> Int
digit5 xs
  | length xs > 5 = max (read (take 5 xs) :: Int) (digit5 (drop 1 xs))
  | otherwise = read xs :: Int
```
