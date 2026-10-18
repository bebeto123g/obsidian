
Изменение размера одного изображения
```bash
convert name.jpg -resize WIDTHxHEIGTH output.jpg
```

Изменение всех .jpg в директории в цикле for
```bash
for i in *.jpg; do convert "$i" -resize WIDTHxHEIGTH "out-$1"; done
```