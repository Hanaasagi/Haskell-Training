#### Description:
The marketing team are spending way too much time typing in hashtags.
Let's help them with out own Hashtag Generator!

Here's the deal:

- If the final result is longer than 140 chars it must return false.
- If the input is a empty string it must return false.
- It must start with a hashtag (#).
- All words must have their first letter capitalized.

Example Input to Output:

" Hello there thanks for trying my Kata" => "#HelloThereThanksForTryingMyKata"

" Hello World " => "#HelloWorld"

#### Solution:

```Haskell
module Codewars.Kata.Hashtag where

import Data.Maybe
import Data.Char (toUpper)

generateHashtag :: String -> Maybe String
generateHashtag = maybeHashtag . camelize . words
  where
    maybeHashtag xs
      | length xs == 0 = Nothing
      | length xs >= 140 = Nothing
      | otherwise = Just ('#':xs)

camelize :: [String] -> String
camelize = concatMap (\(x:xs) -> (toUpper x):xs)
```
