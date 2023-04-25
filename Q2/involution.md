## CONVOLUTION VS INVOLUTION

_general idea:_ The convolution and involution act on different spaces. The convolution works within the specific feature map with a single kernel applied to the whole filter, while the involution has different kernels for each pixel in the image, but are matched across all the feature maps

**Convolutions Review:**
 * Involve multiple feature maps that are received from the channels on the input
 * For each channel there is one kernel:
   * Kernel multiplied by each value in sliding window fashion
   * The kernel outputs for each channel on the specific feature map are summed into a single output map
 * Output maps generated based on the number of set output channels
 * Each output map is then passed as channels into the next convolutional layer


**Involutions:**
 * Convolutions - have the same kernel within the specific channel and feature map, involutions have different kernels for every pixel of the image, but the kernel is shared across all feature maps for that pixel
 * Idea of involutions: combines information across multiple channels instead of having them be isolated from each other until a simple sum at the end
 * Shows good performance by evaluating and comparins pixels among the different feature maps
 * Main difference:
   * Convolution - will learn features based on the pixels around it, but is limited in learning features based on representations of similar areas on different feature maps
   * Involution - will generate kernels based on similar locations in feature maps, which are then used to compare pixels nearby and pool

**Involution Methodology:**
 * Input: takes a specific pixel across all feature maps

1. Use a kernel generator function (neural network with pararmeters being trained over time) - creates a flattened kernel that is reshaped into a kernel (size KxKx1)
2. The created kernel is then used for the specific pixel and the pixels around it (based on kernel size) across all feature maps
   1. The kernel is mapped across the same pixel (and surrounding context) across all channels (kxkx1 * kxkx1 scaled over all channels)
3. The summed kernel output (which is of size KxKxC) is then summed across the kernel dimensions to create the output pixel (1x1xC)

 * Overall methodology: generate a kernel based on a specific pixel and its representations across feature maps, and use that to extract features based on the surrounding context along with channel comparisons

**Convolutional and Involutional Neural Networks:**
 * Both include conventional layers: pooling, batch normalization, ReLU activation
 * Involutional - uses involutions across feature maps
 * Convolution - uses convolutions within the same feature map

**Overall Difference:** The main difference between convolutions and involutions is how the kernel is created, the convolution kernel is generated over time based on backpropagation and only works on the specific feature map. Involutions use information across feature maps to create a kernel to extract features in the input