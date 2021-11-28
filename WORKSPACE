workspace(name = "bazel_jetpack_compose_example")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

_KOTLIN_COMPILER_VERSION = "1.5.21"

_COMPOSE_VERSION = "1.0.2"

## JVM External

_RULES_JVM_EXTERNAL_VERSION = "4.1"

_RULES_JVM_EXTERNAL_SHA = "f36441aa876c4f6427bfb2d1f2d723b48e9d930b62662bf723ddfb8fc80f0140"

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
        "androidx.core:core-ktx:1.6.0",
        "androidx.appcompat:appcompat:1.3.1",
        "com.google.android.material:material:1.4.0",
        "androidx.activity:activity-compose:1.3.0",
        "androidx.compose.material:material:{}".format(_COMPOSE_VERSION),
        "androidx.compose.ui:ui:{}".format(_COMPOSE_VERSION),
        "androidx.compose.ui:ui-tooling:{}".format(_COMPOSE_VERSION),
        "androidx.compose.compiler:compiler:{}".format(_COMPOSE_VERSION),
        "androidx.compose.runtime:runtime:{}".format(_COMPOSE_VERSION),
    ],
    override_targets = {
        "org.jetbrains.kotlinx:kotlinx-coroutines-core-jvm": "@//:kotlinx_coroutines_core_jvm",
    },
    repositories = [
        "https://maven.google.com",
        "https://repo1.maven.org/maven2",
    ],
)

# Secondary maven repository used mainly for workarounds
maven_install(
    name = "maven_secondary",
    artifacts = [
        # Workaround to add missing 'sun.misc' dependencies to 'kotlinx-coroutines-core-jvm' artifact
        # Check root BUILD file and 'override_targets' arg of a primary 'maven_install'
        "org.jetbrains.kotlinx:kotlinx-coroutines-core-jvm:1.5.1",
    ],
    fetch_sources = True,
    repositories = ["https://repo1.maven.org/maven2"],
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
    api_level = 30,
)

## Kotlin

# Enable Kotlin
_RULES_KOTLIN_VERSION = "v1.5.0-beta-4"

http_archive(
    name = "io_bazel_rules_kotlin",
    sha256 = "6cbd4e5768bdfae1598662e40272729ec9ece8b7bded8f0d2c81c8ff96dc139d",
    urls = [
        "https://github.com/bazelbuild/rules_kotlin/releases/download/{}/rules_kotlin_release.tgz".format(_RULES_KOTLIN_VERSION),
    ],
)

load("@io_bazel_rules_kotlin//kotlin:repositories.bzl", "kotlin_repositories", "kotlinc_version")

kotlin_repositories(
    compiler_release = kotlinc_version(
        release = _KOTLIN_COMPILER_VERSION,
        sha256 = "f3313afdd6abf1b8c75c6292f4e41f2dbafefc8f6c72762c7ba9b3daeef5da59",
    ),
)

register_toolchains("//:kotlin_toolchain")
