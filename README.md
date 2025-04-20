# Epikast Exercise
IT Administrator assignment for Epikast

## Description
For this assignment we were requested to host a website using a serverlsess service called [pico.sh](https://pico.sh/)

## Getting started
### Prerequisites
* Linux, Ubuntu 25.04 was used

### Generate a SSH key
Pico.sh is a platform based entirely on SSH. To be able to use it we need a SSH key that uses ED25519. Type the following in cmd:
```
ssh-keygen -t ed25519 -C "your_email@example.com"
```
You will be prompted to provide the file location of where to store the key and after that you will be asked to provide a password.

### Create a pico.sh account
Once you have the SSH key use the following command to connect to pico.sh:
```
ssh pico.sh
```
You may be requested for permission to proceed with the connection, after which you will be asked for the password that was provided while creating the SSH key. After you connect, provide a suitable username.

### Create a html file to upload
We will not create a website from scratch. We will copy the source code of https://www.karl.berlin/simplicity.html

Right click anywhere on the website (that is not a link), select "View Page Source" and copy the source code. Paste the source code in an html file in a directory of your choosing (ex. "~/epikast/public/Exercise in Simplicity.html").

We have also created a "Exercise in Simplicity v2.html" for testing purposes, where we changed the colour of the banner from blue to red.

### Upload the website
Once the file with the website is created simply execute the following command if already inside the directory with the html file:
```
rsync -rv ./ pgs.sh:/sites
```
Alternatively you can use the full path to the folder. For our example we can use
```
rsync -rv ~/epikast/public/ pgs.sh:/sites
```
Note: "sites" is the project name and can be changed to anything as long as it only contrains lower case letters (a-z) and numbers (0-9).

With that all the HTML files in the provided directory are uploaded.

### Find the SSH public key
Last thing in the assignment is to add the SSH key to a file in the the repo. If you saved the key in the default location use
```
cat ~/.ssh/id_ed25519.pub
```
to print the key in the cmd. We pasted ours in bin/public.key. If you saved it somewhere else change the filepath accordingly.
