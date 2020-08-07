# 介绍

这是一个把图片转换成 icon 文件的工具，使用 JavaScript 编写。

在本地直接转换，无需将图片上传到远程服务器。

# 效果

![](./snap.jpg)

# 使用方法

1. 引入 `imageToIcon.js` 。

>`imageToIcon.js` 是一个模块，导出 `{ img2ico }`。

2. 使用 `img2ico.convert()` 进行转换。

## 参数说明

`img2ico.convert()` 的参数是一个 Object：

```
{
  source: string | File
  size: SizeNumber[]
  shape: 'square' | 'circle' | 'fillet'
  bleed: boolean
}

// Type declaration:
type SizeNumber = 16 | 32 | 48 | 96 | 128 | 256 | 512
```

- `source` 图片的 url，或者一个图片文件。（如果使用了图片 url，请注意跨域策略的影响）
- `size` 尺寸，可以同时使用多个尺寸。你也可以使用自定义尺寸。
- `shape` 形状，分别为：正方形、圆形、圆角正方形
- `bleed` 留白，仅当形状是圆角矩形时生效，可以使图片周围有一些留白。

## 输出

转换成功后，返回 icon 文件的 Blob 对象。

本工具不会下载文件。你可以使用 `URL.createObjectURL(blob)` 生成文件的 URL，自行下载。

## 其他说明

1. 生成的 icon 总是正方形（长和宽相等）。如果图片的长度和宽度不相等，则会以窄边作为基准，从窄边开始裁剪出一个正方形。

2. 生成的 icon 可以包含多种尺寸的图标。图标都是 32 位 png 图像。