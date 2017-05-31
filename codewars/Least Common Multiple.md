#### Description:

Write a function that calculates the least common multiple of its arguments; each argument is assumed to be a non-negative integer.

#### Solution:

```Haskell
module LeastCommonMultiple where
import Prelude hiding (lcm)

lcm :: Integral a => [a] -> a
lcm xs = foldl (\a b -> a * b `div` (max 1 $ gcd a b)) 1 xs
```
