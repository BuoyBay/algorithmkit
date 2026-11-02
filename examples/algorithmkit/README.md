# AlgorithmKit ordered-search example

Expected output is `0`, `2`, `7`: the duplicate range in a sorted copy, followed by the original array's unchanged first element.

From this repository root, with Buoy and BPM installed:

```sh
package_source="$PWD"
example_dir=$(mktemp -d)
cp examples/algorithmkit/main.bui "$example_dir/main.bui"
(cd "$example_dir" && bpm init && bpm add algorithmkit --path "$package_source" && bpm build main.bui -o app && ./app)
```

BPM builds from this checkout's package source and installs its declared
dependencies into the consumer project.
