# ngl:cluster:xeno

__`description`__

A **ngl:cluster<xeno>** is a cluster that contains only **ngl:foreign** descriptions.

__`examples`__

```ngl
// xeno_sfml.ngl (xeno cluster)
ngl:xeno:cluster sfml
{
    ngl:xeno<"init", some, params> init
    ngl:xeno<"cleanup", some, thing, to, give, as, params> cleanup
    ngl:xeno<"wait"> wait

    ngl:xeno<"custom", a, b, c> init
}

// program.ngl
ngl:cluster main

ngl:edge<ngl, main, ngl:cluster:xeno:sfml, nge:import>    // import in main cluster
ngl:edge<ngl, ngl, ngl:cluster:xeno:sfml, nge:import>     // import globally

ngl:xeno:cluster:sfml.init                                // call a xeno function
```