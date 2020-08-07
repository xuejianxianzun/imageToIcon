# Introduction

This is a tool for converting image into icon files, written in JavaScript.

Direct conversion locally, no need to upload image to a remote server.

# Effect

![](./snap.jpg)

# Instructions

1. Include `imageToIcon.js`.

>`imageToIcon.js` is a module that exports `{ img2ico }`.

2. Use `img2ico.convert()` to convert.

## Parameter Description

The parameter of `img2ico.convert()` is an Object:

```
{
  source: string | File
  size: SizeNumber[]
  shape:'square' |'circle' |'fillet'
  bleed: boolean
}

// Type declaration:
type SizeNumber = 16 | 32 | 48 | 96 | 128 | 256 | 512
```

-`source` The url of the image, or a image file. (If image url is used, please pay attention to the impact of cross-domain policy)
-`size` size, multiple sizes can be used at the same time. You can also use custom sizes.
-`shape` shapes: square, circle, rounded square
-`bleed` blank-leaving, only effective when the shape is rounded rectangle, can make some white space around the picture.

## Output

After the conversion is successful, the Blob object of the icon file is returned.

This tool will not download files. You can use `URL.createObjectURL(blob)` to generate the URL of the file and download it yourself.

## other instructions

1. The generated icon is always square (length and width are equal). If the length and width of the picture are not equal, the narrow side will be used as the benchmark, and a square will be cropped from the narrow side.

2. The generated icon can contain icons of various sizes. The icons are all 32-bit png image.