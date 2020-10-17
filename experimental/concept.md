ngl concept
ngl concrete
ngl concept static (number, movie)
ngl concept static parametric (many, sequence)
ngl concept dynamic (add, functions..)

ngc:many
{
    ngl:concept:static <static>
    ngl:concept:dynamic <concept> = ngc:loop
}

add many number
add<static data>
many<static data>

ngl:loop
{
    add<ngc:number>
}

many<data>
the application of many on data must verify that
for n input, output is in range 1, inf

ngl:rule<many>
{
    .phase = concept_creation
    processof many<ngc:number> == ngc:range<1, ngc:infinite>
}
