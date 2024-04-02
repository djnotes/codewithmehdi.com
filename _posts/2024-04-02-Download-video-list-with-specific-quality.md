# How to Download a List of Videos with A Specific Format and Quality 

## Steps: 
- Put the links in a file like list.txt
- Pick one of the links and list its formats:
```
yt-dlp --skip-download --list-formats  "https://www.youtube.com/watch?v=SomeVideo"
```
You will see the list of formats. For example, 1920x1080 video format is 399 and mp4 audio format is 140. So, we will specify 399+140 as format to download. 
- Run the following loop over the videos in the list:
```
for file in $(cat list.txt); do yt-dlp  -f bestvideo+bestaudio  --merge-output-format mp4 --format 399+140   "$file"; done
```

399 refers to 
This works for YouTube, but you might be able to use it with other video hosting services as well.

