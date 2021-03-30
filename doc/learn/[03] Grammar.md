# Grammar

The grammar of ngl is customisable, see ngl:shape for more informations.

There is two grammars for ngl, the native grammar, used to create the standard grammar.

## [3.1] Symbols
- `:` : edge
- `{}` : vector data
- `[]` : concrete data
- `<>` : parameterization

## [3.2] Keywords

There is no keywords in ngl. As the only way to create an identifier is from another one, the root identifier will be the equivalent of a keyword. It will be created with a self description.

```
ngl ngl
```

## [3.3] Native grammar

The native grammar is very basic and intrinsic to the ngl compiler. It will just be used to create
the standard grammar (the ngl source code shape)

You can only define new shapes from existing shapes or using intrinsic concepts

```
ngl:shape digit
{
    ngl:range<[0], [9]>
}
```

## [3.4] Standard grammar
### [3.4.1] Expression
#### [3.4.1.1] Description

**descriptor** : existing identifier
**described_identifier** : new identifier

##### Self description

`ngl ngl`

A self descriptor is an entity

##### Scalar description

`ngc number`

##### Post description

````
ngc movie

ngc:movie // post_description of ngc:movie
{
    ngc:name
}
````

##### Vector description

```
ngc movie
{
    ngc:name name
    ngc:name director
}
```

##### Overwrite description

```
ngc array
{
    ngl:data data_type
}

ngc:array integer_array
{
    ngc:integer .data_type // redescription of ngc:array.data_type
}
```

All described_identifiers in the bloc are connected to the described_identifier with an edge of type <has>

`ngl:edge<ngl, ngc:movie, ngc:movie:name, has>`

#### [3.4.1.2] Parameterization

##### Descriptor parameterization (concept)

```
ngc zeta
{
    <ngl:concept> data_type // descriptor_identifier require a parameterisation of a ngl:concept
    <ngl:concept> data_type ngc:integer // default parameterization
                                        // result in ngl:concept<ngc:integer>
    
    <ngl:concrete> value // descriptor_identifier require a parameterisation of a concrete
    <ngl:concrete> value [4] // default parameterization
                             // result in ngl:concrete<4>    
}
```

##### Identifier parameterization (concrete)

```
ngc array
{
    ngc:number <data_type>

    ngc:integer <size> // required described_identifier
    ngc:integer size [255]
}
```

##### Overwrite description

```
ngc array
{
    <ngl:data> data_type
}

ngc:array integer_array
{
    <ngc:integer> .data_type // redescription of ngc:array.data_type required
    // call with integer_array<[4]>
}
```

##### Parameterized description

```
ngc:project:project_zeta<config: release>
{
    ngl:data release_data
}
```

##### Meta parameterization

A parameterized description can use partially parameterized identifiers

```
ngc array
{
    <ngc> type
    ngc:integer <size>
}

ngc resizer
{
    ngc <data> // data is ngc:array<ngc:integer, ?>
    
    ngc:integer internal_size [12]
    
    ngl:meta<data>.parameterize<internal_size>
}

// parameter <size> missing
ngc:resizer<ngc:array<ngc:integer, ?>>
{
    
}

ngc:resizer<ngc:array<ngc:integer>>

```

Append datas for the specified values to the parameterized_descriptor

##### Concept shape

```
ngc zeta
{
    <ngc<ngc, ngc>> concept // any concept taking 2 required concept parameters
}
```

##### Difference between descriptor and identifier parameterization

```
<ngl:concept> data_type [ngc:integer] // (1) expect a concept, concrete interpreted as a concept
ngl:concept <data_type> [4] // (2) expect a concrete

(1) array<ngc:number> [ngc:integer ngc:real ngc:complex]
(2) array<ngc:number> [1 2 3]
```

##### Identifier in parameters

```
ngl:cluster
{
    ngc concept
    ngc entity
    ngc xeno
    // or : ngc [concept entity xeno]
}

ngl:cluster<entity> // search in current scope then ngl:cluster scope
```
