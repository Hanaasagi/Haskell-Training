#### Description:  
Write function avg which calaculates average of numbers in given list.  


#### Solution:  

```Haskell
module Average where

avg :: [Float] -> Float
avg l = sum(l) / fromIntegral (length l) :: Float
```
