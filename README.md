# OBS Replay Buffer Guide
## Quick Few Notes

ShadowPlay replacement using OBS Replay Buffer because Shadowplay sucks ass.

Only use this guide if you have an NVidia GPU because this replies on the NVENC chip on the GPU.

AMD card probably work but I dont know much or if they have their own encoding chip.

https://x.com/nuttylmao/status/1811421731904774386 

Neat OBS trick to automatically orgainze clips. By default all clips will just be sent to a single folder. This will sort clips by date into new folders. Added to settings guide.


## List of some issues I've encountered and solved since using Replay Buffer

1. DO NOT change the volume of OBS in your volume mixer. It is tied to how much volume OBS is capturing. Leave it at 100% or else your recording audio will be extremely quiet.

2. This will be a non-issue for most people but it was an issue for me since I'm on a 1440p ultrawide. I was recording with replay buffer on OBS at 1440p and streaming to Discord in 1440p. This used up over 100% of my GPU Encoder and my replay buffer stopped working. Discord was using 90% of my GPU Encoder and OBS was using 50%. I solved this by scaling down my resolution in OBS to 1080p and stream to discord in 1080p. This reduced the usage to 30% for OBS and 50% for Discord now the total being under 100% making both work perfectly fine. As I mentioned earlier this will be a non-issue for most people since most people have 1080p 16:9 monitors.



## Guide Basis
<https://github.com/MFGAVIN/OBS-Alternative-to-Shadowplay> 

<https://github.com/StuckInLimbo/OBS-ReplayBuffer-Setup>

## OBS DL Link
<https://obsproject.com/download>

## Scripts and Plugins Sources
OBS Buffer Capture Sound.lua = <https://gist.github.com/snakecase/e816384a071cec31efbb4b9e429c108d>

OBS Buffer Clear.lua = <https://obsproject.com/forum/threads/smarter-replay-buffer-options.156347/post-649470/>

OBSPlay.lua = <https://github.com/lolepop/obsplay>

OBS replay buffer Folders.lua = <https://obsproject.com/forum/resources/replay-buffer-folders.1667/> Will autodetect the current full screened application and automatically create a folder named after it when clipping a buffer.

<https://github.com/Meachamp/OBS-NoPreventSleep> = Stops replay buffer when sleeping computer, turns back on when computer wakes. 

C:\Program Files\obs-studio\obs-plugins\64bit

# Table of Contents
- [Installing the Scripts](https://github.com/yuwunii/ReplayBufferGuide?tab=readme-ov-file#installing-the-scripts)
	- [Installing OBS-NoPreventSleep.dll](https://github.com/yuwunii/ReplayBufferGuide/tree/main?tab=readme-ov-file#installing-obs-nopreventsleepdll)
- [Configure OBS Settings](https://github.com/yuwunii/ReplayBufferGuide?tab=readme-ov-file#configure-obs-settings)
	- [Main OBS Window](https://github.com/yuwunii/ReplayBufferGuide?tab=readme-ov-file#main-obs-window)
	- [General](https://github.com/yuwunii/ReplayBufferGuide?tab=readme-ov-file#general)
	- [Output](https://github.com/yuwunii/ReplayBufferGuide?tab=readme-ov-file#output)
		- [Recording](https://github.com/yuwunii/ReplayBufferGuide?tab=readme-ov-file#recording)
		- [Audio](https://github.com/yuwunii/ReplayBufferGuide?tab=readme-ov-file#audio)
		- [Replay Buffer](https://github.com/yuwunii/ReplayBufferGuide?tab=readme-ov-file#replay-buffer)
	- [Audio](https://github.com/yuwunii/ReplayBufferGuide?tab=readme-ov-file#audio-1)
	- [Video](https://github.com/yuwunii/ReplayBufferGuide?tab=readme-ov-file#video)
	- [Hotkeys](https://github.com/yuwunii/ReplayBufferGuide?tab=readme-ov-file#hotkeys)
	- [Advanced](https://github.com/yuwunii/ReplayBufferGuide?tab=readme-ov-file#advanced)
- [How to Make OBS Replay Buffer run on its own on Start Up](https://github.com/yuwunii/ReplayBufferGuide?tab=readme-ov-file#how-to-make-obs-replay-buffer-run-on-its-own-on-start-up)
	- [General](https://github.com/yuwunii/ReplayBufferGuide?tab=readme-ov-file#general-1)
	- [Triggers](https://github.com/yuwunii/ReplayBufferGuide?tab=readme-ov-file#triggers)
	- [Actions](https://github.com/yuwunii/ReplayBufferGuide?tab=readme-ov-file#actions)
	- [Settings](https://github.com/yuwunii/ReplayBufferGuide?tab=readme-ov-file#settings)
	- [Fixing Priority (Optional)](https://github.com/yuwunii/ReplayBufferGuide?tab=readme-ov-file#fixing-priority-optional)

# Installing the Scripts
Click [here](https://github.com/yuwunii/ReplayBufferGuide/releases/download/v0w0/Buffer.Replay.Scripts.7z) to download the Replay Buffer Scripts

Extract then place the "Buffer Replay Scripts" folder in "C:\Program Files\obs-studio\data\obs-plugins\frontend-tools\scripts"

![image](https://github.com/user-attachments/assets/4fb9d8ab-d7b6-47d7-a800-ace89daeef56)


- Open OBS. Click on "Tools" on the top bar then click on "Scripts"

- Click on the + sign, Navigate to the "replay buffer Scripts" folder and add which scripts you want to use.

1. **OBS Buffer Capture Sound.lua** = Plays a sound when you capture a replay buffer. You can replace the sound but the file has to be named "sound.wav". I also advise to use Audacity to adjust the sound to be higher or lower.

2. **OBS Buffer Clear.lua** = By default if you capture, for example, the last 10 minutes but you capture again 3 minutes later it will still capture the last 10 minutes including the clipped part you already captured. This script changes that and makes it funtions the same as ShadowPlay.
  
3. **OBSPlay.lua** = Create a scene for every game you want to have a folder for and clips will get sorted into those. Refer to this guide https://github.com/MFGAVIN/OBS-Alternative-to-Shadowplay/tree/main?tab=readme-ov-file#OBSPlay

Use OBSPlay if you aren't going to use the sort into folders trick. https://x.com/nuttylmao/status/1811421731904774386

or don't use either have have all your clips in a single folder.


## Installing OBS-NoPreventSleep.dll
To make OBS Replay Buffer function more like ShadowPlay you can download this .dll and it will stop replay buffer when you sleep your computer and automatically turn it back on when you wake it up.

<https://github.com/Meachamp/OBS-NoPreventSleep/releases/tag/v0.3>

- Download the .zip in the release here and extract the .dll.
  
- Place the .dll in "C:\Program Files\obs-studio\obs-plugins\64bit"

- Thats all. You can turn on replay buffer then try sleeping your PC. If it goes to sleep then it worked.


# Configure OBS Settings

Settings to change and copy. If a setting is not mentioned then ignore unless you want to change it.

## Main OBS Window
Setting up basic settings

- Create a Scene and name it whatever you want
- Add a new source and pick Display Capture
  - This will be the main thing Replay Buffer will capture. Add new sources to have OBS capture specific things as needed.

- Click the Gear under Audio Mixer
  - This is where you can control the gain on your own microphone and desktop audio if needed.

- Scene transition: switch between Fade and Cut if you want

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
  - Rescale Output = Disabled (DO NOT TOUCH)
  - Custom Muxer Settings = Empty
  - Automatic File Splitting = Unchecked
- Encoder Settings
  - Rate Control = CQP
  - CQ Level = 20 (anywhere between 14-21. Lower = Better Quality, Larger File Size. Higher = Lower Quality, Lower File Size)
  - Keyframe Interval = 2
  - Preset = P5
  - Tuning  = High Quality
  - Multipass Mode = Single Pass
  - Profile = main
  - Look Ahead = Unchecked
  - Psycho Visual Tuning = Checked
  - GPU = 0
  - Max B-frames = 2

![image](https://github.com/user-attachments/assets/7b579542-38da-412e-a217-add32478f5a4)

### Audio
-Set all audio bitrate to 160

![image](https://github.com/user-attachments/assets/d7ea2f5d-516e-412c-bfd0-2a8a1fa6fa84)

### Replay Buffer
  - Enable Replay Buffer = Checked
  - Maximum Replay Time = in seconds (however long you want)
  - Maximum Memory = in MB (temp recordings are saved to RAM instead of storage)
    - This sets the limit on how large the file size will be.
    - If you set the replay time to 10 minutes but the file limit to 2048 MB, the video file will only record up to 2GB worth of video and if it hits that data limit before the 10 minute mark the video file could be less than 10 minutes.
    - ex. I set 10 minutes as my maximum and 4096 MB but the recording hit the memory limit first and the recording I took was only 6 minutes long.
- Here is a rule of thumb to go by. Increase the Memory Limit as needed. Just know it will take RAM space.
  - 5 Minutes = 300s = 2048 MB
  - 10 Minutes = 600s = 4096 MB
  - 15 Minutes = 900s = 6144 MB
  - 20 Minutes = 1200s = 8192 MB
- There is no option to record temp data to disk (like how Shadowplay does it) instead of RAM
- Real life example on how this works
  - I have my limits set to 20 minutes and 4096MB (4GB) memory limit.
  - When I play a game like Valorant there is a lot of stuff moving on screen that uses up the memory limit fast and the clip would end up being around 5-10 minutes at 4GB. Hitting the memory limit first.
  - When I'm watching stuff on Discord theres less moving stuff taking the memory and the clip would record the full 20 minutes and the file only being around 2GB large. Hitting the time limit first.

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
- Downscale Filter = Bicubic. If no option then just leave as is.
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
  - Filename Formatting = %CCYY-%MM-%DD\%CCYY-%MM-%DD %hh-%mm-%ss
    - This will make it so a new folder gets created every day for easier orginazation 
    - Leave as is if you are going to use OBSPlay. Unsure if it works together.
  - Overwrite if file exists = Unchecked


![image](https://github.com/user-attachments/assets/51267aa0-466f-4a1b-ac2c-61382f61b9e6)

# How to Make OBS Replay Buffer run on its own on Start Up
- Open Start Menu, type Task Scheduler and open it.
- Click on "Create Task..."

## General
- Name it anything
- Run with highest privilages = checked

![image](https://github.com/user-attachments/assets/2a61fc1b-74d4-4b9a-97b9-61f3ffa4500c)

## Triggers
- Click "New..."
- Begin the task: = At log in
- Pick Any user or Specific User
- Enabled = checked
- Click "OK"

![image](https://github.com/user-attachments/assets/1e0c04d7-f64f-4f95-bcc1-8f640f28c4c8)


## Actions
- Click "New..."
- Action: Start a program
- Program/Script = "C:\Program Files\obs-studio\bin\64bit\obs64.exe"
  - (has to be obs64.exe)
- Add arguments: = --startreplaybuffer --minimize-to-tray
  - (Remove minimize to tray if you want)
- Start in = C:\Program Files\obs-studio\bin\64bit\
  - VERY IMPORTANT:  Copy exactly that without any "quotations" and make sure the \ is at the end
  - If obs64.exe is on a diffrent drive or path you just need to put the folder path that obs64.exe is in
- Click "OK"

![image](https://github.com/user-attachments/assets/82299acf-03c9-44e1-be23-ef64c50c51e8)


## Settings
- Allow task to be run on demand = checked
- Stop task if its runs longer than: = unckeck
- Click "OK"

![image](https://github.com/user-attachments/assets/1620efb0-fff3-4f55-8780-e8175bebb1c6)


At this point close OBS then right click the task and click run. OBS should run and appear with a red dot on your systen tray. Open it and see if Replay Buffer is running the the button is blue. At this point you are all set up.

## Fixing Priority (Optional)
Task Scheduler gives all tasks a low priority and limits drive speed. I don't know if this negatively affects replay buffer but I'll add this anyways
- Highlight the task you just created
- Click "Export..."
- Save to anywhere (desktop)
- Open file with Notepad
- Ctrl+F "Priority"
- Look for <Priority>7</Priority>
- Replace the 7 with a 4
- Save file
- Go back to Task Scheduler
- Delete the OBS task you created
- Import the new task you just edited
