# Provenance

Independent implementation of standard half-open binary search and linear predicate
search algorithms; no third-party source was copied. Random oracle fixtures are
locally generated with Python Random seed 140031 and checked with Python bisect,
sorted, and list comprehensions. The sole sorting implementation is Buoy's builtin
Array.Sort comparator overload, invoked on Array.Clone output.

Language/API sources inspected locally: `/usr/share/buoy/docs/documentation/arrays.md`
(Array.Sort, Sorted, SortOrder, Clone, comparator sign and stability),
`generic-methods.md`, `generics.md`, `delegates.md`, `closures.md`, and existing
CollectionKeyPolicy generic interface patterns in this workspace's CollectionsKit.
The delegate/class approach was rejected after actual specialization diagnostics;
see package-local candidate evidence. No upstream reporting, license inheritance,
mathematical conformance, non-Linux runtime or external C library dependency is claimed.
