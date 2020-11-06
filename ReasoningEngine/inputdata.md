# **输入数据**

## **对输入图像进行格式转换（NCHW->NHWC）**
```c++
int hw = image_widht * image_height;
int index = 0;
for (int w = 0; w < image_width; w ++)
    {
        for (int h = 0; h < image_height ;h++)
        {
            for (int c= 0 ; c < image_channel; c++)
            {
                send_im[c * hw + w * image_height + h] = (float)img[index];
                index++;
            }
        }
    }
```

## **对输入图像进行格式转换并归一化（NCHW->NHWC）**
```c++
int hw = image_widht * image_height;
int index = 0;
for (int w = 0; w < image_width; w ++)
    {
        for (int h = 0; h < image_height ;h++)
        {
            for (int c= 0 ; c < image_channel; c++)
            {
                send_im[c * hw + w * image_height + h] = ((float)img[index] - mean_vals[c]) * norm_vals[c];
                index++;
            }
        }
    }
```

## **设置输入**
```c++
/*!
 * @brief Set the buffer of the tensor.
 *    A tensor may deny to change its internal buffer setting.
 *
 * @param [in] tensor: The tensor handle.
 * @param [in] buffer: The buffer address.
 * @param [in] buffer_size: The buffer_size.
 *
 * @return 0: Success; -1: Fail.
 * @note  The buffer is still managed by caller.
 */
int set_tensor_buffer(tensor_t tensor, void* buffer, int buffer_size);
```

## **完整代码**
```c++
// 输入数据
float* send_im = new float[image_width * image_height * image_channel];
int hw = image_width * image_height;
int index = 0;
// NCHW->NHWC
for (int w = 0; w < image_width; w ++)
{
    for (int h = 0; h < image_height ;h++)
    {
        for (int c= 0 ; c < image_channel; c++)
        {
            send_im[c * hw + w * image_height + h] = ((float)img[index] - mean_vals[c]) * norm_vals[c];
            index++;
        }
    }
}
set_tensor_buffer(input_tensor, send_im, image_width * image_height * image_channel * sizeof(float));
```