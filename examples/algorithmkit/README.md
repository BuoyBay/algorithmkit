# AlgorithmKit standalone example

From the repository root, check, build, and run with the existing sealed package
in an isolated directory:

```sh
example_dir=$(mktemp -d)
mkdir "$example_dir/packages"
cp examples/algorithmkit/main.bui "$example_dir/main.bui"
cp packages/algorithmkit-0.1.0.buipkg "$example_dir/packages/"
(cd "$example_dir" && buoy main.bui --check --diagnostic-format json && buoy main.bui -o app && ./app)
```

Isolation avoids discovery of unrelated app resources in this checkout.

Expected output: `0`, `2`, `7` on separate lines: duplicate range `[0, 2)` in the
sorted copy, followed by the original array's unchanged first element.

Maintainers run the private validation suite before release. See the repository README for public build instructions.
