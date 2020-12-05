# Versioning

The evolution of the source code is handle through the internal representation
of ngl source code (ngl program graph)

Each change of the program graph will be logged using predefined actions to make cluster
merging possible

# [15.1] nvs

nvs is the version system of ngl and can be controlled by nc.
It's another entity with its own concepts, separated from ngl
```
nvs nvs
{
    refactor
    add
    del
    ...
}
```

ngc:serialize<ngc:movie>
{

}

# [15.2] Program graph evolution

### Concepts
- add : add an edge
- del : delete an edge
- edit :
    - refactor : identifier changed
    - reorder : edge order changed
- add_parameterization
- del_parameterization

Some concepts can be merged, for example (add & parameterization) 

Updating a concept : 
`nc update ngc::movie`

Autodetect the evolution type of the concept and save it.

```
ngc movie
{
    ngc:name <title> 
    // change to ngc:name <name> // nvs:refactor 
    ngc:name <director>
}
```

# [15.3] Concept version resolution

```
Cluster C, concept movie
Cluster A, concept movie v1
Cluster B, concept movie v2

Cluster main use cluster A and B

Duplicated movie in A and B
nvs:resolve<A:movie, B:movie>

// cluster A, v1
ngc movie
{
    ngc:name <title> 
    ngc:name <director>
}

// cluster B, v2
ngc movie
{
    ngc:name <title> 
    ngc:name <director>
    ngc:date <date>
}

// result : no merge required, use v2
```