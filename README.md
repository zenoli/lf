# lf Config
My config for the lf file manager

## Dependencies

### For image previews

* `ueberzug`
* `ffmpegthumbnailer`
* `ImageMagick`
* `poppler`
* `epub-thumbnailer`
* `wkhtmltopdf`
* `bat` (optional - color highlight for text files)
* `chafa` (optional - for image preview over SSH or inside Wayland session)
* `unzip` (optional - for .zip and .jar files)
* `7z` (optional - for .7z files)
* `unrar` (optional - for .rar files)
* `catdoc` (optional - for .doc files)
* `docx2txt` (optional - for .docx files)
* `odt2txt` (optional - for .odt and *.ods files)
* `gnumeric` (optional - for .xls and .xlsx files)
* `exiftool` (optional - for music files)
* `iso-info` (optional - for .iso files)
* `transmission` (optional - for .torrent files)
* `mcomix` (optional - for .cbz and .cbr files)

### For drag and drop:
* `dragon`

## Setup

1. Clone this repo to ~/.config/lf
2. run `make install`. This installs the `lf` wrapper-script `lfrun` into `$PATH`.
3. Copy the following function to your .bashrc/.zshrc:
```
function lfcd {
    tmp="$(mktemp)"
    lfrun -last-dir-path="$tmp" "$@"
    if [ -f "$tmp" ]; then
        dir="$(cat "$tmp")"
        rm -f "$tmp"
        if [ -d "$dir" ]; then
            if [ "$dir" != "$(pwd)" ]; then
                cd "$dir"
            fi
        fi
    fi
}
```

## Uninstall

Run `make uninstall` to remove `lfrun` from `$PATH`.
