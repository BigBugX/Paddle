cc_library(anakin_op_converter SRCS fc.cc conv2d.cc conv2d_fusion.cc
elementwise.cc activation.cc pool2d.cc concat.cc split.cc relu.cc softmax.cc
batch_norm.cc reshape.cc flatten.cc transpose.cc density_prior_box.cc
detection_out.cc scale.cc dropout.cc im2sequence.cc sum.cc affine_channel.cc
roi_align.cc shuffle_channel.cc helper.cc DEPS anakin_engine framework_proto
scope op_registry gtest)

cc_test(test_anakin_fc SRCS test_fc_op.cc DEPS anakin_op_converter mul_op SERIAL)
cc_test(test_anakin_conv2d SRCS test_conv2d_op.cc DEPS anakin_op_converter conv_op im2col vol2col depthwise_conv SERIAL)
cc_test(test_anakin_activation SRCS test_activation_op.cc DEPS activation_op anakin_op_converter SERIAL)
cc_test(test_anakin_pool2d SRCS test_pool2d_op.cc DEPS anakin_op_converter pool_op pooling SERIAL)
cc_test(test_anakin_concat SRCS test_concat_op.cc DEPS anakin_op_converter concat_op concat_and_split SERIAL)
cc_test(test_anakin_split SRCS test_split_op.cc DEPS anakin_op_converter split_op concat_and_split SERIAL)
cc_test(test_anakin_elementwise SRCS test_elementwise_op.cc DEPS anakin_op_converter elementwise_add_op elementwise_mul_op SERIAL)
cc_test(test_anakin_relu SRCS test_relu_op.cc DEPS activation_op anakin_op_converter SERIAL SERIAL)
cc_test(test_anakin_softmax SRCS test_softmax_op.cc DEPS anakin_op_converter softmax_op softmax SERIAL)
cc_test(test_anakin_reshape SRCS test_reshape_op.cc DEPS anakin_op_converter reshape_op SERIAL)
cc_test(test_anakin_flatten SRCS test_flatten_op.cc DEPS anakin_op_converter flatten_op reshape_op SERIAL)
cc_test(test_anakin_transpose SRCS test_transpose_op.cc DEPS anakin_op_converter transpose_op SERIAL)
cc_test(test_anakin_batch_norm SRCS test_batch_norm_op.cc DEPS anakin_op_converter batch_norm_op SERIAL)
cc_test(test_anakin_dropout SRCS test_dropout_op.cc DEPS anakin_op_converter dropout_op SERIAL)
cc_test(test_anakin_sum SRCS test_sum_op.cc DEPS  anakin_op_converter sum_op selected_rows_functor SERIAL)
cc_test(test_anakin_affine_channel SRCS test_affine_channel_op.cc DEPS anakin_op_converter affine_channel_op SERIAL)
