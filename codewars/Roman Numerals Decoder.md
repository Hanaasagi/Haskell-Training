#### Description
Create a function that takes a Roman numeral as its argument and returns its value as a numeric decimal integer. You don't need to validate the form of the Roman numeral.

Modern Roman numerals are written by expressing each decimal digit of the number to be encoded separately, starting with the leftmost digit and skipping any 0s. So 1990 is rendered "MCMXC" (1000 = M, 900 = CM, 90 = XC) and 2008 is rendered "MMVIII" (2000 = MM, 8 = VIII). The Roman numeral for 1666, "MDCLXVI", uses each letter in descending order.

Example:

solution "XXI" -- should return 21

#### solution

```Haskell
table = [("M", 1000), ("D", 500), ("C", 100), ("L", 50), ("X", 10), ("V", 5), ("I",1)]

solution :: String -> Int
solution str = solution' (reverse str) 0 1

solution' :: String -> Int -> Int ->Int
solution' "" res _ = res
solution' str res p = solution' (drop 1 str) (if num < p then res - num else res + num) num
  where c = take 1 str
        (n, num):_ = [(n, num) | (n,num) <- table, n == c]
```
