# Steganography 1

> Resources : https://bobbyluig.gitbooks.io/csc-learn/content/forensics/steg1/steg1.html

Steganography is the art of hide information. 

## Image Steganography

JPEG (extension .jpg) uses lossy compression methods to make the image size smaller. It is the most common format for photos and pictures. JPEG supports 8-bit grayscale to 24-bit color images. The quality of JPEGs slowly decrease the more times you edit it and save it.

GIF (extension .gif) is limited to 8-bit (256 colors). But hey, it supports animation.

BMP (extension .bmp) is Microsoft Window's graphic file format. BMPs are not compressed.

PNG (extension .png) is the alternative to GIF. It supports 8-bit (with optional transparency), 24-bit, or even 48-bit (which becomes 64-bit with the alpha channel). PNGs are widely used due to it's transparency capability.


## Color Depth

8-bit, 24-bit, and 48-bit refer to the color depth of the image.<br>
color depth only go as low as 8-bit (or 1 byte).<br>

<p>Most image formats store colors in an additive format, making the primary colors red, green, and blue. From now on, they will be referred to as R, G, and B.</p>

<p>For 8-bit images, that one byte has to store all three values (thus the horrific 256 colors). 24-bit JPGs use one byte for each R, G, and B color value. I hope you have now made the connection that it's called 24-bit because 3*8 = 24. PNGs and other transparency capable formats are slightly different. They can have an addition alpha channel (A) that defines the opacity of the pixel. R, G, B, and A makes a PNG 32-bit. Finally, we have the ultra high 48-bit and 64-bit color depths. Those contain millions of colors because each R, G, B, and A value take up 2 bytes (16 bits) rather than 1 byte. This is detailed below.</p>

```
8-bit:
(R + G + B) = 8 bits
R = 3 bits
G = 3 bits
B = 2 bits
Transparency extra.
Total of 256 colors.

16-bit:
(R + G + B + A) = 16 bits
Each 4 bits.
Transparency optional.
Total of 4096 colors and 16 levels of transparency.

24-bit:
(R + G + B) = 24 bits
Each 8 bits.
No transparency.
Total of 16777216 colors.

32-bit:
(R + G + B + A) = 32 bits
Each 8 bits.
Transparency optional.
Total of 16777216 colors and 256 levels of transparency.

48-bit:
(R + G + B) = 48 bits
Each 16 bits.
No transparency.
Total of 4096^3 colors.

64-bit:
(R + G + B + A) = 64 bits
Each 16 bits.
Transparency optional.
Total of 4096^3 colors and 4096 levels of transparency.
```


## Least Significant Bit

The least significant bit (LSB) is the most important when it comes to steganography. Why is it called "least significant" then? The LSB is the last or trailing bit in a byte. Changing the LSB would make no significant changes to the image data. 

<p>all we need to is convert it into binary and replace the LSB of each R, G, B, (or A) with a bit of the data.</p>