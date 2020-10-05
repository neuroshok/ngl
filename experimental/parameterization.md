
```
ngc array
{
    <ngl:data> concept // required on descriptor
    ngc:number <size> // required on id
}
ngc:array<ngc:int, 4> ar

ngc zeta
{
    <ngc:array> array // ngc:array with any shape
    <ngc:array<ngc:number, ngl:default>> array // ngc:array with specific shape
    <ngc:array<ngc:movie, 5>> array // ngc:array with specific shape
    // with alias
    ngc concept
    <ngc:array<concept, size>> array
    
    <ngc<ngc, ngc>> concept // any concept of any concepts
    <ngs<ngc, ngc>> concept // specific shape of any concepts
}
ngc:zeta<ngc:array<ngc:int, 2>> z


ngc:zeta alpha
{
    <ngc:custom_array> .array // redescription
}

ngc:project
{
    ngc:configuration config
}

// description
ngc:project project_zeta
{
    ngl:data zeta_data
}

// redescription
ngc:project:project_zeta
{
    ngc:int .zeta_data
}

// parameterized_redescription
ngc:project:project_zeta<config: release>
{
    ngl:data release_data
}
```