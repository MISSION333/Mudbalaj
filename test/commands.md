// https://json2video.com/how-to/ffmpeg-course/ffmpeg-extract-audio.html


ffmpeg \
    -i video1.mp4 \
    -map 0:a \
    -y output.mp3 


ffmpeg \
    -i multilingual-video.mp4 \
    -map 0:a:1 \
    -y output.mp3 

ffmpeg \
    -i multilingual-video.mp4 \
    -map 0:a:1 \
    -map 0:a:2 \
    -y output.m4a


## Extract audio from MP4 to MP3
ffmpeg \
    -i video.mp4 \
    -map 0:a \
    -y output.mp3


## Extract audio from MP4 to WAV
ffmpeg \
    -i video.mp4 \
    -map 0:a \
    -y output.wav


## Extract audio from MKV to WAV
ffmpeg \
    -i video.mkv \
    -map 0:a \
    -y output.wav


## REMOVE audio from video
ffmpeg \
    -i video1.mp4 \
    -an \
    -c copy \
    -y output.mp4 


## Add audio to video
ffmpeg -i input.mp4 -i input.mp3 -c copy -map 0:v:0 -map 1:a:0 output.mp4


## Split Audio into subAudios
ffmpeg -i <Audio>.mp3 -f segment -segment_time 30 -c copy out%03d.mp3


## Split Background Audio and Human Audio.
spleeter separate -p spleeter:2stems -o output_x/ out000.mp3


## Parallel call
parallel -j 3 spleeter separate -p spleeter:2stems -o output_x/ :::  out/out*.mp3
