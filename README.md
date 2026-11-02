# Comparator search and stable sorts

Generic ordered search, predicate search and stable sorted copies, with no
native dependencies. `Import algorithmkit`. Use explicit type arguments for
generic calls.

`order` implements `Ordering Of Integer`; its `Compare(a, b) As Integer` returns
negative, zero or positive according to the chosen order. Use direct comparisons
for integers, never `a - b` (which can overflow). A complete standalone consumer
is in `examples/algorithmkit/main.bui` in the repository.

## Install

From a Buoy consumer project with BPM installed:

```sh
bpm add algorithmkit --git https://github.com/BuoyBay/algorithmkit.git --rev refs/heads/main
```

BPM records the resolved commit in its lockfile. Keep that lockfile with the
consumer project for reproducible installs.

## Example

```basic
Import algorithmkit

Class IntegerOrder Implements Ordering Of Integer
    Public Function Compare(a As Integer, b As Integer) As Integer
        If a < b Then Return -1
        If a > b Then Return 1
        Return 0
    End Function
End Class

Sub Main()
    Dim order As New IntegerOrder
    Dim values() As Integer = [7, 2, 2, 9]
    Dim ordered As Array Of Integer = SortedCopy Of Integer(values, order)
    Dim found As MatchRange = EqualRange Of Integer(ordered, 2, order, 0, Array.Count(ordered))
    Print found.First
    Print found.Finish
    Print values(0)
End Sub
```

## Build from source

With the native `build-packages` driver from [devtools](https://github.com/BuoyBay/devtools)
on your `PATH`, run from this checkout:

```sh
build-packages --root "$PWD" --compile-consumer algorithmkit
```

The driver checks source targets and compiles an import consumer. See the
[API guide](docs/API.md) for behavior, limits and any host prerequisites.

## Contributing

[Contributing](CONTRIBUTING.md) · [License](LICENSE)
