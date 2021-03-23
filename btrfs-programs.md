# 一些好用的 Btrfs 相关的程序

## [compsize][]

查看 `/` 的压缩类型和压缩前后的大小

```sh
sudo compsize /
```

[compsize]: https://github.com/kilobyte/compsize

## [btrfs-heatmap][]

查看 `/mountpoint` 的 heatmap

```sh
sudo btrfs-heatmap /mountpoint
```

[btrfs-heatmap]: https://github.com/knorrie/btrfs-heatmap

## [btrfs-list][]

查看树形的 snapshot 列表

```sh
sudo btrfs quota enable /
# 等待 quota rescan
sudo btrfs-list
sudo btrfs quota disable /
```

[btrfs-list]: https://github.com/speed47/btrfs-list
