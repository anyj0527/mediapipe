# This contains the MediaPipe Tasks NPM package definitions.

load("//mediapipe/framework/port:build_config.bzl", "mediapipe_ts_library")
load("@build_bazel_rules_nodejs//:index.bzl", "pkg_npm")
load("@npm//@bazel/rollup:index.bzl", "rollup_bundle")
load(
    "//mediapipe/framework/tool:mediapipe_files.bzl",
    "mediapipe_files",
)

package(default_visibility = ["//mediapipe/tasks:internal"])

mediapipe_files(srcs = [
    "wasm/audio_wasm_internal.js",
    "wasm/audio_wasm_internal.wasm",
    "wasm/text_wasm_internal.js",
    "wasm/text_wasm_internal.wasm",
    "wasm/vision_wasm_internal.js",
    "wasm/vision_wasm_internal.wasm",
])

# Audio

mediapipe_ts_library(
    name = "audio_lib",
    srcs = ["audio.ts"],
    deps = ["//mediapipe/tasks/web/audio:audio_lib"],
)

rollup_bundle(
    name = "audio_bundle",
    config_file = "rollup.config.mjs",
    entry_point = "audio.ts",
    format = "cjs",
    output_dir = False,
    deps = [
        ":audio_lib",
        "@npm//@rollup/plugin-commonjs",
        "@npm//@rollup/plugin-node-resolve",
    ],
)

pkg_npm(
    name = "audio_pkg",
    package_name = "@mediapipe/tasks-__NAME__",
    srcs = ["package.json"],
    substitutions = {
        "__NAME__": "audio",
        "__DESCRIPTION__": "MediaPipe Audio Tasks",
    },
    tgz = "audio.tgz",
    deps = [
        "wasm/audio_wasm_internal.js",
        "wasm/audio_wasm_internal.wasm",
        ":audio_bundle",
    ],
)

# Text

mediapipe_ts_library(
    name = "text_lib",
    srcs = ["text.ts"],
    deps = ["//mediapipe/tasks/web/text:text_lib"],
)

rollup_bundle(
    name = "text_bundle",
    config_file = "rollup.config.mjs",
    entry_point = "text.ts",
    format = "cjs",
    output_dir = False,
    deps = [
        ":text_lib",
        "@npm//@rollup/plugin-commonjs",
        "@npm//@rollup/plugin-node-resolve",
    ],
)

pkg_npm(
    name = "text_pkg",
    package_name = "@mediapipe/tasks-__NAME__",
    srcs = ["package.json"],
    substitutions = {
        "__NAME__": "text",
        "__DESCRIPTION__": "MediaPipe Text Tasks",
    },
    tgz = "text.tgz",
    deps = [
        "wasm/text_wasm_internal.js",
        "wasm/text_wasm_internal.wasm",
        ":text_bundle",
    ],
)

# Vision

mediapipe_ts_library(
    name = "vision_lib",
    srcs = ["vision.ts"],
    deps = ["//mediapipe/tasks/web/vision:vision_lib"],
)

rollup_bundle(
    name = "vision_bundle",
    config_file = "rollup.config.mjs",
    entry_point = "vision.ts",
    format = "cjs",
    output_dir = False,
    deps = [
        ":vision_lib",
        "@npm//@rollup/plugin-commonjs",
        "@npm//@rollup/plugin-node-resolve",
    ],
)

pkg_npm(
    name = "vision_pkg",
    package_name = "@mediapipe/tasks-__NAME__",
    srcs = ["package.json"],
    substitutions = {
        "__NAME__": "vision",
        "__DESCRIPTION__": "MediaPipe Vision Tasks",
    },
    tgz = "vision_pkg.tgz",
    deps = [
        "wasm/vision_wasm_internal.js",
        "wasm/vision_wasm_internal.wasm",
        ":vision_bundle",
    ],
)
