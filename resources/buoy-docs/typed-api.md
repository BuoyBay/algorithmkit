---
title: "algorithmkit typed API"
summary: "Source-derived public signatures, properties, parameters, defaults, and return values."
category: "Reference"
order: 21
types: ["MatchRange", "Ordering", "Selection"]
dependencies: []
symbols: ["MatchRange", "Ordering", "Selection"]
related: ["api.md", "getting-started.md", "index.md"]
---

# algorithmkit typed API

Generated from the package source declarations. Platform guards are shown where present; inherited members are documented on the base type. See the [API contracts](api.md) for behavior and limitations.

## MatchRange

`Structure MatchRange`

Half-open matching range [First, Finish); an absent value has First = Finish.

### Fields

| Name | Type | Value / Default | Description |
| --- | --- | --- | --- |
| `First` | `Integer` | — | — |
| `Finish` | `Integer` | — | — |

## Ordering

`Public Interface Ordering Of T`

### Compare

`Function Compare(a As T, b As T) As Integer`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `a` | `T` | `ByVal` | Required |
| `b` | `T` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Integer` |

## Selection

`Public Interface Selection Of T`

### Matches

`Function Matches(value As T) As Boolean`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `value` | `T` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Boolean` |

### LowerBound

`Public Function LowerBound Of T(items As Array Of T, value As T, compare As Ordering Of T, first As Integer, finish As Integer) As Integer`

First index whose element does not precede value, in [first, finish].

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `items` | `Array Of T` | `ByVal` | Required |
| `value` | `T` | `ByVal` | Required |
| `compare` | `Ordering Of T` | `ByVal` | Required |
| `first` | `Integer` | `ByVal` | Required |
| `finish` | `Integer` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Integer` |

### UpperBound

`Public Function UpperBound Of T(items As Array Of T, value As T, compare As Ordering Of T, first As Integer, finish As Integer) As Integer`

First index whose element follows value, in [first, finish].

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `items` | `Array Of T` | `ByVal` | Required |
| `value` | `T` | `ByVal` | Required |
| `compare` | `Ordering Of T` | `ByVal` | Required |
| `first` | `Integer` | `ByVal` | Required |
| `finish` | `Integer` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Integer` |

### EqualRange

`Public Function EqualRange Of T(items As Array Of T, value As T, compare As Ordering Of T, first As Integer, finish As Integer) As MatchRange`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `items` | `Array Of T` | `ByVal` | Required |
| `value` | `T` | `ByVal` | Required |
| `compare` | `Ordering Of T` | `ByVal` | Required |
| `first` | `Integer` | `ByVal` | Required |
| `finish` | `Integer` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `MatchRange` |

### BinarySearch

`Public Function BinarySearch Of T(items As Array Of T, value As T, compare As Ordering Of T, first As Integer, finish As Integer) As Integer`

First equivalent index, or -1 when absent (never an arbitrary duplicate).

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `items` | `Array Of T` | `ByVal` | Required |
| `value` | `T` | `ByVal` | Required |
| `compare` | `Ordering Of T` | `ByVal` | Required |
| `first` | `Integer` | `ByVal` | Required |
| `finish` | `Integer` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Integer` |

### FindIndex

`Public Function FindIndex Of T(items As Array Of T, matches As Selection Of T, first As Integer, finish As Integer) As Integer`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `items` | `Array Of T` | `ByVal` | Required |
| `matches` | `Selection Of T` | `ByVal` | Required |
| `first` | `Integer` | `ByVal` | Required |
| `finish` | `Integer` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Integer` |

### FindLastIndex

`Public Function FindLastIndex Of T(items As Array Of T, matches As Selection Of T, first As Integer, finish As Integer) As Integer`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `items` | `Array Of T` | `ByVal` | Required |
| `matches` | `Selection Of T` | `ByVal` | Required |
| `first` | `Integer` | `ByVal` | Required |
| `finish` | `Integer` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Integer` |

### SortedCopy

`Public Function SortedCopy Of T(items As Array Of T, compare As Ordering Of T) As Array Of T`

Shallow copy sorted stably by the builtin comparator sort.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `items` | `Array Of T` | `ByVal` | Required |
| `compare` | `Ordering Of T` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Array Of T` |
