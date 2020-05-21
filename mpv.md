# mpv

mpv 是一个媒体播放器。

## 播放

    mpv file.mp4
    mpv https://example.com/video.mp4

## 摄像头

    mpv av://v4l2:/dev/video0 --profile=low-latency --untimed

## 不使用终端控制器

    mpv --player-operation-mode=pseudo-gui file.mp4

## 快捷键

- Space 暂停/播放
- `←` 后退 5 秒
- `→` 前进 5 秒
- `↓` 后退 1 分钟
- `↑` 前进 1 分钟
- `9` 增大音量
- `0` 减小音量
- `m` 切换静音
- `[` 减速播放
- `]` 加速播放
- Backspace 还原播放速度

更多的快捷键见 `man mpv`。
