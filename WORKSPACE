workspace(name = "bazel_jetpack_compose_example")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

_KOTLIN_COMPILER_VERSION = "1.4.30"

_JETPACK_COMPOSE_VERSION = "1.0.0-beta01"

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
        "androidx.activity:activity-compose:1.3.0-alpha02",
        "androidx.compose.material:material:{}".format(_JETPACK_COMPOSE_VERSION),
        "androidx.compose.ui:ui:{}".format(_JETPACK_COMPOSE_VERSION),
        "androidx.compose.ui:ui-tooling:{}".format(_JETPACK_COMPOSE_VERSION),
        "androidx.compose.compiler:compiler:{}".format(_JETPACK_COMPOSE_VERSION),
        "androidx.compose.runtime:runtime:{}".format(_JETPACK_COMPOSE_VERSION),
    ],
    override_targets = {
        "org.jetbrains.kotlin:kotlin-stdlib": "@com_github_jetbrains_kotlin//:kotlin-stdlib",
        "org.jetbrains.kotlin:kotlin-stdlib-jdk7": "@com_github_jetbrains_kotlin//:kotlin-stdlib-jdk7",
        "org.jetbrains.kotlin:kotlin-stdlib-jdk8": "@com_github_jetbrains_kotlin//:kotlin-stdlib-jdk8",
    },
    repositories = [
        "https://jcenter.bintray.com/",
        "https://maven.google.com",
        "https://repo1.maven.org/maven2",
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

_RULES_KOTLIN_VERSION = "v1.5.0-alpha-3"

_RULES_KOTLIN_SHA = "eeae65f973b70896e474c57aa7681e444d7a5446d9ec0a59bb88c59fc263ff62"

http_archive(
    name = "io_bazel_rules_kotlin",
    sha256 = _RULES_KOTLIN_SHA,
    type = "tar.gz",
    urls = ["https://github.com/bazelbuild/rules_kotlin/releases/download/%s/rules_kotlin_release.tgz" % _RULES_KOTLIN_VERSION],
)

load("@io_bazel_rules_kotlin//kotlin:kotlin.bzl", "kotlin_repositories")

_RULES_KOTLIN_COMPILER_RELEASE = {
    "urls": [
        "https://github.com/JetBrains/kotlin/releases/download/v{v}/kotlin-compiler-{v}.zip".format(v = _KOTLIN_COMPILER_VERSION),
    ],
    "sha256": "7b0aae9dca5ea899ef05dedc0a6fdd6e359451e56ff0dd3354443b3208b31800",
}

kotlin_repositories(
    compiler_release = _RULES_KOTLIN_COMPILER_RELEASE,
)

register_toolchains("//:kotlin_toolchain")
