# WEEK_1

## CHALLENGE_1

### 1)Information
After downloading the image I used file command and confirmed its an image.
On inspecting image details i saw that XMP rights management had a strange string in cc: license .
I copied string and put it in base64 decoder to get flag.

### 2)Matryoshka doll
Matryoshka dolls are famous dolls in which a doll contains a doll in itself.
Use binwalk command to see file contents.
We see it contains a zip file . i used unzip to extract content.
Extracted base_images/2_c.jpg.
Binwalk again and then unzip.
Extracted base_images/3_c.jpg.
Binwalk again and then unzip.
Extracted base_images/4_c.jpg.
Binwalk again and then unzip.
Extracted flag.txt.
Cat the file to get flag.

### 3)tunn3l v1s10n
Ran file command and saw its bmp.
i used hexedit to make the first 10 bytes same as any other .bmp file.
Afterwards the file opened and i saw a picture. However the text on picture was "notaflag".
I proceeded to check wikipedia to find height bytes of file and increased them. After approx tripling the height i was able to see the flag.

#### flag is "picoCTF{qu1t3_a_v13w_2020}".

### 4)MacroHard WeakEdge
On running the file command i see its a .pptm file.
On running binwalk I saw a lot og zip files.
i used unzip command to unzip all files.
After unzipping i saw a unique file /ppt/slideMasters/hidden . 
On using cat on file I got a string which on using base64 decoder and got the flag.
#### flag is picoCTF{D1d_u_kn0w_ppts_r_zip5}

### 5)Enhance!
Used file command and saw its a .svg file.
Used xxd and observed header bytes and saw nothing special.
However on using cat on file I observed the last few commands and was able to see flag in them.










