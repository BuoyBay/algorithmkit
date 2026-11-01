# AlgorithmKit 0.1.0

Pure Buoy generic ordered search, predicate search and stable sorted copies.
Import `algorithmkit`. Use explicit type arguments, for example:

```buoy
Dim position As Integer = LowerBound Of Integer(items, wanted, order, 0, Array.Count(items))
```

`order` implements `Ordering Of Integer`; its `Compare(a, b) As Integer` returns
negative, zero or positive according to the chosen order. Use direct comparisons
for integers, never `a - b` (which can overflow). A complete standalone consumer
is in `examples/algorithmkit/main.bui` in the repository.

## API contracts

Every search takes explicit `first, finish` bounds. They describe `[first, finish)`;
`0 <= first <= finish <= Array.Count(items)` is required. Invalid bounds throw
`InvalidArgumentException` before any callback runs. No negative-index convention
or end sentinel is used. For the entire array pass `0, Array.Count(items)`.

- `LowerBound Of T(items, value, order, first, finish) As Integer`: first element
  not ordered before value; insertion position in the closed interval `[first, finish]`.
- `UpperBound Of T(...) As Integer`: first element ordered after value; insertion
  position in `[first, finish]`.
- `EqualRange Of T(...) As MatchRange`: fields `First, Finish` delimit all equivalent
  elements in the requested range. Absent values produce equal insertion bounds.
- `BinarySearch Of T(...) As Integer`: first equivalent element within the requested
  range, or `-1` when absent. Equivalence means comparator zero, not object identity.
- `FindIndex Of T(items, selection, first, finish) As Integer`: first predicate match,
  or `-1`. `selection` implements `Selection Of T.Matches(value) As Boolean`.
- `FindLastIndex Of T(...) As Integer`: last predicate match, or `-1`.
- `SortedCopy Of T(items, order) As Array Of T`: shallow `Array.Clone` followed by
  built-in `Array.Sort(copy, comparator)`. Equal elements retain input order.

All ordered searches require the selected subrange already sorted under the same
consistent ordering. Unselected elements need not be sorted. The comparator must
provide a stable, transitive strict weak order, with transitive equivalence; it must
handle every supplied value. NaNs, locale rules, Nil class elements and other domain
policies are the caller's responsibility. No sortedness/order validation is performed.
Only the sign matters; comparator results need not be -1 and 1.

Empty ranges produce `first` for both bounds, `[first, first)` for equal range,
and `-1` for binary/predicate searches, without invoking callbacks. Nil ordering
and selection objects throw `InvalidArgumentException`, including on empty inputs.
Callback exceptions propagate. These algorithms never change the input's element
slots. Sorted copies have independent array storage but preserve class references;
mutating an object through the copy also changes that object as seen through the
input. Callbacks must not mutate/reenter the participating arrays or mutate ordering
keys. No rollback of callback side effects is promised.

Bounds and binary search take O(log n) comparisons and O(1) auxiliary storage;
equal range uses two bounds. Predicate searches use O(n) calls, stopping on the
first match in traversal order. Sorted-copy cost and stability are inherited from
Buoy's built-in comparator sort, plus O(n) cloning. No default sort is reimplemented;
use built-in `Array.Sorted`, `Array.Sort` and `Array.SortOrder` for their existing
comparable-type defaults (including case-insensitive default String ordering).
There are no ArrayUtils extensions or implicit equality/ordering policies.

## Compiler compatibility and verification

The packaged Buoy compiler rejects instantiated generic class nested delegates
and module-qualified explicit generic free calls. This API uses generic interfaces
and unqualified explicit generic calls as the tested workaround. Ordinary import
qualification is therefore a current limitation; avoid importing other free functions
with the same names. No generic function is deliberately first instantiated inside
Try (BUI-501). Candidate evidence is in `tests/algorithmkit/defects/`.

Maintainers run the private validation suite before release. See the repository README for public build instructions.
