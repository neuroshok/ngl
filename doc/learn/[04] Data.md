# Data

ngl describe any information (a concrete data, an idea, an action etc...) as a ngl:data
It is the most generic _type_. 
In ngl we don't talk about types but concepts (ngl:data:concept), the difference is theorical and can be demonstrated like this

```
ngc:function sum
{
    ngc number <a>
    ngc number <b>
}
ngl:sum<4,4> // ok
ngl:sum<4,[four]> // ok
```

```
// pseudo code
function sum(number, number)
{
}
sum(4,4) // ok
sum(4,"four") // type system error
```

## [4.1] Concept

## [4.2] Concrete

## [4.3] Shape

## [4.4] Variable

## [4.5] Type


