FirefoxCache2
=============
Python scripts for parsing the index file and individual cache files from the cache2 folder of Firefox defaulted on in version 32

##Blogs
Written by [@JamesHabben](https://twitter.com/JamesHabben):<br>
http://encase-forensic-blog.guidancesoftware.com/2015/02/firefox-cache2-storage-breakdown.html

Written by [@sandersonforens](https://twitter.com/sandersonforens):<br>
http://sandersonforensics.com/forum/content.php?216-Converting-the-new-Firefox-cache2-files-to-an-SQLite-DB-for-investigating

##Usage
```
usage: firefox-cache2-file-parser.py [-h] [-f FILE] [-d DIRECTORY] [-o OUTPUT]

Parse Firefox cache2 files in a directory or individually.

optional arguments:
  -h, --help            show this help message and exit
  -f FILE, --file FILE  single cache2 file to parse
  -d DIRECTORY, --directory DIRECTORY
                        directory with cache2 files to parse
  -o OUTPUT, --output OUTPUT
                        CSV output file
```

```
usage: firefox-cache2-index-parser.py [-h] [-o OUTPUT] file

Parse Firefox cache2 index file.

positional arguments:
  file                  index file to parse

optional arguments:
  -h, --help            show this help message and exit
  -o OUTPUT, --output OUTPUT
                        CSV output file

```

#Commercial Tools Parsing Cache2
|Company|Tool|URL|
|---|---|---|
|Digital Detective|NetAnalysis & HstEx|http://www.digital-detective.net/digital-forensic-software/netanalysis/|
|Foxton Software|Browser History Viewer (Free)|http://forensic-software.co.uk/browser-history-viewer/|
|NirSoft|MozillaCacheView (Free)|http://www.nirsoft.net/utils/mozilla_cache_viewer.html|
|Magnet Software|Internet Evidence Finder|http://www.magnetforensics.com/|
