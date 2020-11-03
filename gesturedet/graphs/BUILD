# Copyright 2019 The MediaPipe Authors.
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

load(
    "@mediapipe//mediapipe/framework/tool:mediapipe_graph.bzl",
    "mediapipe_binary_graph",
)

licenses(["notice"])

package(default_visibility = ["//visibility:public"])

exports_files(glob([
    "*.pbtxt",
]))

cc_library(
    name = "desktop_offline_calculators",
    deps = [
        "@mediapipe//mediapipe/calculators/core:flow_limiter_calculator",
        "@mediapipe//mediapipe/calculators/core:gate_calculator",
        "@mediapipe//mediapipe/calculators/core:immediate_mux_calculator",
        "@mediapipe//mediapipe/calculators/core:packet_inner_join_calculator",
        "@mediapipe//mediapipe/calculators/core:previous_loopback_calculator",
        "@mediapipe//mediapipe/calculators/video:opencv_video_decoder_calculator",
        "@mediapipe//mediapipe/calculators/video:opencv_video_encoder_calculator",
    ],
)


# TODO Use flag to decide GPU/no-GPU build
cc_library(
    name = "multi_hand_desktop_tflite_calculators_cpu",
    deps = [
        ":desktop_offline_calculators",
        "@mediapipe//mediapipe/calculators/util:association_norm_rect_calculator",
        "@mediapipe//mediapipe/calculators/util:collection_has_min_size_calculator",
        "//gesturedet/graphs/subgraphs:multi_hand_detection_cpu",
        "//gesturedet/graphs/subgraphs:multi_hand_landmark_cpu",
        "//gesturedet/graphs/subgraphs:multi_hand_renderer_cpu",
    ],
)


cc_library(
    name = "multi_hand_desktop_tflite_calculators_gpu",
    deps = [
        ":desktop_offline_calculators",
        "@mediapipe//mediapipe/calculators/util:association_norm_rect_calculator",
        "@mediapipe//mediapipe/calculators/util:collection_has_min_size_calculator",
        "//gesturedet/graphs/subgraphs:multi_hand_detection_cpu",
        "//gesturedet/graphs/subgraphs:multi_hand_landmark_cpu",
        "//gesturedet/graphs/subgraphs:multi_hand_renderer_cpu",
    ],
)


mediapipe_binary_graph(
    name = "multi_hand_tracking_desktop_live",
    graph = "multi_hand_tracking_desktop_live.pbtxt",
    output_name = "multi_hand_tracking_desktop_live.binarypb",
    deps = [
        ":desktop_offline_calculators",
        "@mediapipe//mediapipe/calculators/util:association_norm_rect_calculator",
        "@mediapipe//mediapipe/calculators/util:collection_has_min_size_calculator",
    ],
)


mediapipe_binary_graph(
    name = "raw_multi_hand_tracking_desktop_live",
    graph = "raw_multi_hand_tracking_desktop_live.pbtxt",
    output_name = "raw_multi_hand_tracking_desktop_live.binarypb",
)
