load("@build_bazel_rules_nodejs//:index.bzl", "nodejs_binary")
load("@io_bazel_rules_docker//nodejs:image.bzl", "nodejs_image")
load("@genrules//google_cloud_run:index.bzl", "deploy")

nodejs_binary(
    name = "server",
    entry_point = "server.js",
    visibility = ["//visibility:public"],
)

nodejs_image(
    name = "server_image",
    entry_point = "server.js",
    include_node_repo_args = False,
    node_repository_name = "nodejs_linux_amd64",
    visibility = ["//visibility:public"],
)

deploy(
    name = "nodejs_service",
    target = ":server_image",
    port = "1337",
)
