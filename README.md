# bazel_jetpack_compose_example

Sample repo demonstrating how to use Jetpack Compose with Bazel

![CI](https://github.com/Bencodes/bazel_jetpack_compose_example/workflows/CI/badge.svg?branch=master)
[![GitHub license](https://img.shields.io/github/license/Bencodes/bazel_jetpack_compose_example)](https://github.com/Bencodes/bazel_jetpack_compose_example/blob/master/LICENSE)

## Building

`$ bazel build //compose-app:compose_example_app`

```console
❯ bazel build //compose-app:compose_example_app
INFO: Analyzed target //compose-app:compose_example_app (0 packages loaded, 0 targets configured).
INFO: Found 1 target...
Target //compose-app:compose_example_app up-to-date:
  bazel-bin/compose-app/compose_example_app_deploy.jar
  bazel-bin/compose-app/compose_example_app_unsigned.apk
  bazel-bin/compose-app/compose_example_app.apk
INFO: Elapsed time: 0.771s, Critical Path: 0.00s
INFO: 1 process: 1 internal.
INFO: Build completed successfully, 1 total action
```
