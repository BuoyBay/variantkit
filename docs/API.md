# VariantKit 0.1.0

`Import Xojo` and `Import variantkit` expose `ExactVariantDictionary`, an explicit
adapter for the bundled Xojo shim's Variant. It does not replace Dictionary or
change existing code's key semantics. Install `variantkit`, `collectionskit`, and
the compiler's `Xojo-1.0.0.buipkg` together. BPM resolves the local CollectionsKit
source dependency; the compiler-supplied Xojo archive must be supplied separately.
Xojo also imports the compiler-supplied Crypto, Regex, SQLite3, Postgres, XML
and ZIP packages; install that dependency closure when using an isolated project.
The strict `Package Variant` type is a different implementation and is not accepted
by these APIs. No new hashing or cryptographic primitive is implemented here.

## Keys and values

Double keys use their IEEE-754 bits rather than six-digit display text. Adjacent
Doubles and `0.3` versus `0.1+0.2` remain distinct. Positive and negative zero are
one key. NaN keys throw InvalidArgumentException before mutation. Infinities are
accepted. Integer widths share exact numeric identity, with unsigned values above
Int64.MaxValue kept distinct from negative integers. String, Boolean, Double and
integer keys occupy separate namespaces.

Strings default to `String.LCase` matching, preserving the first key's original
spelling. `New ExactVariantDictionary(True)` selects exact String comparison.
No Unicode normalization or full case-folding beyond the installed LCase behavior
is added. Nil Variant references, Empty Variants and boxed Nil objects share one
Nil key. Other object keys compare by reference identity. Hash collisions are
resolved by equality; an object's hash alone is never treated as its identity.

`ExactVariantKey(key, caseSensitive=False)` provides the scalar encoding used for
hashing/comparison. Its object encoding is only a hash bucket and must not be used
as a unique or persistent object identifier. Encodings are implementation details,
not an interchange format. String/MemoryBlock semantics follow the installed
runtime. Equal stored keys must remain stable while present.

Values are Xojo Variant references, including a present Nil value. Get returns
`Some(Nil)` for that case and None for an absent key. Object payloads are shared;
there is no deep copy or serialization. Extended ClassicVariant payloads can be
transported explicitly as objects with RBClassic's ClassicInterop helpers.

## API

`New ExactVariantDictionary(caseSensitive=False, maxEntries=100000)` uses the
CollectionsKit entry bound 1..1,000,000. `Count` and `CaseSensitive` are read-only.
`Set(key,value)` returns True for insertion and False for replacement. Replacement
retains key and insertion position; remove/reinsert appends. `Get` returns Optional
Of Variant, `Lookup(key,fallback)` returns the stored value or fallback, and
`ContainsKey`, `Remove`, and `Clear` provide ordinary mutation/inspection.
`Entries()` returns paired insertion-order snapshots. `Keys()` and `Values()`
return detached arrays; take Entries when a single paired snapshot is required.
`Clone()` copies dictionary structure and shares reference payloads.

Storage and behavior reuse OrderedHashMap with a fixed key policy. Average map
operations are O(1); collisions can make them O(n). Snapshots/Clone/Clear are O(n).
There is no live iterator, concurrent mutation, deep copy, eviction or protection
against adversarial hash flooding. Entry bounds do not bound payload bytes.
Keys and values are retained strongly. Internal classes have package-prefixed
names because the installed compiler does not completely enforce private-type
visibility; callers must not depend on these helpers.

## Verify
