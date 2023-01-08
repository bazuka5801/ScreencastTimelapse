# ScreencastTimelapse
The simple way for recording Timelapse's of Screencast

Supported OS: MacOS


## Mac OS (guide)

### Preparation:

1. Open `System Preferences` -> `Security` -> `Privacy` -> `Screen Recording`, and add your terminal or iTerm
<img width="400px" src="https://user-images.githubusercontent.com/11452353/211177111-75430f72-722b-4aa0-b496-9e545268e05d.png" />

2. Open `System Preferences` -> `Sound`, and turn off `Play user interface sound effects`

3. Create folder `screen` on your Desktop (After this guide you will can rename this folder or move everywhere)

4. Install `ffmpeg`, the simplest way `brew install ffmpeg`

### Guide:
1. Capture screenshots every N seconds
```bash
while :;do screencapture ~/Desktop/screen/CG--$(date "+%y-%m-%d--%H-%M-%S").png;sleep 10;done
```
P.s. press `Ctrl+C` to stop recording

2. Convert all screenshots to 60fps video
```bash
cd ~/Desktop/screen
ffmpeg -framerate 60 -pattern_type glob -i '*.png' \
  -c:v libx264 -pix_fmt yuv420p ../out.mp4
```
