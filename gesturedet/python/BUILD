# Copyright 2020 The MediaPipe Authors.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

load("@pybind11_bazel//:build_defs.bzl", "pybind_extension")

licenses(["notice"])  # Apache 2.0


# TODO Use flag to decide between build
pybind_extension(
    name = "_framework_bindings",
    srcs = ["framework_bindings.cc"],
    linkopts = select({
        "@mediapipe//third_party:opencv_source_build": [],
        "//conditions:default": [
            "-lopencv_core",
            "-lopencv_imgproc",
            "-lopencv_highgui",
            "-lopencv_video",
            "-lopencv_features2d",
            "-lopencv_calib3d",
            "-lopencv_imgcodecs",
        ],
    }),
    deps = [
        # BUILTIN CALCULATORS --
        "@mediapipe//mediapipe/calculators/core:pass_through_calculator",
        "//gesturedet/graphs:multi_hand_desktop_tflite_calculators_cpu",
        # ------
        "@mediapipe//mediapipe/python/pybind:calculator_graph",
        "@mediapipe//mediapipe/python/pybind:image_frame",
        "@mediapipe//mediapipe/python/pybind:matrix",
        "@mediapipe//mediapipe/python/pybind:packet",
        "@mediapipe//mediapipe/python/pybind:packet_creator",
        "@mediapipe//mediapipe/python/pybind:packet_getter",
        "@mediapipe//mediapipe/python/pybind:resource_util",
        "@mediapipe//mediapipe/python/pybind:timestamp",
        "@mediapipe//mediapipe/python/pybind:validated_graph_config",
    ],
)


pybind_extension(
    name = "_framework_bindings_gpu",
    srcs = ["framework_bindings.cc"],
    linkopts = select({
        "@mediapipe//third_party:opencv_source_build": [],
        "//conditions:default": [
            "-lopencv_core",
            "-lopencv_imgproc",
            "-lopencv_highgui",
            "-lopencv_video",
            "-lopencv_features2d",
            "-lopencv_calib3d",
            "-lopencv_imgcodecs",
        ],
    }),
    deps = [
        # BUILTIN CALCULATORS --
        "@mediapipe//mediapipe/calculators/core:pass_through_calculator",
        "//gesturedet/graphs:multi_hand_desktop_tflite_calculators_gpu",
        # ------
        "@mediapipe//mediapipe/python/pybind:calculator_graph",
        "@mediapipe//mediapipe/python/pybind:image_frame",
        "@mediapipe//mediapipe/python/pybind:matrix",
        "@mediapipe//mediapipe/python/pybind:packet",
        "@mediapipe//mediapipe/python/pybind:packet_creator",
        "@mediapipe//mediapipe/python/pybind:packet_getter",
        "@mediapipe//mediapipe/python/pybind:resource_util",
        "@mediapipe//mediapipe/python/pybind:timestamp",
        "@mediapipe//mediapipe/python/pybind:validated_graph_config",
        "@mediapipe//mediapipe/gpu:gl_calculator_helper",
        "@mediapipe//mediapipe/gpu:gpu_buffer",
        "@mediapipe//mediapipe/gpu:gpu_shared_data_internal",
    ],
)
