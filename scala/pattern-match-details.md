```
// case block is a PartialFunction
{ case x => y}
```

1. case class, call 
```
case class Test(t: Int)
Test.unapply: Test => Option[Tuple1]
```

2. Seq
```
List(1, 2, 3) match {
  case h +: tail => h
}
// +:（::, :+ also) is a class, but in infix form, just like
case +:(h, tail) => h
```
