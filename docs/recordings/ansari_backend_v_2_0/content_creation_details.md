Related to ansari_thumbnail_background.png:
* Used Descript's AI Gen. tool to create a background image for video thumbnails.
* Used https://www.pixelcut.ai/ai-image-editor?tool=upscale to upscale the image.
* Used https://www.iloveimg.com/photo-editor to add text to the image.
  * Used Oswald font
  * Used 0c433a color for text

Related to audio editing:
* Used Descript to edit audio.
* Related to `Audio Effects`:
  * Added `studio sound` with `65%` intensity (free plan contains few tries, so I subscribed to creative plan).
* Removed filler words using Descript's `remove filler words` / `shorten word gaps` features (same free/subscription comment)

Related to video editing:
* Used Descript to edit video.
* Saw this awesome (slightly UI-outdated) tutorial: https://www.youtube.com/watch?v=ySv-KhsKF9M
* Manually added chapters by reading the transcript and adding chapter markers.
* Exported these chapters to YouTube-like description by following this YouTube short: https://www.youtube.com/shorts/38Fee7sDI3s
* Exported transcript to `md` file using these settings:
  * Include composition name
  * Include markers ✅
  * Include ignored text ✅
  * timecodes:
    * Interval: 30 seconds
    * paragraph breaks ✅
    * markers ✅
* Exported subtitles with these settings:
  * Format: `srt`
  * Max characters per line: `66`
  * Max lines per card: `1`

Related to video description:
* Wrote to `underlord` prompts similar to these ones for the videos in the series:
  * "generate a video description for this video based on the transcription content and markers of this project; I'll later add this to a youtube video , which is a new video in a series of videos we're making for explaining Ansari backend repo. talk with "we" pronoun, as we're a team."
  * "for this video, write to me a video's description that is a one liner which is related to the title/outline of the video. I will later add this to the description section of a YouTube video."
  * "write to me a description similar to this structure/size (but for the content of this video): `then paste the description of the first video in the series`"
* Used the following to get PRs/commits that deprecated/removed certain files/folders:
  * GitHub Copilot chat: https://github.com/copilot/share/4a524330-4ae0-8cd4-a942-8442207528a3
  * GitHub UI file history: https://github.com/ansari-project/ansari-backend/commits/main/FILE_NAME.EXT

Finally, used these general steps (as reminders) before uploading each video to YouTube:
1. Rename descript file ( Ansari Backend V2.0 - 00x ... (SquadCast Session x Take x) )
2. Rename 00x_ folder 
3. Create thumbnail
4. Modify description (paste the timestamps, then paste the two prompt messages to underlord)
5. Create transcript/subtitles
6. Sign in first, THEN add video metadata (e.g., remove squadcast suffix and add thumbnail), then upload
7. Go to YouTube Studio, then add thumbnail (as adding it in descript doesn't suffice for some reason), then add subtitles, then add to playlist