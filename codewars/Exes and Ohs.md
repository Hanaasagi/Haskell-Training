#### Description:

Check to see if a string has the same amount of 'x's and 'o's. The method must return a boolean and be case insensitive. The string can contains any char.

Examples input/output:  

```
XO("ooxx") => true
XO("xooxx") => false
XO("ooxXm") => true
XO("zpzpzpp") => true // when no 'x' and 'o' is present should return true
XO("zzoo") => false
```

#### Solution:  

```Haskell
module Codewars.Kata.XO where

-- | Returns true if the number of
-- Xs is equal to the number of Os
-- (case-insensitive)
xo :: String -> Bool
xo str = 0 == foldl (\acc s -> if s == 'o' || s == 'O' then
                                   acc +1
                               else
                                   if s == 'x' || s == 'X'then
                                       acc - 1
                                   else
                                       acc
                    ) 0 str
```


#### Better Solution:

```Haskell
module Codewars.Kata.XO where

import Data.Char (toLower)
import Data.List (filter)

xo :: String -> Bool
xo str = count 'x' str == count 'o' str
  where count char = length . filter ((==) char . toLower)
```
