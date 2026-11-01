---
summary: "Implement an ordering policy and search explicit half-open array ranges."
related: ["index.md", "api.md", "typed-api.md"]
---

# Getting started

Import algorithmkit and implement `Ordering Of T.Compare(a As T, b As T) As Integer`.
Return a negative value for before, zero for equivalent, positive for after.
For Integer use comparisons instead of subtraction to avoid overflow.

Call `SortedCopy Of Integer(items, order)` to clone then sort stably. Call
`LowerBound Of Integer(sortedItems, wanted, order, 0, Array.Count(sortedItems))`
for the first possible match/insertion position. Supply explicit type arguments;
module-qualified generic calls are not supported by the tested compiler.

All ranges are half-open. Every authored example is checked on six targets by the
repository verifier. See the standalone `examples/algorithmkit/main.bui` consumer.


Save the following as `main.bui` in your consumer project. Package archives and any dependencies must be installed as described above.

```buoy
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
