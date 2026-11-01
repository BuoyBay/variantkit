---
summary: "Import VariantKit and preserve distinct numeric keys in an ExactVariantDictionary."
title: "VariantKit getting started"
related: ["api.md", "index.md", "typed-api.md"]
---

# Getting started

Install Xojo, CollectionsKit and VariantKit archives in your consumer packages directory. Save this as main.bui and compile with `buoy main.bui -o app`. It prints 2 and one.

```buoy
Import Xojo
Import variantkit
Sub Main()
    Dim values As New ExactVariantDictionary
    values.Set(Variant.From(1.0), Variant.From("one"))
    values.Set(Variant.From(1.0000000000000002), Variant.From("next Double"))
    Print values.Count
    Print values.Get(Variant.From(1.0)).Value.AsString().Value
End Sub
```
