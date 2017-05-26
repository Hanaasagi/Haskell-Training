#### Description:

>A friend of mine takes a sequence of numbers from 1 to n (where n > 0).
Within that sequence, he chooses two numbers, a and b.
He says that the product of a and b should be equal to the sum of all numbers in the sequence, excluding a and b.
Given a number n, could you tell me the numbers he excluded from the sequence?

The function takes the parameter: `n` (don't worry, n is always strictly greater than 0 and small enough so we shouldn't have overflow) and returns an array of the form:

```
[(a, b), ...] or [[a, b], ...] or {{a, b}, ...} or or [{a, b}, ...]
```

with all `(a, b)` which are the possible removed numbers in the sequence `1 to n`.

`[(a, b), ...] or [[a, b], ...] or {{a, b}, ...} or ...`will be sorted in increasing order of the "a".

It happens that there are several possible (a, b). The function returns an empty array if no possible numbers are found which will prove that my friend has not told the truth!

(See examples for each language in "RUN EXAMPLES")
Examples:

```
removNb(26) should return [(15, 21), (21, 15)]
```

or

```
removNb(26) should return { {15, 21}, {21, 15} }
```

or

```
removeNb(26) should return [[15, 21], [21, 15]]
```

or

```
removNb(26) should return [ {15, 21}, {21, 15} ]
```

or

```
in C:
removNb(26) should return  **an array of pairs {{15, 21}{21, 15}}**
tested by way of strings.
```

#### Solution:

```Haskell
module Codewars.Kata.RemovNB where

removNb :: Integer-> [(Integer, Integer)]
removNb n = [(x, y) | x <- l, let (y, r) = (lsum - x) `quotRem` (x + 1), r == 0, y <= n]
	    where
	      l = [1..n]
	      lsum = (n * (n+1)) `div` 2
```

#### Better Solution:

```Haskell
    module Codewars.Kata.RemovNB where

    removNb :: Integer-> [(Integer, Integer)]
    removNb n = [(a,b) | a <- [1..n], let (b, r) = quotRem (sn -a) (a + 1), r == 0, b <= n, b /= a]
            where sn = sum [1..n]
```
