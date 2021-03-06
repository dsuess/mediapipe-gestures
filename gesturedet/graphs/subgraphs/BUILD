# Copyright 2019 The MediaPipe Authors.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http:@mediapipe//www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

load(
    "@mediapipe//mediapipe/framework/tool:mediapipe_graph.bzl",
    "mediapipe_simple_subgraph",
)

licenses(["notice"])

package(default_visibility = ["//visibility:public"])

mediapipe_simple_subgraph(
    name = "hand_detection_cpu",
    graph = "hand_detection_cpu.pbtxt",
    register_as = "HandDetectionSubgraph",
    deps = [
        "@mediapipe//mediapipe/calculators/image:image_properties_calculator",
        "@mediapipe//mediapipe/calculators/image:image_transformation_calculator",
        "@mediapipe//mediapipe/calculators/tflite:ssd_anchors_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_converter_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_custom_op_resolver_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_inference_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_tensors_to_detections_calculator",
        "@mediapipe//mediapipe/calculators/util:detection_label_id_to_text_calculator",
        "@mediapipe//mediapipe/calculators/util:detection_letterbox_removal_calculator",
        "@mediapipe//mediapipe/calculators/util:detections_to_rects_calculator",
        "@mediapipe//mediapipe/calculators/util:detections_to_render_data_calculator",
        "@mediapipe//mediapipe/calculators/util:non_max_suppression_calculator",
        "@mediapipe//mediapipe/calculators/util:rect_transformation_calculator",
    ],
)

mediapipe_simple_subgraph(
    name = "multi_hand_detection_cpu",
    graph = "multi_hand_detection_cpu.pbtxt",
    register_as = "MultiHandDetectionSubgraph",
    deps = [
        "@mediapipe//mediapipe/calculators/core:begin_loop_calculator",
        "@mediapipe//mediapipe/calculators/core:clip_vector_size_calculator",
        "@mediapipe//mediapipe/calculators/core:end_loop_calculator",
        "@mediapipe//mediapipe/calculators/image:image_properties_calculator",
        "@mediapipe//mediapipe/calculators/image:image_transformation_calculator",
        "@mediapipe//mediapipe/calculators/tflite:ssd_anchors_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_converter_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_custom_op_resolver_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_inference_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_tensors_to_detections_calculator",
        "@mediapipe//mediapipe/calculators/util:detection_label_id_to_text_calculator",
        "@mediapipe//mediapipe/calculators/util:detection_letterbox_removal_calculator",
        "@mediapipe//mediapipe/calculators/util:detections_to_rects_calculator",
        "@mediapipe//mediapipe/calculators/util:non_max_suppression_calculator",
        "@mediapipe//mediapipe/calculators/util:rect_transformation_calculator",
    ],
)

mediapipe_simple_subgraph(
    name = "hand_landmark_cpu",
    graph = "hand_landmark_cpu.pbtxt",
    register_as = "HandLandmarkSubgraph",
    deps = [
        "@mediapipe//mediapipe/calculators/core:split_normalized_landmark_list_calculator",
        "@mediapipe//mediapipe/calculators/core:split_vector_calculator",
        "@mediapipe//mediapipe/calculators/image:image_cropping_calculator",
        "@mediapipe//mediapipe/calculators/image:image_properties_calculator",
        "@mediapipe//mediapipe/calculators/image:image_transformation_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_converter_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_custom_op_resolver_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_inference_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_tensors_to_classification_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_tensors_to_floats_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_tensors_to_landmarks_calculator",
        "@mediapipe//mediapipe/calculators/util:detections_to_rects_calculator",
        "@mediapipe//mediapipe/calculators/util:landmark_letterbox_removal_calculator",
        "@mediapipe//mediapipe/calculators/util:landmark_projection_calculator",
        "@mediapipe//mediapipe/calculators/util:landmarks_to_detection_calculator",
        "@mediapipe//mediapipe/calculators/util:landmarks_to_render_data_calculator",
        "@mediapipe//mediapipe/calculators/util:rect_transformation_calculator",
        "@mediapipe//mediapipe/calculators/util:thresholding_calculator",
        "@mediapipe//mediapipe/graphs/hand_tracking/calculators:hand_landmarks_to_rect_calculator",
    ],
)

mediapipe_simple_subgraph(
    name = "multi_hand_landmark_cpu",
    graph = "multi_hand_landmark.pbtxt",
    register_as = "MultiHandLandmarkSubgraph",
    deps = [
        ":hand_landmark_cpu",
        "@mediapipe//mediapipe/calculators/core:begin_loop_calculator",
        "@mediapipe//mediapipe/calculators/core:end_loop_calculator",
        "@mediapipe//mediapipe/calculators/util:filter_collection_calculator",
    ],
)

mediapipe_simple_subgraph(
    name = "renderer_cpu",
    graph = "renderer_cpu.pbtxt",
    register_as = "RendererSubgraph",
    deps = [
        "@mediapipe//mediapipe/calculators/util:annotation_overlay_calculator",
        "@mediapipe//mediapipe/calculators/util:detections_to_render_data_calculator",
        "@mediapipe//mediapipe/calculators/util:labels_to_render_data_calculator",
        "@mediapipe//mediapipe/calculators/util:landmarks_to_render_data_calculator",
        "@mediapipe//mediapipe/calculators/util:rect_to_render_data_calculator",
    ],
)

mediapipe_simple_subgraph(
    name = "multi_hand_renderer_cpu",
    graph = "multi_hand_renderer_cpu.pbtxt",
    register_as = "MultiHandRendererSubgraph",
    deps = [
        "@mediapipe//mediapipe/calculators/core:begin_loop_calculator",
        "@mediapipe//mediapipe/calculators/core:end_loop_calculator",
        "@mediapipe//mediapipe/calculators/util:annotation_overlay_calculator",
        "@mediapipe//mediapipe/calculators/util:detections_to_render_data_calculator",
        "@mediapipe//mediapipe/calculators/util:landmarks_to_render_data_calculator",
        "@mediapipe//mediapipe/calculators/util:rect_to_render_data_calculator",
    ],
)

mediapipe_simple_subgraph(
    name = "hand_detection_gpu",
    graph = "hand_detection_gpu.pbtxt",
    register_as = "HandDetectionSubgraph",
    deps = [
        "@mediapipe//mediapipe/calculators/image:image_properties_calculator",
        "@mediapipe//mediapipe/calculators/image:image_transformation_calculator",
        "@mediapipe//mediapipe/calculators/tflite:ssd_anchors_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_converter_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_custom_op_resolver_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_inference_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_tensors_to_detections_calculator",
        "@mediapipe//mediapipe/calculators/util:detection_label_id_to_text_calculator",
        "@mediapipe//mediapipe/calculators/util:detection_letterbox_removal_calculator",
        "@mediapipe//mediapipe/calculators/util:detections_to_rects_calculator",
        "@mediapipe//mediapipe/calculators/util:non_max_suppression_calculator",
        "@mediapipe//mediapipe/calculators/util:rect_transformation_calculator",
    ],
)

mediapipe_simple_subgraph(
    name = "multi_hand_detection_gpu",
    graph = "multi_hand_detection_gpu.pbtxt",
    register_as = "MultiHandDetectionSubgraph",
    deps = [
        "@mediapipe//mediapipe/calculators/core:begin_loop_calculator",
        "@mediapipe//mediapipe/calculators/core:clip_vector_size_calculator",
        "@mediapipe//mediapipe/calculators/core:end_loop_calculator",
        "@mediapipe//mediapipe/calculators/image:image_properties_calculator",
        "@mediapipe//mediapipe/calculators/image:image_transformation_calculator",
        "@mediapipe//mediapipe/calculators/tflite:ssd_anchors_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_converter_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_custom_op_resolver_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_inference_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_tensors_to_detections_calculator",
        "@mediapipe//mediapipe/calculators/util:detection_label_id_to_text_calculator",
        "@mediapipe//mediapipe/calculators/util:detection_letterbox_removal_calculator",
        "@mediapipe//mediapipe/calculators/util:detections_to_rects_calculator",
        "@mediapipe//mediapipe/calculators/util:non_max_suppression_calculator",
        "@mediapipe//mediapipe/calculators/util:rect_transformation_calculator",
    ],
)

mediapipe_simple_subgraph(
    name = "hand_landmark_gpu",
    graph = "hand_landmark_gpu.pbtxt",
    register_as = "HandLandmarkSubgraph",
    deps = [
        "@mediapipe//mediapipe/calculators/core:split_normalized_landmark_list_calculator",
        "@mediapipe//mediapipe/calculators/core:split_vector_calculator",
        "@mediapipe//mediapipe/calculators/image:image_cropping_calculator",
        "@mediapipe//mediapipe/calculators/image:image_properties_calculator",
        "@mediapipe//mediapipe/calculators/image:image_transformation_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_converter_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_custom_op_resolver_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_inference_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_tensors_to_classification_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_tensors_to_floats_calculator",
        "@mediapipe//mediapipe/calculators/tflite:tflite_tensors_to_landmarks_calculator",
        "@mediapipe//mediapipe/calculators/util:detections_to_rects_calculator",
        "@mediapipe//mediapipe/calculators/util:landmark_letterbox_removal_calculator",
        "@mediapipe//mediapipe/calculators/util:landmark_projection_calculator",
        "@mediapipe//mediapipe/calculators/util:landmarks_to_detection_calculator",
        "@mediapipe//mediapipe/calculators/util:rect_transformation_calculator",
        "@mediapipe//mediapipe/calculators/util:thresholding_calculator",
        "@mediapipe//mediapipe/graphs/hand_tracking/calculators:hand_landmarks_to_rect_calculator",
    ],
)

mediapipe_simple_subgraph(
    name = "multi_hand_landmark_gpu",
    graph = "multi_hand_landmark.pbtxt",
    register_as = "MultiHandLandmarkSubgraph",
    deps = [
        ":hand_landmark_gpu",
        "@mediapipe//mediapipe/calculators/core:begin_loop_calculator",
        "@mediapipe//mediapipe/calculators/core:end_loop_calculator",
        "@mediapipe//mediapipe/calculators/util:filter_collection_calculator",
    ],
)

mediapipe_simple_subgraph(
    name = "renderer_gpu",
    graph = "renderer_gpu.pbtxt",
    register_as = "RendererSubgraph",
    deps = [
        "@mediapipe//mediapipe/calculators/util:annotation_overlay_calculator",
        "@mediapipe//mediapipe/calculators/util:detections_to_render_data_calculator",
        "@mediapipe//mediapipe/calculators/util:labels_to_render_data_calculator",
        "@mediapipe//mediapipe/calculators/util:landmarks_to_render_data_calculator",
        "@mediapipe//mediapipe/calculators/util:rect_to_render_data_calculator",
    ],
)

mediapipe_simple_subgraph(
    name = "multi_hand_renderer_gpu",
    graph = "multi_hand_renderer_gpu.pbtxt",
    register_as = "MultiHandRendererSubgraph",
    deps = [
        "@mediapipe//mediapipe/calculators/core:begin_loop_calculator",
        "@mediapipe//mediapipe/calculators/core:end_loop_calculator",
        "@mediapipe//mediapipe/calculators/util:annotation_overlay_calculator",
        "@mediapipe//mediapipe/calculators/util:detections_to_render_data_calculator",
        "@mediapipe//mediapipe/calculators/util:landmarks_to_render_data_calculator",
        "@mediapipe//mediapipe/calculators/util:rect_to_render_data_calculator",
    ],
)
