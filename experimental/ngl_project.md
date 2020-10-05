`nc project add ngl`

`nc [test build install] raz`
`nc [test build install] raz:example:[demo1 demo2]`

entity P1
    concept
        function 
    concrete
        instruction
entity P2

```

ngl:ecosystem:project ngl
{
    .name [ngl]
    //.location no location, conceptual project, not concrete

    ngc:project<cpp> compiler
    {
        .name [nc]
        .vcs [git]
    }
    
    ngc:project website
    {
        .name [ngl_website]
    }

    ngc:project documentation
    {
        .name [doc]
        .compiler.name [mkdocs build]
        .location [home/ads/ngl/doc]
    }
}

ngl:documentation<.phase: build.begin>
{
    ngl:env .command
    {
        interface.send
        [echo Hi, building ] documentation.name [ !]
        [cd ] .location
    }
}
// ngl.documentation.compiler.name ngl.documentation.compiler.option // executed at phase.build.end

ngl<.configuration: experimental, .compiler.name: [clang]>
{
    .compiler
}

```