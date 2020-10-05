create an entity
`nc add entity ark`

add a concept_cluster
`nc add cluster ncc /home/ncc/`
`nc add cluster ncc neuroshok.com/standard/ncc`

create a project of type ngl:project described here ngl/project.md
`nc add ngl:project zeta`

to use another project type

create a custom nglp:project in a file and add it in the current entity graph
`nc edge ark:project:website /home/projects/website.ngl:website`

 specify the path to an identifier containing the description
`nc add ark:project:website zeta`

```
zeta/
  ngl (optional, language description)
  nc (concretization description)
```

concretize the project
`nc zeta`