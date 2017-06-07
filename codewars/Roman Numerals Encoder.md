#### Description:

Create a function taking a positive integer as its parameter and returning a string containing the Roman Numeral representation of that integer.

Modern Roman numerals are written by expressing each digit separately starting with the left most digit and skipping any digit with a value of zero. In Roman numerals 1990 is rendered: 1000=M, 900=CM, 90=XC; resulting in MCMXC. 2008 is written as 2000=MM, 8=VIII; or MMVIII. 1666 uses each Roman symbol in descending order: MDCLXVI.

Example:

```
solution 1000 -- should return "M"
```

Help:

```
Symbol    Value
I          1
V          5
X          10
L          50
C          100
D          500
M          1,000
```

Remember that there can't be more than 3 identical symbols in a row.

More about roman numerals - http://en.wikipedia.org/wiki/Roman_numerals


#### Solution:

```Haskell
module RomanNumerals where

solution :: Integer -> String
solution n
  | n >= 1000 = 'M': solution (n - 1000)
  | n >= 900  = "CM" ++ solution (n - 900)
  | n >= 500  = 'D': solution (n - 500)
  | n >= 400  = "CD" ++ solution (n - 400)
  | n >= 100  = 'C': solution (n - 100)
  | n >= 90   = "XC" ++ solution (n - 90)
  | n >= 50   = 'L': solution (n - 50)
  | n >= 40   = "XL" ++ solution (n - 40)
  | n >= 10   = 'X': solution (n - 10)
  | n >= 9    = "IX" ++ solution (n - 9)
  | n >= 5    = 'V': solution (n - 5)
  | n >= 4    = "IV" ++ solution (n - 4)
  | n >= 1    = 'I': solution (n - 1)
  | otherwise = ""
```

#### Better Solution:  

```Haskell
module RomanNumerals where

numerals :: [(String, Integer)]
numerals = zip ["M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I" ]
               [1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1]

solution :: Integer -> String
solution 0 = ""
solution n = k ++ solution (n - v)
             where (k, v) = head $ filter ((<=n).snd) numerals
```
