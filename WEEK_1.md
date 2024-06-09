# WEEK_1

## CHALLENGE_1

### 1)Information
After downloading the image I used file command and confirmed its an image.
On inspecting image details i saw that XMP rights management had a strange string in cc: license .
I copied string and put it in base64 decoder to get flag.

#### flag is picoCTF{the_m3tadata_1s_modified}

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

#### flag is picoCTF{ac0072c423ee13bfc0b166af72e25b61}

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

### 9) MSB
Tried to solve using various tools like stegsolve , stegseek but was unable to solve it.


### 10) Extensions
Use file command and we see its supposed to be jpg not txt.
Change extension to .jpg and open to get flag.
#### flag is picoCTF{now_you_know_about_extensions

## Challenge2
### Sakura Room
#### 1) 
Just type "Let's Go!"

#### 2)
On opening and inspecting the image we can see the file path.
This leads us to our guess which is SakuraSnowAngelAiko which is the username.

#### 3)
On searching the username on browser we can see a github profile .
Another good result is the linkedin profile which gives us her name that is "Aiko Abe".

The first result on searching the username we get github account which has repository called pgp.
On searching about PGP we get to know its a method of encrypting and decrypting emails.
We have the public PGP key. On searching how to use it I got to know about software kleopatra.
Using public PGP key on it we get details which gives us the email : SakuraSnowAngel83@protonmail.com

#### 4)
Github profile also has several other repos . I see some mining repos , our pgp one ,  an IO one and one named eth.
1) The eth file contains info. On searching internet for eth we get ethereum as our crypto currency.
2) We browse history of eth repo file and can see a line which has later been removed.
We get the wallet adress from this : 0xa102397dbeeBeFD8cD2F73A89122fCdB53abB6ef
3) On searching it on browser we get a site called etherscan which gives us past transaction details.
These can be used to get mining pool on 23rd jan 2021 : Ethermine
4) And we also get other crypto used by Aiko : Tether

#### 5)
1) Given photo shows AikoAbe3 on searching we get twitter account and get twitter handle : SakuraLoverAiko
2)We see on twitter posts that Aiko has saved her wifi details somewhere on dark web with our hint being deep and paste.
On searching for dark web I had to install Tor and subsquently i searched for deep paste.
I found out its an onion. I tried to open it but was unable to. Hence i had to use hint given on site.
Hint had picture which had site given : http://deepv2w7p33xa4pwxzwi2ps4j62gfxpyp44ezjbmpttxz3owlsp4ljid.onion
3) On searching how to get Bssid when i have username and password i got a site called wigle.net .
Afterwards i solved 6th question first through which i filtered search region for wigle.net to Japan.
Search gave me wifi BSSID and location of Aiko's home : 84:af:ec:34:fc:f8

#### 6)

1) The photo before flight seems to be the sakura tree.
Actually couldnt find answer to 1st part and had to search to get hint which is the washington monument.
Hence nearest airport code is : DCA

2) We have image first class lounge sakura lounge. Just searched this on google found similar image to be of airport in Haneda
   Code is : HND
3) Lake is easy to find as image has map of japan. Open map and get name og lake : Lake Inawashiro
4) I actually guessed it due to a wifi network called Hirosaki_Free_wifi however our answer is confirmed when we find BSSID in q5.

### 2) Gralhix tasks
#### 6) 
I just cropped the tweet to get image. I then revese searched on tin eye and found it being used in articles as old as 2016.
Hence its not an image of 2023.
I also found a link of alamy which tells us image is taken in 2006.

#### 4)
Just right clicked image and searched on google.
Got result of Oan Resort.
Location is : Oan resort , Oan island Wonip , Chuuk , Micronesia.
Coordinates can be gotten by opening it on google maps : 7.363445 N , 151.755707 E.
Observe background islands in image and shape of islands in google earth , google maps . Camera is facing North West.

#### 3)
Just crop the image and use it in google image search.
Found an article on atalayar that they are standing at Ankara Presidential complex.(https://www.atalayar.com/en/articulo/politics/somalia-erdogans-spearhead-east-africa/20200508113246145709.html)

Coordinates are : 39.9308 N , 32.7992 E

#### 14)
Using date and time stamp I was able to determine the earthquake being talked about was the one in romania.
I explored earthquake list of 2016.
Took a still of video and searched it on google lens. Got suggested Chisinau which happens to be capital of moldova neihboring romania.
Hence we get earthquake location as Chisinau . Earthquake was of 5.5 -6 on richter scale.
I searched for buildings in Chisinau and luckily found one similar to the large building in background. That image was much clearer and once i searched for the place on gmaps i could summarize the location. : V continental Business centre
Coordinates : 47.0167644 N , 28.852601 E

#### 26)
I observed the image tags and took them in ascending order.
1st image is of Chorsu Bazaar , Tashkent , Uzbekistan.
2ns image shows a ferris wheel which leads us to an amusement park anhor lokomotiv.
However image is near halva cafe and browsing nearby on maps we find 2nd location : approx coordinates : 41.326116 N , 69.266301

I googles samsung sign and tashkent and got an image but got nothing else.
I googled for Navien in tashkent but found its office which looked completely different.
Its a picture on road near a bus stand.


Our video seemed to be of a train. So we can look for railway stations . Nearest railway station to pic 2 is Stantsiya Tashkent Pass.
So our pic 3 should be somewhere in between. A guess after seeing maps and google earth is coordinate : 41.2983   N , 69.2723 E

For 4th image we just see a bridge under which a road is there. Couldnt find fourth.

for mode of transportation:
1 to 2 can be car or by walking
2 to 3 can be car or walking
3 to 4 is car then train and then car.
