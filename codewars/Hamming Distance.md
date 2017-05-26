#### Description:

The Hamming Distance is a measure of similarity between two strings of equal length. Complete the function so that it returns the number of positions where the input strings do not match.

Examples (in JavaScript):

```
hamming("I like turtles","I like turkeys")  //returns 3
hamming("Hello World","Hello World")  //returns 0
```

You can assume that the two input strings are of equal length.



#### Solution:

```Haskell
module Hamming where

hamming :: String -> String -> Int
hamming a b = foldl (\acc (x,y) -> if x /= y then acc+1 else acc) 0 (zip a b)
```

#### Better Solution:

```Haskell
module Hamming where

hamming :: String -> String -> Int
hamming a b = length . filter id $ zipWith (/=) a b
```
