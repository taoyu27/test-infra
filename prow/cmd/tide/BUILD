load("@io_bazel_rules_docker//go:image.bzl", "go_image")
load(
    "@io_bazel_rules_go//go:def.bzl",
    "go_binary",
    "go_library",
)

go_image(
    name = "image",
    base = "@git-base//image",
    embed = [":go_default_library"],
    importpath = "k8s.io/test-infra/prow/cmd/tide",
    pure = "on",
    visibility = ["//visibility:public"],
)

go_library(
    name = "go_default_library",
    srcs = ["main.go"],
    importpath = "k8s.io/test-infra/prow/cmd/tide",
    visibility = ["//visibility:private"],
    deps = [
        "//prow/config:go_default_library",
        "//prow/git:go_default_library",
        "//prow/github:go_default_library",
        "//prow/kube:go_default_library",
        "//prow/tide:go_default_library",
        "//vendor/github.com/sirupsen/logrus:go_default_library",
    ],
)

go_binary(
    name = "tide",
    embed = [":go_default_library"],
    importpath = "k8s.io/test-infra/prow/cmd/tide",
    pure = "on",
    visibility = ["//visibility:public"],
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
    visibility = ["//visibility:public"],
)
