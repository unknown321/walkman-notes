# walkman-notes

If you cannot see album art on your Sony Walkman A-* series even if it is embedded into your music files, you have to make sure your album art has following configuration:

  - baseline jpeg (**not** [interlaced](https://en.wikipedia.org/wiki/Interlacing_(bitmaps))) - `$ identify -verbose cover.jpg  | grep lace`
  - png

Picture tag must be written in ISO-8859-1 encoding, not UTF8.

Mimetype - `image/jpeg` or `image/png` (probably not necessary)

Interlaced to baseline conversion:

```shell
jpegtran -perfect -copy all -optimize cover.jpg > baselined.jpg && mv cover.jpg cover_interlaced.jpg && mv baselined.jpg cover.jpg
```

You can use [kid3](https://kid3.kde.org/) to change mimetype and encoding or fiddle with command line.

---

Links to discussions on Sony forums, where I was unable to post:

https://community.sony.co.uk/t5/portable-audio/re-sony-nw-a45-walkman-missing-artwork-help/td-p/2491157/page/2

https://community.sony.co.uk/t5/portable-audio/missing-album-covers-on-new-sony-a15-walkman/td-p/1843375/page/4
