### Setup

```
sudo curl -L https://yt-dl.org/downloads/latest/youtube-dl -o /usr/local/bin/youtube-dl
sudo chmod a+rx /usr/local/bin/youtube-dl
sudo apt install ffmpeg
```

### Example Command:

```
youtube-dl -u user@email.com -p password --download-archive playlist.txt "https://www.youtube.com/playlist?list=XXXXXXXXXXXXXXXX" -f 'bestvideo[ext=mp4]+bestaudio[ext=m4a]/best[ext=mp4]/best' -o '%(title)s.%(ext)s' --restrict-filenames
```
