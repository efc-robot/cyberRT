load("@rules_cc//cc:defs.bzl", "cc_binary", "cc_library")
load("//tools/bazel:cpplint.bzl", "cpplint")

package(default_visibility = ["//visibility:public"])

# cc_binary(
#     name = "libcommon_component_example.so",
#     linkshared = True,
#     linkstatic = False,
#     deps = [":common_component_example_lib"],
# )

# cc_library(
#     name = "common_component_example_lib",
#     srcs = ["common_component_example.cc"],
#     hdrs = ["common_component_example.h"],
#     deps = [
#         "//cyber",
#         "//examples/proto:driver_cc_proto",
#     ],
# )

cc_binary(
    name = "publisher",
    srcs = ["helloworld_writer.cc"],
    deps = [
        "//cyber",
        "//examples/proto:driver_cc_proto",
    ],
)

cc_binary(
    name = "subscriber",
    srcs = ["helloworld_reader.cc"],
    deps = [
        "//cyber",
        "//examples/proto:driver_cc_proto",
    ],
)

cpplint()
