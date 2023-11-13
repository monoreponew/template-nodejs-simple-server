load("@aspect_rules_js//js:defs.bzl", "js_binary")
load("@genrules//google_cloud_run:index.bzl", "deploy")
load("@aspect_rules_js//js:defs.bzl", "js_image_layer")

js_binary(
    name = "server",
    entry_point = "server.js",
    visibility = ["//visibility:public"],
)

js_image_layer(
    name = "layer",
    binary = ":server",
)

deploy(
    name = "js_service",
    tar = ":layer",
    cmd = "server/server",
    port = "1337",
)
