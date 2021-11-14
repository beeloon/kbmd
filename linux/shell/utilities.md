## autojump
autojump is a faster way to navigate your filesystem. It works by maintaining a database of the directories you use the most from the command line.
Directories must be visited first before they can be jumped to.
```bash
# install if not preinstalled
sudo apt install autojump

# go to Desktop/scheme/horai/api/coupon
j coupon
```

## wget
The non-interactive network downloader
```bash
wget [option] [URL]

# download file from www.google.com into Download folder
wget -P ~/Downloads [URL]

# download file from www.google.com into Download folder and rename it to myfile.txt
wget -P ~/Downloads/myfile.txt [URL]

# download file if connection was lost (for big files)
wget -c [URL] 

# check if file availability by link
wget --spider [URL]

# downloads several files by links which located in file.txt 
wget -i file.txt

# recursive downloads by link with deep level
wget -r -l [deep] [URL] 

# recursive download with specified types
wget -r -A type1,type2,...,typeN [URL]
```

## tar
an archiving utility
```bash
# archive file1..fileN to ARCHIVE.tar (without compression)
#   - c create  a  new archive
#   - v print info on screen
#   - f create file on command system
#   - z filter the archive through gzip(1).

# work as unzip
tar -cvf [ARCHIVE.tar] file1, file2, ..., fileN

# work as gzip
tar -zcvf [ARCHIVE.tar] file1, file2, ..., fileN

# work as zip
tar -xvf [ARCHIVE.tar]

# work as gunzip
tar -xzvf [ARCHIVE.tar]
```

## bzip
```bash
# another archive utility
bzip2 [FILE]

bunzip2 [FILE].bz2
```

