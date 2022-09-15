# pants-sourceroot-error

## Reproduction of an error generating a python dist in v2.13

Running the command:

```bash@
./pants package lib/test:dist
```

Works fine in pants `v2.11.1`, but after upgrading to `v2.13.0`

Results in the error:

```text
NoSourceRootError: No source root found for `3rdparty`. See https://www.pantsbuild.org/v2.13/docs/source-roots for how to define source roots.
```

However, adding `"/"` to the list of `root_patterns`, resolves the issue:

```bash
[source]
root_patterns = [
  "/",
  "/lib/*"
]
```

This solution doesn't seem to fit the intended use of `root_patterns`. Is it a bug?
