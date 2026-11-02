# Provenance

Independent implementation of standard half-open binary search and linear
predicate-search algorithms; no third-party source was copied. Sorting delegates
to Buoy's built-in comparator overload on a cloned array.

The API follows Buoy's documented array, generic-interface and closure contracts.
The installed language reference documents comparator signs and sorting stability.
[CollectionsKit](https://github.com/BuoyBay/collectionskit) uses a related generic
policy interface. This package has no external C library dependency and does not
claim compatibility with a separate binary implementation.
