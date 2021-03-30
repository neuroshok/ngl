# Environment

## [9.1] Storage


## [9.2] ngl:environment
```
ngl:environment
{
    ngl:data processor
    {
        ngl:storage register
        ngl:data word_size
    }

    ngl:storage
    {
        ngl:data hdd
        ngl:data ram
    }

    ngl:entity os
    {
        ngl:data word_size
        
        ngl:data <architecture>
        ngl:storage filesystem
        ngl:storage stack
        ngl:storage heap

        ngl:storage console
        ngl:storage io = [console]
    }
}
```