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
/en[english comment]
/fr[commentaire en français !]
function sum(number, number)
{
}
sum(4,4) // ok
sum(4,"four") // type system error
```

## [4.1] Concept

A concept is a ngl:data owned and described by a ngl:entity

## [4.1.1] Intrinsic

- ngc:and
- ngc:element
- ngc:many
- ngc:not
- ngc:or
- ngc:range
- ngc:sequence
- 
    - ngc:static (a number, an object)
    - ngc:dynamic (a function, a process, an entity)

````
ngc:array<ngl:int> ar // incomplete parametrization

// merge concepts using an expression
(ar & ngc:dynamic) dynamic_array

ngc:array
{
    <ngc> data_type // ngc & dynamic -> no match
    <ngc::size> // ngc:number & dynamic -> allow size to change, parameterization complete
    // default storage : stack -> dynamic size not allowed
    // search for a dynamic storage with minimal condition -> heap and database found
    // database -> ngc:dynamic & ngc:persistent
    // heap -> ngc:dynamic -> select heap
}

// add concepts
(ar + ngc:sort) sortable_array
````

## [4.2] Concrete

A concrete is a ngl:data representing the concretization of a ngl:concept
in the ngl:entity storage.

```cpp
// integer array, deduced
[16 51 156]

// digit array
<ngc:digit>[1 6 5 1 1 5 6]

// boolean array
<ngc:boolean>[01101001]
X[00 22 FA]
B[1011010001]
S[coucou c'est moi]

// binary array
<ngc:hexa>[00 22 FF 78]

// string, deduced
[test]

// string, parameterization required, nc can't deduce the concept associated to the shape
<ngc:string>[0123]


// string containing []
[__[ ngs:return begin pattern
ngs:return ]__] end pattern

[__[
use [this] to create "concrete" datas
with multilines
]__]


[[]] // concrete using array of array
[_[]_] // concrete using pattern

[
    [ [123 000] [456 000] ]
    [ [123 000] [456 000] ]
]
``` 

## [4.3] Shape

## [4.4] Variable

## [4.5] Type

### [4.5.1] Arrays

````
ngc:array<ngc:int> array [0 1 2 3]
ngc:array<ngc:int> [array1 array2]

ngc:int[0 1 2 3]
ngc:bool[01001011010]
ngc:hexa[FF00FF]
````

### [4.5.2] Enum

An enum is an array of identifiers

````
ngc:array<ngl:identifier, 4> color_enum [red blue yellow]

//

// 3 identifiers from ngc:color
ngc:color [red blue yellow]

// loop on color identifiers
ngl:loop<ngl:meta<ngc:color>.edges>
{
    // ngl:meta<red>.name
    // ar<red> // ar expect ngc:int,  ngl:meta<red>.index
}

//

// all fields required
ngc <color>
{
    ngc:string name
    ngc:hexa rgb
}

1/description/                   ngc:color<[Red], [FF0000]> red
2/description, syntax2 /         ngc:color<> red{ [Red], [FF0000] }
3/alias parameterization/        ngl:alias<red, ngc:color<[Red], [FF0000]>>
4/alias description of concrete/ ngl:alias red ngc:color<[Red], [FF0000]>
5/edge description of concrete/  ngl:edge<alias> red ngc:color<[Red], [FF0000]>

ngc:color red
{
    .name [Red]
    .rgb [FF0000]
}

ngc:color<.name [Red], .rgb [FF0000]> red
ngc:color<.name [Blue], .rgb [0000FF]> blue

// custom shape
ngs:custom_color ngc:color
{
    red FF0000 [Red]
}
````
