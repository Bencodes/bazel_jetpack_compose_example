workspace(name = "bazel_jetpack_compose_example")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

_KOTLIN_COMPILER_VERSION = "1.4.21"

## JVM External

_RULES_JVM_EXTERNAL_VERSION = "4.0"

_RULES_JVM_EXTERNAL_SHA = "31701ad93dbfe544d597dbe62c9a1fdd76d81d8a9150c2bf1ecf928ecdf97169"

http_archive(
    name = "rules_jvm_external",
    sha256 = _RULES_JVM_EXTERNAL_SHA,
    strip_prefix = "rules_jvm_external-{}".format(_RULES_JVM_EXTERNAL_VERSION),
    urls = [
        "https://github.com/bazelbuild/rules_jvm_external/archive/{}.zip".format(_RULES_JVM_EXTERNAL_VERSION),
    ],
)

load("@rules_jvm_external//:defs.bzl", "maven_install")

maven_install(
    artifacts = [
        "org.jetbrains.kotlin:kotlin-stdlib:{}".format(_KOTLIN_COMPILER_VERSION),
        "androidx.core:core-ktx:1.3.2",
        "androidx.appcompat:appcompat:1.2.0",
        "com.google.android.material:material:1.2.1",
        "androidx.compose.material:material:1.0.0-alpha09",
        "androidx.compose.ui:ui:1.0.0-alpha09",
        "androidx.compose.ui:ui-tooling:1.0.0-alpha09",
        "androidx.compose.compiler:compiler:1.0.0-alpha09",
    ],
    repositories = [
        "https://jcenter.bintray.com/",
        "https://maven.google.com",
        "https://repo1.maven.org/maven2",
    ],
)

## Stardoc

_STARDOC_VERSION = "0.4.0"

_STARDOC_SHA = "36b8d6c2260068b9ff82faea2f7add164bf3436eac9ba3ec14809f335346d66a"

http_archive(
    name = "io_bazel_stardoc",
    sha256 = _STARDOC_SHA,
    strip_prefix = "stardoc-{}".format(_STARDOC_VERSION),
    urls = [
        "https://github.com/bazelbuild/stardoc/archive/{}.zip".format(_STARDOC_VERSION),
    ],
)

load("@io_bazel_stardoc//:setup.bzl", "stardoc_repositories")

stardoc_repositories()

## Import Skylib

_SKYLIB_VERSION = "1.0.2"

_SKYLIB_SHA = "97e70364e9249702246c0e9444bccdc4b847bed1eb03c5a3ece4f83dfe6abc44"

http_archive(
    name = "bazel_skylib",
    sha256 = _SKYLIB_SHA,
    urls = [
        "https://github.com/bazelbuild/bazel-skylib/releases/download/{0}/bazel-skylib-{0}.tar.gz".format(_SKYLIB_VERSION),
    ],
)

load("@bazel_skylib//:workspace.bzl", "bazel_skylib_workspace")

bazel_skylib_workspace()

## Protobuf

_PROTOBUF_VERSION = "3.14.0"

_PROTOBUF_SHA = "bf0e5070b4b99240183b29df78155eee335885e53a8af8683964579c214ad301"

http_archive(
    name = "com_google_protobuf",
    sha256 = _PROTOBUF_SHA,
    strip_prefix = "protobuf-{}".format(_PROTOBUF_VERSION),
    urls = [
        "https://github.com/protocolbuffers/protobuf/archive/v{}.zip".format(_PROTOBUF_VERSION),
    ],
)

load("@com_google_protobuf//:protobuf_deps.bzl", "protobuf_deps")

protobuf_deps()

## Rules PKG

_RULES_PKG_VERSION = "0.2.4"

_RULES_PKG_SHA = "4ba8f4ab0ff85f2484287ab06c0d871dcb31cc54d439457d28fd4ae14b18450a"

http_archive(
    name = "rules_pkg",
    sha256 = _RULES_PKG_SHA,
    urls = [
        "https://github.com/bazelbuild/rules_pkg/releases/download/{0}/rules_pkg-{0}.tar.gz".format(_RULES_PKG_VERSION),
    ],
)

## Android

_RULES_ANDROID_VERSION = "0.1.1"

_RULES_ANDROID_SHA = "cd06d15dd8bb59926e4d65f9003bfc20f9da4b2519985c27e190cddc8b7a7806"

http_archive(
    name = "build_bazel_rules_android",
    sha256 = _RULES_ANDROID_SHA,
    strip_prefix = "rules_android-{}".format(_RULES_ANDROID_VERSION),
    urls = [
        "https://github.com/bazelbuild/rules_android/archive/v{}.zip".format(_RULES_ANDROID_VERSION),
    ],
)

load("@build_bazel_rules_android//android:rules.bzl", "android_sdk_repository")

android_sdk_repository(
    name = "androidsdk",
    api_level = 29,
)

## Kotlin

_RULES_KOTLIN_VERSION = "6d0a72d634c9ba2ae26e2af4927500a6739d3acd"

_RULES_KOTLIN_SHA = "600c8d07451bdc85e599180f172e5625cd6afe1eea80dc5aaaa109f5517c07bc"

http_archive(
    name = "io_bazel_rules_kotlin",
    sha256 = _RULES_KOTLIN_SHA,
    strip_prefix = "rules_kotlin-{}".format(_RULES_KOTLIN_VERSION),
    urls = [
        "https://github.com/lyft/rules_kotlin/archive/{}.tar.gz".format(_RULES_KOTLIN_VERSION),
    ],
)

load("@io_bazel_rules_kotlin//kotlin:kotlin.bzl", "kotlin_repositories")

_RULES_KOTLIN_COMPILER_RELEASE = {
    "urls": [
        "https://github.com/JetBrains/kotlin/releases/download/v{v}/kotlin-compiler-{v}.zip".format(v = _KOTLIN_COMPILER_VERSION),
    ],
    "sha256": "46720991a716e90bfc0cf3f2c81b2bd735c14f4ea6a5064c488e04fd76e6b6c7",
}

kotlin_repositories(
    compiler_release = _RULES_KOTLIN_COMPILER_RELEASE,
)

register_toolchains("//:kotlin_toolchain")
