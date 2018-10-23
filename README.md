# Minimal reproduction of nested workspace test issue with Bazel when --nolegacy_external_runfiles is turned on

To reproduce run:

```bash
bazel test @nested_workspace//:test
```

The error observed is:

```
exec ${PAGER:-/usr/bin/less} "$0" || exit 1
Executing tests from @nested_workspace//:test
-----------------------------------------------------------------------------
external/bazel_tools/tools/test/test-setup.sh: line 282: : command not found
```

I tested with Bazel 0.18.0 and Bazel 0.17.2 and the result was the same.

This test will pass if the following lines are commented out in `.bazelrc`:

```
run --nolegacy_external_runfiles
test --nolegacy_external_runfiles
```
