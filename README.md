# Computer-Graphics


# Tonemapping

**Exposure** - the amount of light that is captured, depends on the scene luminance, if a scene is brigheter, then more light will reach the camera film/sensor, increasing exposure.

**HDR** is high dynamic range - a photo has more dynamic range in it than any camera can capture in a single shot so to create a real HDR image, take two or three more photos, at different exposure values, typically one frame will be at sort of a center exposure, which would be maybe what you considered a proper exposure. The rest of the exposures are over or lower exposure - to capture the highlights and shadows of the photoes- The photos are then combined to make the final HDR image.

**Tonemapping** -  is convert the tonal range from a high range to a low range. This is because most standard display devices such as a monitor can only reproduce a low range of dynamic values. So make image that has a HDR image to display devices on standard devices so that the image looks realistic.

A camera cannot capture a full dynamic range of a scene in a single exposure so we capture a bracket set of different exposure levels and we merge them together to make an HDR photo.
The HDR result needs to be reproduced on a lower dynamic range display for viewing. This lets you see the details in both the highlights and shadows (repordiviihng the dynamic range that was originally captured) -2 0 2, merged and tonemap.

base layer HDR image - more contrast between bright and dark spots is and HDR photo - to experience the etire range of light that is experienced by the human eye more than so you could ever capture in a single exposure with your camera.

![image](https://user-images.githubusercontent.com/48233453/151075573-bc1bd445-6516-494f-8d2d-7580b3c677b6.png)
Therefore, an HDR image is encoded in a format that allows the largest range of values, e.g. floating-point values stored with 32 bits per color channel.
HDR stands for High Dynamic Range and refers to the contrast or color range between the lightest and darkest tones in an image.
- Wider color gamut and contrast range than Standard Dynamic Range (SDR).
- Bright tones are made brighter without overexposing. Dark tones are made darker without underexposing.

![image](https://user-images.githubusercontent.com/48233453/151076488-e4f08532-07ec-46da-a8ac-00ad8ea2a7e8.png)



## https://graphics.cs.utah.edu/courses/cs4600/fall2021/





# Voxel
A voxel is a unit of graphic information that defines a point in three-dimensional space. Since a pixel (picture element) defines a point in two dimensional space with its X and Y coordinates , a third z coordinate is needed. In 3-D space, each of the coordinates is defined in terms of its position, color, and density.

The difference between a pixel and a voxel is that a pixel is a square inside of a 2D image with a position in a 2D grid and a single color value, whereas a voxel is a cube inside of a 3D model that contains a position inside a 3D grid and a single color value.

![image](https://user-images.githubusercontent.com/48233453/156168348-b0f52e71-7225-44d7-9a4a-a50fc84c109b.png)


## Data Storage Format
1) Store in hard disk directly in the format of images / video frames.
2) Make LMDB, which could accelerate the IO and decompression speed during training.
3) memcached is also supported, if they are installed (usually on clusters).

##### LMDB Description
- During training, we use LMDB to **speed up the IO and CPU decompression. **(During testing, usually the data is limited and it is generally not necessary to use LMDB). The acceleration depends on the configurations of the machine, and the following factors will affect the speed:
- **Some machines will clean cache regularly, and LMDB depends on the cache mechanism**. Therefore, if the data fails to be cached, you need to check it. After the command free -h, the cache occupied by LMDB will be recorded under the buff/cache entry.
- Whether the memory of the machine **is large enough to put the whole LMDB data in**. If not, it will affect the speed due to the need to constantly update the cache.
If you cache the LMDB dataset for the first time, it may affect the training speed. So before training, you can enter the LMDB dataset directory and cache the data by: cat data.mdb > /dev/nul.

# Residuals
![image](https://user-images.githubusercontent.com/48233453/176226975-aeaf0993-797c-4c6a-a6f3-a292c5232aa6.png)

# Pixel Shuffle
![image](https://user-images.githubusercontent.com/48233453/176227137-8f7b3a95-1111-47b7-8aef-6c577ce8ac4d.png)

# Back Propogatoin through time
![image](https://user-images.githubusercontent.com/48233453/176227773-3bcf6fc4-1ed9-4742-ba5b-1491fdcf2513.png)
