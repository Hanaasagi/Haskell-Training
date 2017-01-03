####Description:

Write a function called validParentheses that takes a string of parentheses, and determines if the order of the parentheses is valid. validParentheses should return true if the string is valid, and false if it's invalid.

Examples:
validParentheses( "()" ) => returns true
validParentheses( ")(()))" ) => returns false
validParentheses( "(" ) => returns false
validParentheses( "(())((()())())" ) => returns true

All input strings will be nonempty, and will only consist of open parentheses '(' and/or closed parentheses ')'


####Solution:  

    module Codewars.Parentheses where

    validParentheses :: String -> Bool

    validParentheses string = [] == foldr (\chr acc -> if chr == '(' then
                                                         if length acc == 0 || take 1 acc /= ")" then
                                                           ['N']
                                                         else
                                                           drop 1 acc
                                                       else
                                                         ')': acc ) [] string



####Great Solution:  

    module Codewars.Parentheses where

    validParentheses :: String -> Bool
    validParentheses = parse 0

    parse :: Int -> String -> Bool
    parse n [] = n == 0
    parse n (x:xs)
      | n < 0 = False
      | otherwise = case x of
                  '(' -> parse (n + 1) xs
                  ')' -> parse (n - 1) xs
