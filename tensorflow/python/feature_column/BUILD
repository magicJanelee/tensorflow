package(
    default_visibility = [
        "//tensorflow:internal",
    ],
    features = [
        "-layering_check",
        "-parse_headers",
    ],
)

licenses(["notice"])  # Apache 2.0

load("//tensorflow:tensorflow.bzl", "py_test")

filegroup(
    name = "all_files",
    srcs = glob(
        ["**/*"],
        exclude = [
            "**/METADATA",
            "**/OWNERS",
        ],
    ),
    visibility = ["//tensorflow:__subpackages__"],
)

py_library(
    name = "feature_column",
    srcs = ["feature_column.py"],
    srcs_version = "PY2AND3",
    deps = [
        ":lookup_ops",
        "//tensorflow/python:embedding_ops",
        "//tensorflow/python:framework",
        "//tensorflow/python:init_ops",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:parsing_ops",
        "//tensorflow/python:platform",
        "//tensorflow/python:sparse_ops",
        "//tensorflow/python:sparse_tensor",
        "//tensorflow/python:string_ops",
        "//tensorflow/python:util",
        "//tensorflow/python:variable_scope",
        "//tensorflow/python:variables",
    ],
)

filegroup(
    name = "vocabulary_testdata",
    srcs = [
        "testdata/warriors_vocabulary.txt",
        "testdata/wire_vocabulary.txt",
    ],
)

py_test(
    name = "feature_column_test",
    srcs = ["feature_column_test.py"],
    data = [":vocabulary_testdata"],
    srcs_version = "PY2AND3",
    tags = ["no_pip"],
    deps = [
        ":feature_column",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:platform_test",
        "//tensorflow/python:training",
    ],
)

# TODO(ptucker,yleon): Move along with 3p/tf/contrib/lookup.
# Test is still in 3p/tf/contrib/lookup.
py_library(
    name = "lookup_ops",
    srcs = [
        "lookup_ops.py",
    ],
    srcs_version = "PY2AND3",
    deps = [
        "//tensorflow/python:array_ops",
        "//tensorflow/python:control_flow_ops",
        "//tensorflow/python:framework",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:lookup_ops_gen",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:string_ops",
        "//tensorflow/python:training",
        "//tensorflow/python:util",
    ],
)
