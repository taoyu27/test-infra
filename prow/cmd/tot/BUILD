package(default_visibility = ["//visibility:public"])

load("@io_bazel_rules_docker//go:image.bzl", "go_image")
load(
    "@io_bazel_rules_go//go:def.bzl",
    "go_binary",
    "go_library",
    "go_test",
)

go_image(
    name = "image",
    base = "@alpine-base//image",
    embed = [":go_default_library"],
    importpath = "k8s.io/test-infra/prow/cmd/tot",
    pure = "on",
)

go_binary(
    name = "tot",
    embed = [":go_default_library"],
    importpath = "k8s.io/test-infra/prow/cmd/tot",
    pure = "on",
)

go_test(
    name = "go_default_test",
    srcs = ["main_test.go"],
    embed = [":go_default_library"],
    importpath = "k8s.io/test-infra/prow/cmd/tot",
)

go_library(
    name = "go_default_library",
    srcs = ["main.go"],
    importpath = "k8s.io/test-infra/prow/cmd/tot",
    deps = ["//vendor/github.com/sirupsen/logrus:go_default_library"],
)

filegroup(
    name = "package-srcs",
    srcs = glob(["**"]),
    tags = ["automanaged"],
    visibility = ["//visibility:private"],
)

filegroup(
    name = "all-srcs",
    srcs = [":package-srcs"],
    tags = ["automanaged"],
)
