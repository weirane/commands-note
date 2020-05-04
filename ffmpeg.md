# ffmpeg

Ffmpeg 是一个视频处理工具。

## 录屏

```sh
ffmpeg -video_size 1920x1080 -framerate 25 -f x11grab -i :0.0+0,0 output.mp4
```

## 两个视频左右拼接

```sh
ffmpeg -i input1.mov -i input2.mov -filter_complex hstack output.mov
```

需要上下拼接则将 `hstack` 改为 `vstack`。

## 给视频去抖动

<https://github.com/georgmartius/vid.stab>

```sh
ffmpeg -i input.mp4 -vf vidstabdetect -f null -
ffmpeg -i input.mp4 -vf vidstabtransform,unsharp=5:5:0.8:3:3:0.4 output.mp4
```
