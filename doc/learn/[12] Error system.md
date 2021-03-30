# Error system

Error type
```
System error
Programmer error
User error
```

Error handling // depends on error type
```
terminate
ignore
call<custom_function>
```

## [12.1] Rule based errors

The error system can generate errors based on the rule constraints.
If a rule is broken, it can trigger an error.

```
ngc:storage my_storage
ngl:rule<my_storage, ignore> // on broken rule, no error generated because of the error handling parameter
{
    ! ngl:edge
    ngl:edge:read
}
```