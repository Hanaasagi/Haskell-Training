####Description:

You probably know the "like" system from Facebook and other pages. People can "like" blog posts, pictures or other items. We want to create the text that should be displayed next to such an item.

Implement a function likes :: [String] -> String, which must take in input array, containing the names of people who like an item. It must return the display text as shown in the examples:  

    likes [] // must be "no one likes this"
    likes ["Peter"] // must be "Peter likes this"
    likes ["Jacob", "Alex"] // must be "Jacob and Alex like this"
    likes ["Max", "John", "Mark"] // must be "Max, John and Mark like this"
    likes ["Alex", "Jacob", "Mark", "Max"] // must be "Alex, Jacob and 2 others like this"

For more than 4 names, the number in and 2 others simply increases.  

####Solution:

    module Likes where

    likes :: [String] -> String
    likes xs
      | len == 0 = "no one likes this"
      | len == 1 = xs !! 0 ++ " likes this"
      | len == 2 = xs !! 0 ++ " and " ++ xs !! 1 ++ " like this"
      | len == 3 = xs !! 0 ++ ", " ++ xs !! 1  ++ " and " ++ xs !! 2 ++ " like this"
      | len > 3 = xs !! 0 ++ ", " ++ xs !! 1  ++ " and " ++ show(len-2) ++ " others like this"
      where len = length xs

####Great Solution:  

    module Likes where

    likes :: [String] -> String
    likes list =
        unwords [subjects list, message list]
        
    subjects []                 = "no one"
    subjects [x]                = x
    subjects [x, y]             = unwords [x, "and", y]
    subjects [x, y, z]          = unwords [x ++ ",", y, "and", z]
    subjects (x : y : _ : rest) = unwords [x ++ ",", y, "and", show (length rest + 1), "others"]

    message list
        | length list < 2 = "likes this"
        | otherwise       = "like this"