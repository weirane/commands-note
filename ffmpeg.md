# FFmpeg

FFmpeg 是一个视频、音频处理工具。

## 录屏

```sh
ffmpeg -video_size 1920x1080 -framerate 25 -f x11grab -i :0.0+0,0 output.mp4
```

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
