# FFmpeg

FFmpeg 是一个视频、音频处理工具。

## 录屏

```sh
ffmpeg -video_size 1920x1080 -framerate 25 -f x11grab -i :0.0+0,0 output.mp4
```

## 录音

```sh
ffmpeg -f pulse -i default output.wav
```

可使用 `pulsemixer` 设置 default 设备。

## 加速

[FFmpeg page][speed-ffmpeg]

可用于音频和视频。加速音频 1.2 倍：

```sh
ffmpeg -i input.mp3 -filter:a atempo=1.2 -vn output.mp3
```

[speed-ffmpeg]: https://trac.ffmpeg.org/wiki/How%20to%20speed%20up%20/%20slow%20down%20a%20video

## 两个视频左右拼接

```sh
ffmpeg -i input1.mov -i input2.mov -filter_complex hstack output.mov
```

需要上下拼接则将 `hstack` 改为 `vstack`。

## 连接视频

先创建一个文件

```sh
cat > inputs <<EOF
file '/path/to/input1.mp4'
file './relative/input2.mp4'
EOF
```

然后执行命令

```sh
ffmpeg -f concat -safe 0 -i inputs -c copy output.mp4
```

[更详细的文档][concat-doc]。

或者使用 bash 写一个脚本 [vidcat]。

```sh
vidcat input1.mp4 input2.mp4 -o output.mp4
```

[concat-doc]: https://trac.ffmpeg.org/wiki/Concatenate
[vidcat]: https://github.com/weirane/scripts/blob/449f1f63b65253a305b3/vidcat

## 从视频中提取音频

```sh
ffmpeg -i input.flv -vn -acodec copy output.aac
```

- `-vn`: no video
- `-acodec copy`: use the same audio stream that's already in there

## 剪裁

可用于音频和视频。

```sh
ffmpeg -ss 10 -t 6.5 -i input.mp3 output.mp3
```

从第 10 秒开始，持续 6.5 秒。

## 给视频去抖动

<https://github.com/georgmartius/vid.stab>

```sh
ffmpeg -i input.mp4 -vf vidstabdetect -f null -
ffmpeg -i input.mp4 -vf vidstabtransform,unsharp=5:5:0.8:3:3:0.4 output.mp4
```
