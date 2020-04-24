# Youtube_subscription_manager

[![PyPI](http://img.shields.io/pypi/v/youtube-sm.svg)](http://pypi.python.org/pypi/youtube-sm/)
[![example](https://sawyerf.gitlab.io/youtube_sm/exampleshield.svg)](https://sawyerf.gitlab.io/youtube_sm/example.html)
[![docs](https://img.shields.io/static/v1?label=docs&message=master&color=brightgreen)](docs/)
[<img alt="Github" src="https://ionogy.github.io/kernel.css/GitHub-Mark.png" width="22px">](https://github.com/sawyerf/youtube-sm)
[![GitLab](https://sawyerf.gitlab.io/youtube_sm/gitlab.jpg)](https://gitlab.com/sawyerf/youtube-sm)

<p><img align='right' width=400px height=auto src='https://sawyerf.gitlab.io/youtube_sm/binome.jpg' /></p>

- [Description](#description)
- [Installation](#installation)
- [Usage](#usage)
- [Commands](#commands)
- [Support Platforms](#support-platforms)
- [Example](#example)
- [Type of File](#type-of-file)
- [Cache](#cache)
- [HTML & RSS](#html--rss)
- [Requirements](#requirements)
- [Compatible](#compatible)
- [Screenshots](#screenshots)

## Description
Youtube_subscription_manager is an alternative to youtube.com to retrieve the videos of your subscriptions feed without requires an account *(You can also recover the videos of other platform).*

It can gather informations about every video in a playlist, a channel or your subsciptions feed and outputs it as a html page, a detailed list or a list of links.

## Installation
1. Clone the project: `git clone https://github.com/sawyerf/youtube-sm.git`
2. Open the folder you just cloned : `cd youtube-sm`
3. Execute the setup: `sudo python3 setup.py install`
4. Recover your subscription file in youtube and you are ready to go !

## Usage

1. Download your subscriptions configuration from youtube.com ([here](https://www.youtube.com/subscription_manager?action_takeout=1))
2. Once this is done, you may load it by using the following command :
```
youtube-sm --init [file]
```

3. Finally, you can start using the program using the commands shown below :
```
youtube-sm [OPTIONS]
```

## Commands

```
-a           URL       Add a sub to your sub list.
-e                     Edit your sub list.
-h                     Print this help text and exit.
-l           URL       Analyze only one sub.
-m           MODE      Choose the type of the output file (html, json, raw, list, view).
-r                     Remove the cache.
-s           URL       Stats of the selected channel(s).
-t           DAYS      Select how many DAYS ago the last content written to your file will be dated .
-v                     Verbose.
--af         FILE      Add a list of sub to your sub list.
--ax         FILE      Add a xml file in your sub list.
--cat                  View your subscriptions.
--css        STYLE     Export the css files (light, dark, switch).
--dead                 Show the dead channels + those who posted no videos.
--help                 Print this help text and exit.
--html                 Recover sub with html page instead of RSS. This method recover more video.
--init       FILE      Remove all your subs and add new.
--loading              Print a progress bar.
--old        MONTHS    Show channels who didn't post videos since MONTHS + dead channels.
--output     FILE      Write the output in FILE.
--ultra-html           An advanced version of --html.
--version              Print version.
```

## Support Platforms
- Dailymotion
- Infoconcert
- Peertube
- Youtube

## Example

- Basic
```
youtube-sm
```

- Your sub since 1 month
```
youtube-sm -t 30 --css --loading
```

- All the videos of a channel
```
youtube-sm -l https://www.youtube.com/channel/UC-lHJZR3Gqxm24_Vd_AJ5Yw -t -1 -m list --loading -r --output test.csv
```

- Add a sub
```
youtube-sm -a https://www.youtube.com/channel/UC-lHJZR3Gqxm24_Vd_AJ5Yw
```

## Type of File
#### Raw :
```
{date}     {video_id}     {channel_id}     {title}     {channel}     {link_pic}
```
#### List :
```
https://www.youtube.com/watch?v={video_id}
```
#### View :
```
{views}
```
#### Json :
```json
{
	"url": {
		"content": "https://www.youtube.com/watch?v=ID",
		"image": "https://i.ytimg.com/vi/ID/mqdefault.jpg",
		"uploader": "https://youtube.com/channel/ID"
	},
	"date": "2020-04-23 16:08:22",
	"title": "Video Title",
	"uploader": "Channel",
	"views": "228283"
}
```
#### Html :
```html
<!--NEXT -->
<div class="video">
	<a class="left" href="{video_id}">
		<div class="container">
			<img src="{link_pic}">
			<div class="bottom-right">{time}</div>
		</div>
	</a>
	<a href="https://www.youtube.com/watch?v={video_id}"><h4>{title}</h4> </a>
	<a href="https://www.youtube.com/channel/{channel_id}"> <p>{channel}</p> </a>
	<p>{date}</p>
	<p class="clear"></p>
</div>
```

## Cache
3 files are generated by the program : `sub.swy`, `log` and `data/`.
- `sub.swy` is a list of yours subscriptions.
- `log` contains the script's time of execution.
- `data/` is a folder where the information for every video are stored.

These 3 files are generated in:
- Windows: `C:\Users\<name>\.youtube_sm\`.
- Linux/MacOS:   `/home/<name>/.cache/youtube_sm/.`.

## HTML & RSS
With youtube-sm you can recover your subscriptions using two methods:
- RSS (default): videos are recovered through an XML page.
- HTML (with --html): videos are recovered through an HTML page.


They are two choice because they cannot recover the same informations and don't require the same amount of time. 
So the default method (the RSS method) is more adapted to recover only the newest videos, whereas the HTML method
is more adapted to recover all the videos of a playlist or to recover its last 30 videos of a channel.

|            | *ULTRA-HTML* | *ULTRA-HTML* |    *HTML*   |    *HTML*    |     *RSS*    |
|:----------:|:------------:|:------------:|:-----------:|:------------:|:------------:|
|            | **Channel**  | **Playlist** | **Channel** | **Playlist** |   **Both**   |
|  Execution |**very** slow |**very** slow |     slow    |     slow     |     Fast     |
|   Number   |    **all**   |    **all**   |  30 videos  |  100 videos  |   15 videos  |
|    Date    |     **~**    |       ✖      |     **~**   |       ✖      |       ✔      |
|  Like Rate |       ✖      |       ✖      |      ✖      |       ✖      |       ✔      |
|    Views   |       ✔      |       ✖      |      ✔      |       ✖      |       ✔      |

## Requirements
- Python 3

## Compatible
- Linux
- Windows
- Android (Termux)
- MacOS

## Screenshots
<a href="https://sawyerf.gitlab.io/youtube_sm/example.html"><img src="https://sawyerf.gitlab.io/youtube_sm/sub_mob.jpg" alt="Phone screen" width=405px height=720px>
<img src="https://sawyerf.gitlab.io/youtube_sm/sub_pc.jpg" alt="PC screen" width=100% height=auto></a>
