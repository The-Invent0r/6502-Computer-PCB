# 6502-Computer-PCB

DISCLAIMER: I DELETED ALL OF THE CONNECTIONS FOR GRANT SEARLE'S VIDEO+KEYBOARD INTERFACE BEFORE UPLOADING THE FILES. IF YOU WANT TO ADD IN THE VIDEO+KEYBOARD INTERFACE PLEASE TAKE A LOOK AT HIS WEBSITE (http://searle.x10host.com/MonitorKeyboard/index.html) AND FOLLOW THE DIRECTIONS ON THERE. IT MIGHT BE WORTH IT TO PROTOTYPE THE INTERFACE ON BREADBOARDS FIRST.


I made this Modified version of Ben Eater's 6502 computer PCB and decided instead of adding a VGA video card, I wanted to connect this to a CRT monitor using a composite video cable. 
I decided to add in a 6551 ACIA (Asyncronous Communications Interface Adapter) to give the computer serial I/O capabilites. I then found Grant Searle's video+keyboard interface and decided to incorporate that into my design. 
The only issue was that my 6551 was sending and receiving data at 19200 baud, and the video+keyboard interface was running at 115200 baud. Luckily it was an easy fix to go into the software and update the USARD_BAUD variable from 115200u1 to 19200u1. 
However, before uploading the code I changed the fuse bytes to ensure that the 2 AVR chips were running at the correct crystal oscillator frequencies. 
To upload the code for the keyboard chip I used WinAVR. I found that before uploading the keyboard interface code, I needed to change the file name to main.c and I also had to create my own makefile for the atmega328p. 
For the video chip I decided to use the .hex file burn that directly into the other atmega328p using the command line. 
When I first prototyped this circuit on breadboards I had a lot of issues which I later discovered were caused by using a low quality breadboard. So if all off your connections and software are correct, try using a more expensive but higher quality BB830 breadboard.
When you first connect the circuit to an LCD screen you should see a cursor blinking. In order to conduct a loopback test of the circuit, simply connect the Rx pin to the Tx pin on the keyboard chip, then connect the PS2 keyboard and start typing. If it works then you'll see the correct characters on the screen.

I also made a short YouTube video demonstrating the workings (https://www.youtube.com/watch?v=8I7XNCFC5iU)

![20220930_150136](https://user-images.githubusercontent.com/29239243/194722983-07c7fe45-ddef-48b9-b235-9b804303eea0.jpg)
![20220930_170826](https://user-images.githubusercontent.com/29239243/194722992-ca49237b-6e60-4c9b-8efe-6a2a17eb0fa9.jpg)
