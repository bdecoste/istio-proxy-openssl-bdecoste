# Copyright 2016 Google Inc. All Rights Reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#    http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
################################################################################
#

load(
     "//:repositories.bzl",
     "googletest_repositories",
     "mixerapi_dependencies",
)

googletest_repositories()
mixerapi_dependencies()

new_local_repository(
    name = "openssl",
    path = "/usr/local/lib64",
    build_file = "openssl.BUILD"
)

# When updating envoy sha manually please update the sha in istio.deps file also
ENVOY_SHA = "d61de1ec7f9cd6b6e9c533b354f72ac3b28d7dd1"

git_repository(
    name = "envoy",
    commit = "d61de1ec7f9cd6b6e9c533b354f72ac3b28d7dd1",
    remote = "https://github.com/bdecoste/envoy",
)

ENVOY_OPENSSL_SHA="927f136c36f07ec104e1ffafae668182852dd512"

git_repository(
    name = "envoy_openssl",
    commit = "927f136c36f07ec104e1ffafae668182852dd512",
    remote = "https://github.com/bdecoste/envoy-proxy-openssl",
)

load("@envoy//bazel:repositories.bzl", "envoy_dependencies")
envoy_dependencies()

load("@envoy//bazel:cc_configure.bzl", "cc_configure")
cc_configure()

load("@envoy_api//bazel:repositories.bzl", "api_dependencies")
api_dependencies()

load("@io_bazel_rules_go//go:def.bzl", "go_rules_dependencies", "go_register_toolchains")
go_rules_dependencies()
go_register_toolchains()

load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")
git_repository(
    name = "org_pubref_rules_protobuf",
    commit = "563b674a2ce6650d459732932ea2bc98c9c9a9bf",  # Nov 28, 2017 (bazel 0.8.0 support)
    remote = "https://github.com/pubref/rules_protobuf",
)