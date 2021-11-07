---
title: "ASCII Art -Image to ASCII Converter- "
date: 2021-11-07T14:27:24+01:00
draft: flase
---
## Introduction
**ASCII art** is the forming pictures or art out of the ASCII's printable characters. 

|input|output|         
|----------------|-------------------------------|
| ![blender](/img/ascii_art/blender.jpg) |![blenderAscii](/img/ascii_art/blenderascii.jpg) |


**ASCII art** is used wherever text can be more **readily printed** or **transmitted** than graphics, or in some cases, where the transmission of pictures is not possible. This includes printers, old phones or even **Google meet** and **twitch**  chat!

## How it works
In this article u will learn how to make a program that converts a given image to ASCII characters, using the **C++** programming language and the **SFML** Multimedia libray.


### 1. Loading the image:
```C++
  std::string inputPath="myImage.jpg";
  sf::Image img;
  img.loadFromFile(inputPath);
```

### 2. Turning the image into Greyscale:
- We consider the image as 2x2 matrix.
- we extract every pixel using a nested loop.
- We turn each pixel into black and white using the RBG colors values in the greyscale system (read about the greyscale system for better understanding).
```C++
#define RED 0.2126
#define Green 0.587
#define Blue 0.114
int grey = 0;
for (int i(0); i < img.getSize().x; i++)
 {
   for (int j(0); j < img.getSize().y; j++)
   {
     grey = img.getPixel(i, j).r * RED + img.getPixel(i, j).g * Green + img.getPixel(i, j).b * Blue;
     img.setPixel(i, j, sf::Color(grey, grey, grey));
   }
 }
```
### 3. We convert the image to a low Resolution version:
Many people can't get why we need to lower the resolution, i'll explain it using an exemple:  
If we take an image with 1920*1080px resolution and start replacing every pixel with an ASCII char the result will contain **2073600** characters and it won't fit on any screen.
That's why we need to group each "X" adjacents pixels by reducing the resolution.  
If we group each 100 horizontal pixels and 100 vertical pixels the result from the exemple above will only have 207 characters.
```C++
  int scaleX = 10; //the horizontal pixels number that an ASCII character will replace
  int scaleY = 10; //the vertical pixels number that an ASCII character will replace
  sf::Image greyLowResImg(img);
  int grey = 0;
  for (int i(0); i < img.getSize().x - scaleX; i += scaleX)
  {
    for (int j(0); j < img.getSize().y - scaleY; j += scaleY)
    {
      for (int x(0); x < scaleX; x++)
      {
        for (int y(0); y < scaleY; y++)
        {
          grey += grayImg.getPixel(i + x, j + y).r;
        }
      }
      grey /= scaleX * scaleY + 1;
      for (int x(0); x < scaleX; x++)
      {
        for (int y(0); y < scaleY; y++)
        {
          greyLowResImg.setPixel(i + x, j + y, sf::Color(grey, grey, grey));
        }
      }
    }
  }
```
### 4. We replace the lowRes image pixels with ASCII chars  
- We choose the ASCII characters that we want to use.
- We replace the pixels with the ASCII chars according to how dark the pixel is.
```c++
 //We choose the ASCII characters we want to use
 std::string ascii = "@#$=+|:. "; 
 
 std::string asciiArt;

  for (int j(0); j < greyLowResImg.getSize().y; j += scaleY)
  {
    for (int i(0); i < greyLowResImg.getSize().x; i += scaleX)
    {
      asciiArt += ascii[(int)(greyLowResImg.getPixel(i, j).r / 255.f * ascii.size())];
    }
    asciiArt += "\n";
  }
```
## Conclusion 
This project was very interesting, i learned how to manipulate images at the lower level, i understood how filters work and how to convert an image to Greyscale.
I used it to troll my classmates during the online classes by sending ASCII arts in the chat.

You can find the entire [source code](https://github.com/muhammedBkf/JPGtoASCII_converter) here.