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
HDR stands for High Dynamic Range and refers to the contrast or color range between the lightest and darkest tones in an image
