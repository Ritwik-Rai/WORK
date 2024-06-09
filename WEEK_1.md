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
I couldnt open the file so i used hexedit to make the first 10 bytes same as any other .bmp file.
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

#### flag is picoCTF{3nh4nc3d_d0a757bf}

### 6)advanced_potion_making
File is corrupted. On using xxd and checking header bytes I see 89 50 42 11 and i also see IHDR written .
We can guess file is supposed to be .png . I correcteg Header bytes to 89 50 4E 47 and tried to open file.
However I got IHDR length error. I searched on wikipedia for IHDR length bytes and changed the length bytes value to default value.
00 12 13 14 to 00 00 00 0D.
I now opened file and saw screen is just red. I tried to use binwalk however got nothing.
I tried to use zsteg but didnt work.
I then opened file in image editor and tried changing colours.
In black and white mode you get flag.

#### flag is picoCTF{w1z4rdry}

### 7)File types
Upon using cat on file we get some script.
1st line of script is the hint. Use sh Flag.pdf to get shell archive text.
then use ar x flag to proceed.

From here its quite similar to the bandit game level 12 except there are much more file types.
First we make random directory(say abc) and then use file command to see that we have a .cpio file. Use cpio -D -i abc < flag to get decompressed file in our directory.
cd to this directory and then proceed.
We see file type using file . Its bzip2 .
put .bz2 extension on file and decompress using bzip2 -d command.
We see file type using file . Its gzip .
put .gz extension on file and decompress using gzip -d command.
We see file type using file . Its lzip .
put .lz extension on file and decompress using lzip -d command.
We see file type using file . Its lz4 .
put .lz4 extension on file and decompress using lz4 -d command.
We see file type using file . Its lzma .
put .xz extension on file and decompress using xz -d command.
We see file type using file . Its lzop .
put .lzop extension on file and decompress using lzop -d command.
We see file type using file .
put .lz extension on file and decompress using lzip -d command.
We see file type using file . Its xz .
put .xz extension on file and decompress using xz -d command.

Finally we see output which is heaxadecimal.Use converter to get flag.

#### flag is picoCTF{f1len@m3_m@n1pul@t10n_f0r_0b2cur17y_950c4fee}

### 8) hideme
Use binwalk on file and then use unzip.
Open file it has flag

#### flag is picoCTF{Hiddinng_An_imag3_within_@n_ima9e_cda72af0}

### 9) 





### 10) Extensions
Use file command and we see its supposed to be jpg not txt.
Change extension to .jpg and open to get flag.
#### flag is picoCTF{now_you_know_about_extensions}







