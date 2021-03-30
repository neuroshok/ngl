# Interaction

## [6.1] Edge

An edge is a link between two ngl:data. It's used to create a logic between datas (interactions, constraints, aliases, imports etc ...)

```
ngl:edge<ngl, ngl:concept, ngc, nge:alias> // low level
ngl:alias<ngl:concept, ngc> // user level
```

## [6.2] Entity



## [6.3] I/O

I/O is represented by read/write operations on a ngl:storage 

```
ngl:project program
{
    ngl:environment:os:io = [io:console, logger] // read/write
}

ngl:program
{
    ngl:data input = ngl:read

    ngl:write<[coucou]>
}

ngl:function write
{
    ngl:data <value>
    ngl:entity <targets> = ngl:environment:os:io // ngl:environment:os:io = [console database]
}
```