# ReplayBufferGuide
## Guides
<https://github.com/MFGAVIN/OBS-Alternative-to-Shadowplay> 

<https://github.com/StuckInLimbo/OBS-ReplayBuffer-Setup>

## OBS DL Link
<https://obsproject.com/download>

## Scripts and Plugins
OBSPlay.lua = <https://github.com/lolepop/obsplay>

OBS Buffer Capture Sound.lua = <https://gist.github.com/snakecase/e816384a071cec31efbb4b9e429c108d>

OBS Buffer Clear.lua = <https://obsproject.com/forum/threads/smarter-replay-buffer-options.156347/post-649470/>

OBS Buffer Replay Folders.lua = <https://obsproject.com/forum/resources/replay-buffer-folders.1667/>

<https://github.com/Meachamp/OBS-NoPreventSleep> = (Stops buffer replay when sleeping computer, turns back on when computer wakes. Currently not working for me.)


# Installing the Scripts
- Download "Buffer Replay Scripts.7z". Extract then place the "Buffer Replay Scripts" folder in "C:\Program Files\obs-studio\data\obs-plugins\frontend-tools\scripts"

- Open OBS. Click on "Tools" on the top bar then click on "Scripts"

- Click on the + sign, Navigate to the "Buffer Replay Scripts" folder and add which scripts you want to use.

1. **OBS Buffer Capture Sound.lua** = Plays a soundbyte when you capture a buffer replay. You can replace the sound but the file has to be named "sound.wav". I also advise to use Audacity to adjust the sound to be higher or lower.

2. **OBS Buffer Clear.lua** = By default if you capture, for example, the last 10 minutes but you capture again 3 minutes later it will still capture the last 10 minutes including the clipped part you already captured. This script changes that and makes it funtions the same as ShadowPlay.

**Only pick ONE between OBS Buffer Replay Folders.lua and OBSPlay.lua**

3. **OBS Buffer Replay Folders.lua** = Automatically creates a folder based on the current fullscreen application opened. Works like how ShadowPlay creates folders per game but this script is less reliable but works.
  
4. **OBSPlay.lua** = This script does the same job as the Replay Folders script but you have to create a scene for every game you want to have a folder for instead. Refer to this guide https://github.com/MFGAVIN/OBS-Alternative-to-Shadowplay/tree/main?tab=readme-ov-file#OBSPlay

# Copy These Settings

Setting to change and copy. If setting not mentioned then ignore unless you want to change it.

## General

- System Tray
  - Enable = Checked
  - Always minimize to system tray instead of taskbar (your choice) = Checked

![image](https://github.com/user-attachments/assets/0db3426c-7851-4bea-af2b-68397eadcf71)

## Output
### Recording
  - Output Mode = Advanced
  - Type = Standard
- Recording Settings
  - Recording Path = Set to somewhere
  - Generate File Name without Space = Unchecked
  - Recoding Format = MPEG-4 (.mp4)
  - Video Encoder = NVIDIA NVENC HEVC
  - Audio Encoder = FFmpeg AAC
  - Audio Track = 1 (or how many ever you want to use)
  - Rescale Output = Disabled
  - Custom Muxer Settings = Empty
  - Automatic File Splitting = Unchecked
- Encoder Settings
  - Rate Control = CQP
  - CQ Level = 18 (anywhere between 14-21. Lower = Better Quality, Larger File Size. Higher = Lower Quality, Lower File Size)
  - Keyframe Interval = 0
  - Preset = P6
  - Tuning  = High Quality
  - Multipass Mode = Single Pass
  - Profile = main
  - Look Ahead = Unchecked
  - Psycho Visual Tuning = Checked
  - GPU = 0
  - Max B-frames = 2

![image](https://github.com/user-attachments/assets/97a456c6-d689-49b0-88a0-146b6374551a)

### Audio
-Set all audio bitrate to 160

![image](https://github.com/user-attachments/assets/d7ea2f5d-516e-412c-bfd0-2a8a1fa6fa84)

### Replay Buffer
  - Enable Replay Buffer = Checked
  - Maximum Replay Time = in seconds (however long you want)
  - Maximum Memory = in MB (temp recordings are saved to RAM instead of storage)
- Refer to this guide to choose settings
  - 5 Minutes = 300s = 2048 MB
  - 10 Minutes = 600s = 4096 MB
  - 15 Minutes = 900s = 6144 MB
  - 20 Minutes = 1200s = 8192 MB

![image](https://github.com/user-attachments/assets/5852b14d-d146-433d-9caa-3bec56118bf9)

## Audio
- General
  - Sample Rate = 48kHz
  - Channels = Stereo
- Global Audio Devices
  - Configure to your needs
- Meters
  - Decay Rate = Fast
  - Peak Meter Type = Sample Peak

![image](https://github.com/user-attachments/assets/fa7de9d6-bdde-4fec-8340-c2574b0852c9)

## Video
- Base (Canvas) Resolution = Your Native Resolution
- Output (Scaled) Resolution = Your Native Resolution
- Downscale Filter = Do Not Touch
  - Common FPS Values = 60

![image](https://github.com/user-attachments/assets/eb689d05-56e7-4970-a68d-7c4912426fce)

## Hotkeys
 - Replay Buffer = Set to whatever

![image](https://github.com/user-attachments/assets/f780dac3-53a7-422f-94cf-5a1e6a132859)

## Advanced
- General
  - Process Priority = Normal
  - Show active outputs warning on exit = Checked
- Video
  - Renderer = Direct3D 11
  - Color Format = NV12 (8-bit, 4:2:0, 2 planes)
  - Color Space = Rec. 709
  - Color Range = Limited
- Recording
  - Filename Formatting = (You can leave as is. Hover over the text box to see formats)
  - Overwrite if file exists = Unchecked


![image](https://github.com/user-attachments/assets/51267aa0-466f-4a1b-ac2c-61382f61b9e6)
