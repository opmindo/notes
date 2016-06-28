### pattern matching
如果模式匹配多个值，必须用括号括起来(if you want to bind to several variables (even if one of them is just _ and doesn't actually bind at all), we have to surround them in parentheses. )
```
head' :: [a] -> a
head' [] = error "can head an empty list, you Dummy"
-- x:xs need to be put in parentheses
head' (x:xs) = x
```
模式匹配中，List直接用[x, y], [x, _]来进行匹配，不需要括号, kind of syntax sugar
```
tt :: (Show a) => [a] => String
tt [] = "empty list"
-- same as: tt [x] = ...
tt (x:[]) = "one element" ++ (show x)
-- same as tt [x, y] = ..
tt (x:y:[]) = "two elements" ++ (show x) ++ ", " ++ (show y)
-- can't use tt [x, y, _], may be more than 3
tt (x:y:_) = "3 or more than 3 elements"
```
`patterns`可以在匹配的同时保留整体
```
>>let tall all@(x:xs) = (show all) ++ ", first = " ++ show x
>> tall "554"
"\"554\""
```

### guards
`guards`可以用来处理多个条件，类似于c的`switch`
```
max' :: (Ord a) => a -> a -> a  
max' a b   
    | a > b     = addOne a
    -- otherwise 处理其他
    | otherwise = b 
    where addOne x = (x+1)
              decOne x = (x-1)
-- 也可以写成一行
-- max' a b | a > b = a | otherwise = b  
```
可以在`guards`后面加`where`定义方法，不过`where`需要对齐(Notice that all the names are aligned at a single column. If we don't align them nice and proper, Haskell gets confused because then it doesn't know they're all part of the same block.)
`where`跟正常方法一样，可以用pattern matching, 也可以嵌套定义`where`

### `let`表达式
`let <bindings> in <expr>`, 多行bindings需要对齐，单行可以`;`隔开
```
>>(let a = 100; b = 200; c = 300 in a*b*c, let foo="Hey "; bar = "there!" in foo ++ bar) 
(6000000,"Hey there!")  
``` 

### `case`表达式
```
head' :: [a] -> a  
head' [] = error "No head for empty lists!"  
head' (x:_) = x  

-- 跟上面效果一致，方法pattern match只是syntax sugar
head' xs = case xs of [] -> "No head for empty lists!"
                      (x:_) -> x
-- where 里边也可以用第一种形式
describeList :: [a] -> String
describeList xs = "The list is " ++ what xs
    where what [] = "empty."
          what [x] = "a singleton list."
          what xs = "a longer list."
```
### 常见错误
```
-- real world haskell
-- file: ch03/BogusPattern.hs

data Fruit = Apple | Orange
apple = "apple"
orange = "orange" 

-- apple/orange只是模式匹配的变量，不是global var=> apple/orange
whichFruit :: String -> Fruit
whichFruit f = case f of
    apple -> Apple
    orange -> Orange

-- file: ch03/BogusPattern.hs
equational apple = Apple
equational orange = Orange

-- file: ch03/BogusPattern.hs
betterFruit f = case f of
"apple" -> Apple
"orange" -> Orange
```

pattern match不能多次用同一个变量表示`匹配变量相同`(A name can appear only once in a set of pattern bindings)
```
bad_nodesAreSame (Node a _ _) (Node a _ _) = Just a
```
