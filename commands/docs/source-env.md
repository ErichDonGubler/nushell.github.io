---
title: source-env
categories: |
  core
version: 0.95.0
core: |
  Source the environment from a source file into the current environment.
usage: |
  Source the environment from a source file into the current environment.
---
<!-- This file is automatically generated. Please edit the command in https://github.com/nushell/nushell instead. -->

# `source-env` for [core](/commands/categories/core.md)

<div class='command-title'>Source the environment from a source file into the current environment.</div>

## Signature

```> source-env {flags} (filename)```

## Parameters

 -  `filename`: The filepath to the script file to source the environment from.


## Input/output types:

| input | output |
| ----- | ------ |
| any   | any    |

## Examples

Sources the environment from foo.nu in the current context
```nu
> source-env foo.nu

```
