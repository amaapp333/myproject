load("@io_bazel_rules_closure//closure:defs.bzl", "closure_proto_library")
load("@rules_cc//cc:defs.bzl", "cc_proto_library")
load("@rules_proto//proto:defs.bzl", "proto_library")

package(default_visibility = ["//visibility:public"])

licenses(["notice"])

proto_library(
    name = "validator-proto",
    srcs = ["validator.proto"],
)

proto_library(
    name = "validator_proto",
    srcs = ["validator.proto"],
)

cc_proto_library(
    name = "validator_cc_proto",
    deps = [":validator_proto"],
)

closure_proto_library(
    name = "validator_closure_proto",
    deps = [":validator_proto"],
)

# <validator rules protoascii>
# The validator rules, stored in a series of .protoascii files.
# This set of rules is what is released to cdn.ampproject.org/v0/validator.js
genrule(
    name = "validator-all-protoascii-gen",
    srcs = [
        "validator-main.protoascii",
        "validator-css.protoascii",
        "validator-svg.protoascii",
        "@amphtml-extensions//:validator-extensions-protoascii",
    ],
    outs = ["validator.protoascii"],
    cmd = ("cat $(SRCS) > $(OUTS)"),
)
# </validator rules all protoascii>

filegroup(
    name = "testdata_files",
    srcs = glob([
        "testdata/*/*.html",
        "testdata/*/*.out",
        "testdata/*/*.out.cpponly",
    ]),
)
