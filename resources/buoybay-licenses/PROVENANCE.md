# Provenance

Original adapter implementation for this workspace. No third-party implementation
code copied. Exact binary64 encoding uses the installed Xojo MemoryBlock Double
and UInt64 accessors; Python struct provides an independent bit oracle. Policy
hashing, collision resolution, insertion order and reference ownership reuse local
CollectionsKit. Bundled Xojo Variant and the strict Variant package are distinct
and deliberately not silently interconverted.
