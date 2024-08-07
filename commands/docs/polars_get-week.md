---
title: polars get-week
categories: |
  dataframe
version: 0.96.0
dataframe: |
  Gets week from date.
usage: |
  Gets week from date.
---
<!-- This file is automatically generated. Please edit the command in https://github.com/nushell/nushell instead. -->

# `polars get-week` for [dataframe](/commands/categories/dataframe.md)

<div class='command-title'>Gets week from date.</div>

## Signature

```> polars get-week {flags} ```


## Input/output types:

| input | output |
| ----- | ------ |
| any   | any    |

## Examples

Returns week from a date
```nu
> let dt = ('2020-08-04T16:39:18+00:00' | into datetime --timezone 'UTC');
    let df = ([$dt $dt] | polars into-df);
    $df | polars get-week
╭───┬────╮
│ # │ 0  │
├───┼────┤
│ 0 │ 32 │
│ 1 │ 32 │
╰───┴────╯

```
