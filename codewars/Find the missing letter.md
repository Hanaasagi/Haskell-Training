#### Description:
Find the missing letter

Write a method that takes an array of consecutive (increasing) letters as input and that returns the missing letter in the array.

You will always get an valid array. And it will be always exactly one letter be missing. The length of the array will always be at least 2.
The array will always contain letters in only one case.

Example:

```
['a','b','c','d','f'] -> 'e'
['O','Q','R','S'] -> 'P'
```

Have fun coding it and please don't forget to vote and rank this kata! :-)

I have also created other katas. Take a look if you enjoyed this kata!



#### Solution:  

*Maybe it's ugly :p*  

```Haskell
module Kata where
import Data.Char (ord, chr)
findMissingLetter' :: [Char] -> Char -> Char
findMissingLetter' [] s = s
findMissingLetter' (c:cs) s
  | c /= s = s
  | otherwise = findMissingLetter' cs (chr $ ord s + 1)

findMissingLetter :: [Char] -> Char
findMissingLetter cs = findMissingLetter' cs (cs !! 0)
```

#### Better Solution:

```Haskell
module Kata where

import Data.List
import Data.Char

findMissingLetter :: [Char] -> Char
findMissingLetter cs = head $ [head cs .. last cs] \\ cs

```
or  

```Haskell
module Kata where
import Data.Char(ord,chr)

findMissingLetter :: [Char] -> Char
findMissingLetter [x] = chr $ ord x +1
findMissingLetter (x:xs@(y:_))
  | ord x == ord y -1 = findMissingLetter xs
  | otherwise = chr $ ord x +1
```
