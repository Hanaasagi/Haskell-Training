#### Description:

Write a function called `validBraces` that takes a string of braces, and determines if the order of the braces is valid. `validBraces` should return true if the string is valid, and false if it's invalid.

This Kata is similar to the Valid Parentheses Kata, but introduces four new characters. Open and closed brackets, and open and closed curly braces. Thanks to arnedag for the idea!

All input strings will be nonempty, and will only consist of open parentheses '(' , closed parentheses ')', open brackets '[', closed brackets ']', open curly braces '{' and closed curly braces '}'.

What is considered Valid? A string of braces is considered valid if all braces are matched with the correct brace.
For example:
'(){}[]' and '([{}])' would be considered valid, while '(}', '[(])', and '[({})](]' would be considered invalid.

Examples:
`validBraces( "(){}[]" )` => returns true
`validBraces( "(}" ) =>` returns false
`validBraces( "[(])" )` => returns false
`validBraces( "([{}])" )` => returns true

#### Solution:

```Haskell
module Codewars.Kata.Braces where
import Data.Maybe (fromMaybe, listToMaybe)

match :: Char -> Char
match '{' = '}'
match '[' = ']'
match '(' = ')'
match  _  = ' '

validBraces :: String -> Bool
validBraces = check []
  where  check [] [] = True
         check _  [] = False
         check stack (x:xs)
           | x `elem` "({[" = check (x:stack) xs
           | otherwise = if x == (match . fromMaybe ' ' . listToMaybe $ stack) then
                           check (tail stack) xs
                         else False
```
