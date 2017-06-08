#### Description:

ROT13 is a simple letter substitution cipher that replaces a letter with the letter 13 letters after it in the alphabet. ROT13 is an example of the Caesar cipher.

Create a function that takes a string and returns the string ciphered with Rot13. If there are numbers or special characters included in the string, they should be returned as they are. Only letters from the latin/english alphabet should be shifted, like in the original Rot13 "implementation".

Please note that using "encode" in Python is considered cheating.

#### Solution:

```Haskell
module Rot13 where

import Data.Char

rot13 :: String -> String
rot13 str = map (\char -> if char `elem` alpha then shift char 13 else char) str
  where alpha = ['a'..'z'] ++ ['A'..'Z']
shift ::  Char -> Int -> Char
shift char offset = chr (start + (ord char - start + offset) `mod` 26)
  where start = if isUpper char then 65 else 97
```
