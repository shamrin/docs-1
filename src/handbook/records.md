# Records

Records are `attribute: value` pairs associated to a unique ID

## Syntax

```
[attribute]
[attribute: value]
[attribute1: value1, ... , attributeN: valueN]
[attribute1: [attribute2: value]]
r = [attribute ...]
r.attribute
```

## Description

Records are the predominate datatype in Eve. Records are used in two ways:

1. In the match phase, you supply a pattern of attributes to match records in the Eve DB.
2. In the action phase, you supply a pattern of attributes to insert into the Eve DB.

`[attribute]` matches all records with the given attribute.

`[attribute: value]` matches all records with the given attribute filtered on specified value.

`[attribute1: value1, ... , attributeN: valueN]` is the general case for records. This matches all records with all of the given attributes filtered on the given value.

`[attribute1: [attribute2: value]]` nests a record within another record.

`r = [attribute ...]` equates a record to a variable `r`.

`r.attribute` attributes of records can be accessed using dot notation.

## Examples

Match all records with a name, and bind a `#div` for each one.

```
match
  [name]
bind
  [#div text: name]
```

Records can have multiple attributes

```
match
  [#student name grade school]
bind
  [#div text: "{{name}} is in {{grade}}th grade at {{school}}"]
```

Join records by binding attributes from one record into another record. Equate records with variables. Access record attributes using dot notation. 

```
match
  school = [#school name address]
  student = [#student school: name]
bind
  [#div text: "{{student.name}} attends {{school.name}} at {{address}}"]
```

Records can be nested.

```
commit
  [@Jeremey spouse: [@Wendy]]
```

Dot notation can be composed for deep access to records

```
match
  jeremy = [@Jeremy]
bind
  [#div text: "{{jeremy.name}} is married to {{jeremy.spouse.name}}"]
```

## See Also

[binding](binding.md) | [match phase](match-phase.md) | [action phase](action-phase.md) | [name selector](names.md) | [tag selector](tags.md)