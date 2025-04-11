# Week 11.1

## Caesar Cipher Code Names
Using a key of three we must create a Caesar cipher to encrypt our codename. Mine is the below:
Edqdqd Pxiilqv --> Banana Muffins

## Decoding

48 61 20 48 61 20 48 61 21 20 59 6f 75 20 63 61 6e 20 6e 65 76 65 72 20 63 61 74 63 68 20 74 68 65 20 41 6c 70 68 61 62 65 74 20 42 61 6e 64 69 74 21 20 53 65 65 20 69 66 20 79 6f 75 20 63 61 6e 20 66 6f 6c 6c 6f 77 20 6d 65 20 68 65 72 65 3a 0a 30 31 31 30 31 30 30 30 20 30 31 31 31 30 31 30 30 20 30 31 31 31 30 31 30 30 20 30 31 31 31 30 30 30 30 20 30 30 31 31 31 30 31 30 20 30 30 31 30 31 31 31 31 20 30 30 31 30 31 31 31 31 20 30 31 31 31 30 31 31 31 20 30 31 31 31 30 31 31 31 20 30 31 31 31 30 31 31 31 20 30 30 31 30 31 31 31 30 20 30 31 31 31 30 30 30 30 20 30 31 31 30 30 30 30 31 20 30 31 31 30 30 31 31 31 20 30 31 31 30 30 31 30 31 20 30 31 31 30 31 31 31 31 20 30 31 31 31 30 30 31 30 20 30 31 31 30 30 30 30 31 20 30 31 31 30 31 31 30 31 20 30 31 31 30 30 30 30 31 20 30 30 31 30 31 31 31 30 20 30 31 31 30 30 30 31 31 20 30 31 31 30 31 31 31 31 20 30 31 31 30 31 31 30 31 20 30 30 31 30 31 31 31 31 20 30 30 31 31 31 31 31 31 20 30 31 31 31 30 30 30 30 20 30 30 31 31 31 31 30 31 20 30 31 31 30 30 30 30 31 20 30 31 31 30 30 30 31 30 20 30 31 31 31 30 31 30 31 20 30 31 31 31 30 30 31 30 20 30 31 31 30 30 31 31 31 20 30 31 31 30 31 31 30 30 20 30 31 31 30 30 30 30 31 20 30 31 31 31 30 30 31 30 20 30 30 31 31 30 30 30 31

We must decode the above Hexadecimal code:

Ha Ha Ha! You can never catch the Alphabet Bandit! See if you can follow me here:
01101000 01110100 01110100 01110000 00111010 00101111 00101111 01110111 01110111 01110111 00101110 01110000 01100001 01100111 01100101 01101111 01110010 01100001 01101101 01100001 00101110 01100011 01101111 01101101 00101111 00111111 01110000 00111101 01100001 01100010 01110101 01110010 01100111 01101100 01100001 01110010 00110001

Next we must decode the binary from the above message:

http://www.pageorama.com/?p=aburglar1<br>
The Mayor is just the beginning of my Reign, My next target will be:  68 74 74 70 73 3a 2f 2f 77 77 77 2e 70 61 67 65 6f 72 61 6d 61 2e 63 6f 6d 2f 3f 70 3d 63 6c 75 65 2d 32

Again we find a Hexadecimal code to convert:

https://www.pageorama.com/?p=clue-2<br>
Impressive work solving my puzzles, my next target will be: 68 111 99 116 111 114 32 66 114 111 119 110 39 115 32 72 111 117 115 101

This time we are given a decimal which I needed to convert to Hexadecimal and then into text revealing the final clue:

D o c t o r   B r o w n ' s   H o u s e

## Ciphers

Caesars cipher again will be use to decrypt the below message. We were given the Key {123456} = {341256}<br>
I broke this down into chunks of 6 and then just moved the first digits to the middle which unscrambled the words.

Message:  u Yocanen vecar tcthh e phAlab Betant,di Mney xtar Tgeist  Cvialnsou Hse
You ca_n neve_r catc_h the _Alphab_et Ban_dit, M_y next_ Targe_t is C_alvins_ House

## OpenSSL


'''console
wget https://gist.githubusercontent.com/jmmeacham/d894fcde2f5ed5613fe49fee433a6bbc/raw/809ea931822ac3ed30e93d864bf251f7c106166e/key-iv to download the file
cat key-iv
openssl enc -pbkdf2 -nosalt -aes-256-cbc -in communication.txt.enc -d -base64 -K 346B3EFB4B899E8205C4B35E91F5A4605A54F89730AE65CA2C43AB464E76CA99 -iv 759D1B9BF335985F55E3E9940E751B67
'''
