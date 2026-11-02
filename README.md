# Exact Variant dictionary keys

`Import Xojo` and `Import variantkit` expose `ExactVariantDictionary`, an explicit
adapter for the bundled Xojo shim's Variant. It does not replace Dictionary or
change existing code's key semantics. Install `variantkit`, `collectionskit`, and
the compiler's `Xojo-1.0.0.buipkg` together. BPM resolves the local CollectionsKit
source dependency; the compiler-supplied Xojo archive must be supplied separately.
Xojo also imports the compiler-supplied Crypto, Regex, SQLite3, Postgres, XML
and ZIP packages; install that dependency closure when using an isolated project.
The strict `Package Variant` type is a different implementation and is not accepted
by these APIs. No new hashing or cryptographic primitive is implemented here.

## Install

From a Buoy consumer project with BPM installed:

```sh
bpm add variantkit --git https://github.com/BuoyBay/variantkit.git --rev refs/heads/main
```basic

BPM records the resolved commit in its lockfile. Keep that lockfile with the
consumer project for reproducible installs.
BPM also resolves `collectionskit`.

## Example

```basic
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

## Build from source

With the native `build-packages` driver from [devtools](https://github.com/BuoyBay/devtools)
on your `PATH`, run from this checkout:

```sh
build-packages --root "$PWD" --compile-consumer variantkit
```

The driver checks source targets and compiles an import consumer. See the
[API guide](docs/API.md) for behavior, limits and any host prerequisites.

## Local Buoy setup

On your own machine, install Buoy and run:

```sh
buoy ai init --both
```

## Contributing

[Contributing](CONTRIBUTING.md) · [License](LICENSE)
