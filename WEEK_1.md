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
However i wasnt able to open the file so i used hexedit to make the first 10 bytes same as any other .bmp file.
