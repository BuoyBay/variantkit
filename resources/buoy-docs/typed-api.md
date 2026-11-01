---
title: "variantkit typed API"
summary: "Source-derived public signatures, properties, parameters, defaults, and return values."
category: "Reference"
order: 21
types: ["ExactVariantDictionary"]
dependencies: ["collectionskit"]
symbols: ["ExactVariantDictionary"]
related: ["api.md", "getting-started.md", "index.md"]
---

# variantkit typed API

Generated from the package source declarations. Platform guards are shown where present; inherited members are documented on the base type. See the [API contracts](api.md) for behavior and limitations.

## VariantKit functions

### ExactVariantKey

`Public Function ExactVariantKey(key As Variant, caseSensitive As Boolean = False) As String`

Exact scalar key encoding; all integer widths share a numeric namespace. Signed zero is normalized. NaN keys reject. Object encoding is a hash bucket, not identity: the dictionary policy additionally checks reference identity.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `key` | `Variant` | `ByVal` | Required |
| `caseSensitive` | `Boolean` | `ByVal` | `False` |

#### Returns

| Type |
| --- |
| `String` |

## ExactVariantDictionary

`Public Class ExactVariantDictionary`

Insertion-ordered dictionary with exact numeric Variant keys and explicit casing.

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `Count` | `Integer` | Yes | No | — | — |
| `CaseSensitive` | `Boolean` | Yes | No | — | — |

### Constructor

`Public Sub Constructor(caseSensitive As Boolean = False, maxEntries As Integer = 100000)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `caseSensitive` | `Boolean` | `ByVal` | `False` |
| `maxEntries` | `Integer` | `ByVal` | `100000` |

Returns: no value.

### Set

`Public Function Set(key As Variant, value As Variant) As Boolean`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `key` | `Variant` | `ByVal` | Required |
| `value` | `Variant` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Boolean` |

### Get

`Public Function Get(key As Variant) As Optional Of Variant`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `key` | `Variant` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Optional Of Variant` |

### Lookup

`Public Function Lookup(key As Variant, fallback As Variant) As Variant`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `key` | `Variant` | `ByVal` | Required |
| `fallback` | `Variant` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Variant` |

### ContainsKey

`Public Function ContainsKey(key As Variant) As Boolean`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `key` | `Variant` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Boolean` |

### Remove

`Public Function Remove(key As Variant) As Boolean`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `key` | `Variant` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Boolean` |

### Entries

`Public Function Entries() As Array Of OrderedEntry Of Variant, Variant`

No parameters.

#### Returns

| Type |
| --- |
| `Array Of OrderedEntry Of Variant, Variant` |

### Keys

`Public Function Keys() As Array Of Variant`

No parameters.

#### Returns

| Type |
| --- |
| `Array Of Variant` |

### Values

`Public Function Values() As Array Of Variant`

No parameters.

#### Returns

| Type |
| --- |
| `Array Of Variant` |

### Clone

`Public Function Clone() As ExactVariantDictionary`

No parameters.

#### Returns

| Type |
| --- |
| `ExactVariantDictionary` |

### Clear

`Public Sub Clear()`

No parameters.

Returns: no value.
