# random

Generates a random number between 0 and 1

## Syntax

```
y = random[seed]
```

## Attributes

- seed - initializes the random number generator. The seed itself does not need to be random.

## Description

`y = random[seed]` generates a pseudorandom number drawn from the [standard uniform distribution][1], meaning the generated number is restricted to be between 0 and 1. To generate a number between a custom range, see the examples.  

[1]: https://en.wikipedia.org/wiki/Uniform_distribution_(continuous)#Standard_uniform

## Examples

Prints a random number every second

```
match 
  [#time minutes seconds]
  x = random[seed: seconds]
commit
  [#div time: "{{minutes}}{{seconds}}"  text: x]
```

Generate a random number between 5 and 10

```
match
  x = random[]
```

## See Also