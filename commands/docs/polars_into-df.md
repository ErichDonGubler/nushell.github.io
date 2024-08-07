---
title: polars into-df
categories: |
  dataframe
version: 0.96.0
dataframe: |
  Converts a list, table or record into a dataframe.
usage: |
  Converts a list, table or record into a dataframe.
---
<!-- This file is automatically generated. Please edit the command in https://github.com/nushell/nushell instead. -->

# `polars into-df` for [dataframe](/commands/categories/dataframe.md)

<div class='command-title'>Converts a list, table or record into a dataframe.</div>

## Signature

```> polars into-df {flags} ```

## Flags

 -  `--schema, -s {record}`: Polars Schema in format [{name: str}]. CSV, JSON, and JSONL files


## Input/output types:

| input | output |
| ----- | ------ |
| any   | any    |

## Examples

Takes a dictionary and creates a dataframe
```nu
> [[a b];[1 2] [3 4]] | polars into-df
╭───┬───┬───╮
│ # │ a │ b │
├───┼───┼───┤
│ 0 │ 1 │ 2 │
│ 1 │ 3 │ 4 │
╰───┴───┴───╯

```

Takes a list of tables and creates a dataframe
```nu
> [[1 2 a] [3 4 b] [5 6 c]] | polars into-df
╭───┬───┬───┬───╮
│ # │ 0 │ 1 │ 2 │
├───┼───┼───┼───┤
│ 0 │ 1 │ 2 │ a │
│ 1 │ 3 │ 4 │ b │
│ 2 │ 5 │ 6 │ c │
╰───┴───┴───┴───╯

```

Takes a list and creates a dataframe
```nu
> [a b c] | polars into-df
╭───┬───╮
│ # │ 0 │
├───┼───┤
│ 0 │ a │
│ 1 │ b │
│ 2 │ c │
╰───┴───╯

```

Takes a list of booleans and creates a dataframe
```nu
> [true true false] | polars into-df
╭───┬───────╮
│ # │   0   │
├───┼───────┤
│ 0 │ true  │
│ 1 │ true  │
│ 2 │ false │
╰───┴───────╯

```

Convert to a dataframe and provide a schema
```nu
> {a: 1, b: {a: [1 2 3]}, c: [a b c]}| polars into-df -s {a: u8, b: {a: list<u64>}, c: list<str>}
╭───┬───┬───────────────────┬───────────╮
│ # │ a │         b         │     c     │
├───┼───┼───────────────────┼───────────┤
│ 0 │ 1 │ ╭───┬───────────╮ │ ╭───┬───╮ │
│   │   │ │   │ ╭───┬───╮ │ │ │ 0 │ a │ │
│   │   │ │ a │ │ 0 │ 1 │ │ │ │ 1 │ b │ │
│   │   │ │   │ │ 1 │ 2 │ │ │ │ 2 │ c │ │
│   │   │ │   │ │ 2 │ 3 │ │ │ ╰───┴───╯ │
│   │   │ │   │ ╰───┴───╯ │ │           │
│   │   │ ╰───┴───────────╯ │           │
╰───┴───┴───────────────────┴───────────╯

```

Convert to a dataframe and provide a schema that adds a new column
```nu
> [[a b]; [1 "foo"] [2 "bar"]] | polars into-df -s {a: u8, b:str, c:i64} | polars fill-null 3
╭───┬───┬─────┬───╮
│ # │ a │  b  │ c │
├───┼───┼─────┼───┤
│ 0 │ 1 │ foo │ 3 │
│ 1 │ 2 │ bar │ 3 │
╰───┴───┴─────┴───╯

```
