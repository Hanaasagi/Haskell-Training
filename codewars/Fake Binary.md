####Description:

Given a string of numbers, you should replace any number below 5 with '0' and any number 5 and above with '1'. Return the resulting string.


####Solution:

	module Codewars.Kata.FakeBinary where

	fakeBin :: String -> String
	fakeBin [] = []
	fakeBin (x:xs) = c:fakeBin xs
	  where c = if x >= '5' then '1' else '0'
