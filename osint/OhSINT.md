### TryHackme Room: OhSINT (CTF Challenge)

### Room Link

[Click here to open the room](https://tryhackme.com/room/ohsint)

### Room Description

What information can you possibly get with just one image file?

### Objective

The objective of this room is to find as much information as possible by only having an image, using OSINT techniques.

### Vulnerability found

Exposure of identity and personal data due to metadata contained image file.

## Methodology

1.I check if the image file has metadata that can reveal sensitive information. To do this, I'm gonna use exiftool, a tool that lets us see metadatas in files. I ran the following command: exiftool WindowsXP_1551719014755.jpg

2.

