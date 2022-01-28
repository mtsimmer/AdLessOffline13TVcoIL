Tired of ads ?
==============
 <b> Here is an example of downloading from TV13 website with no ads. </b>

```batch
ffmpeg.exe -i "https://cdnapisec.kaltura.com/p/2748741/sp/274874100/playManifest/entryId/1_4950q0tu/protocol/https/format/applehttp/flavorIds/1_2n8pvvg3,1_ib2rkqnp,1_hc35kik8,1_anl9rsji,1_9ehs1bwy/a.m3u8" -vcodec libx264 S05E04.mp4
```

<h1> The right build of ffmpeg is part of the solution </h1>

Please note the tested build is on the date of release of the repo 
<a href="https://www.gyan.dev/ffmpeg/builds/"> static FFMpeg Builds </a>
<i>(supposed to be about 5.0)</i> 


But how ?
=========

Well first disable your adblocker <i>(yes enjoying the site without ads wont happen today)</i>
and go to <a href="https://13tv.co.il/yummies/games-of-chef/season-05/episodes/"> The site of the chosen episodes you wanna download </a>
<i>(supposed to be about 5.0)</i><br>
- open the link you would like to download and click 
- Click <b> F12 </b> 
- go to <b> Network </b> 
- <i>(see the little search)</i> look for <b> a.m3u8 </b>
- now, copy the URL and remove the GET parameters everything after the '<b>?</b>' in the '<b>URL</b>'

all that's left to do is feed ffmpeg with the found and trimmed url. <br>
you've got a few options how to do it. <i>(these examples are on the first example)</i>

- Please note that '<b>-vcodec copy</b>' is the fastes but most storage hungry.
```batch
ffmpeg.exe -i "https://cdnapisec.kaltura.com/p/2748741/sp/274874100/playManifest/entryId/1_4950q0tu/protocol/https/format/applehttp/flavorIds/1_2n8pvvg3,1_ib2rkqnp,1_hc35kik8,1_anl9rsji,1_9ehs1bwy/a.m3u8" -vcodec copy Example.mkv
```
- Please note that '<b>-vcodec libx264</b>' is slow but storage humble.
```batch
ffmpeg.exe -i "https://cdnapisec.kaltura.com/p/2748741/sp/274874100/playManifest/entryId/1_4950q0tu/protocol/https/format/applehttp/flavorIds/1_2n8pvvg3,1_ib2rkqnp,1_hc35kik8,1_anl9rsji,1_9ehs1bwy/a.m3u8" -vcodec libx264 Example.mkv
```
- Please note that '<b>-vcodec h264_qsv</b>' is quicker storage humble. <i>Quicker but requires intel Quick sync on board (if you are running on IGPU give it a shot maybe a laptop?)</i> 
```batch
ffmpeg.exe -i "https://cdnapisec.kaltura.com/p/2748741/sp/274874100/playManifest/entryId/1_4950q0tu/protocol/https/format/applehttp/flavorIds/1_2n8pvvg3,1_ib2rkqnp,1_hc35kik8,1_anl9rsji,1_9ehs1bwy/a.m3u8" -vcodec h264_qsv Example.mkv
```

side notes
==========

- the storage may vary.
- this process maybe automated with a nice crawler and some python.
- all this research was done for research porpuses only.