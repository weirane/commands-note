# Imagemagick

Imagemagick 是一个图像处理工具。

## 转换格式

```sh
convert input.png output.jpg
```

## 剪裁

```sh
convert -crop 800x600+10+10 input.png output.png
```

## 剪裁白色区域

```sh
convert input.png -trim output.png
```

## 将白色区域变为透明

```sh
convert input.png -transparent white output.png
```

## 将外侧的白色区域变为透明

```sh
convert input.png -fill none -draw 'color 1,1 floodfill' output.png
```
