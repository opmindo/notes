### data 定义
we can use the same name for data type and value constructor,   This has no special meaning, like `Person` in the following: 
```haskell
data Point = Point Float Float deriving(Show)
```
Value constructors are actually **functions that ultimately return a value of a data type. **

#### record syntax
当一种data type包含很多字段的时候，用旧的方式定义会完全搞不懂什么是什么，recoard syntax省事多了
并且这样会声称字段对应的方法 `model`, `year`
```
>> data Car = Car { model :: String, year :: int } deriving Show
>> car = Car { model = "Honda", year = 1988}
>> model car
Honda
>> car 
Car { model = "Honda", year = 1988}
```
#### type parameter and type constructor
给data type加参数可以生成不同的data type，Maybe可以生成`Maybe [Char]` `Maybe Int`之类
```
data Maybe a = Nothing | Just a
-- a 只是定义了类型, 跟参数完全没关系
-- ZipList Int之类的是个整体，而不是真的有具体的值ZipList 1
data ZipList a = ZipList { getZipList :: [a] } 
```
#### newtype
`newtype`比`data`高效，因为data要重新包装，而newtype只包含一个值，只是值的类型被重新定义了一下
```
data ZipList a = ZipList { ZipList :: [a]}
newtype ZipList a = ZipList { ZipList :: [a]}
```

