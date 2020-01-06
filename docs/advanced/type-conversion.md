---
id: type-conversion
title: Type Conversion
---

After formula resolves a value, RockTomate tries to do a conversion if target type and resolved type are not the same. It can do conversion simple as from `string` to `int` or as complicated as `string[]` to `int`.

This article goes into full detail on what to expect from converted values. A conversion between types `string` and `int` will be used as an example but this applies to many other common types.

On the left hand-side is the resolved value type and on the right hand-side is the target type. Target type is a type expected by the formula as requested by the input field of the Step.

## `string` and `int`

| Conversion        | Behaviour                                   |
|-------------------|---------------------------------------------|
| `string` to `int` | `string` will be parsed to be of type `int` |
| `int` to `string` | `int`  will be converted to `string`        |

## `string[]` and `int[]`

| Conversion            | Behaviour                                                                                                |
|-----------------------|----------------------------------------------------------------------------------------------------------|
| `string[]` to `int[]` | Each individual item will be parsed to `int` type and placed into an collection of type `int[]`          |
| `int[]` to `string[]` | Each individual item will be converted to `string` type and placed into an collection of type `string[]` |

## `string` and `string[]`

| Conversion             | Behaviour                                                        |
|------------------------|------------------------------------------------------------------|
| `string[]` to `string` | First item of the initial collection will be returned            |
| `string` to `string[]` | Resolved value will be put into an collection of type `string[]` |

## `string[]` and `int`

| Conversion             | Behaviour                                                                               |
|------------------------|-----------------------------------------------------------------------------------------|
| `string[]` to `int`    | First item of the initial collection will be parsed into type of `int` and returned     |
| `int` to `string[]`    | Resolved value will converted to `string` and put into an collection of type `string[]` |

## `string` and `int[]`

| Conversion             | Behaviour                                                                               |
|------------------------|-----------------------------------------------------------------------------------------|
| `string` to `int[]`    | String will be parsed into type `int` and put into collection of type `int[]`           |
| `int[]` to `string`    | First item of the array will be converted to `string` and returned                      |