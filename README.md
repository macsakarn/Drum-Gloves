# Drum-Gloves Project

## INTRODUCTION

  Drums’ Glove is designed for the entertainment and practiced the hand muscle sensory isolation as a designed and developed to control the glove and has a series of sounds like a team drum which include snare drum, tenor drum, bass drum, cymbals, hi-hat and kettledrum for the ordinary people who want to play a team drum that save cost and reduce space. Drums’ Glove was made from Arduino Lilypad and knowledge about drum set model. In the glove has a module that sends a signal to Arduino nano and sends analog signal.

## ABOUT THIS PROJECT
  
  This project was created for education.
It was caused by me wanting to play the drums and not having enough money to buy drums to play. Therefore was born as a
**Drum-Gloves Project** It was made for those who like to play drums. But don't have money to buy gloves The gloves will consist of
1. Snare drum 
2. Tenor drum 
3. Bass drum 
4. Cymbals 
5. Hi-hat 
6. Kettledrum

## COMPONENTS AND SUPPLIES

  - Arduino Nano R3
  - Jeck 3.5 cable
  - REGULATOR (+5 VOLTS. 1.5 AMP IC)
  - Diode 1N4007 (1A 1000V Rectifier)
  - 9V Battery Connector 
  - Micro SD Card Module
  - Switch x6
  - Jumper wires
  - PCB Board
  - Glove
  
  ## SCHEMATICS
  
  ![alt text](https://raw.githubusercontent.com/macsakarn/Drum-Gloves/master/Media/Images/Schematic.jpg "SCHEMATICS")
  
  ## CODE
  First things first, let's program the Arduino.
  - Download and install the Arduino software from http://arduino.cc.
  
  Use the Libraries manager [Click](https://github.com/macsakarn/Drum-Gloves/tree/master/Code/Libraries) to install
  ```c
  #include <SD.h>
  #include <TMRpcm.h>
  #include <SPI.h>
  ```
  ###### If you want to see the full version [Click](https://github.com/macsakarn/Drum-Gloves/tree/master/Code)
  
  #### Set pin
  ```c
  int pong = 10;
  int nang = 8;
  int kang = 7;  //Set finger pin 
  int koy = 6;
  int chee = 5;
  int hand = 3;
  
  pinMode (pong, INPUT_PULLUP);
  pinMode (chee, INPUT_PULLUP);
  pinMode (kang, INPUT_PULLUP);  //Set pinmode
  pinMode (nang, INPUT_PULLUP); 
  pinMode (koy, INPUT_PULLUP);
  pinMode (hand, INPUT_PULLUP);
  ```
  #### Set speaker librarie
  ```c
  TMRpcm tmrpcm; //Call libraries TMRpcm.h
  tmrpcm.speakerPin = 9; //5,6,11 or 46 on Mega, 9 on Uno, Nano, etc
  ```
  #### Set SD Card
  ```c
  if (!SD.begin(SD_ChipSelectPin)) {  // see if the card is present and can be initialized:
    Serial.println("SD fail");
  }
  ```
  #### Check values from switch
  
  ```c
  v_pong = digitalRead(pong);
  v_chee = digitalRead(chee);
  v_kang = digitalRead(kang); 
  v_nang = digitalRead(nang);
  v_koy = digitalRead(koy);
  v_hand = digitalRead(hand);
  ```
  
  #### Example of code for pressing and playing music
  ```c
  if (v_pong == 0) {
    delay(time_delay); //delay 50ms
    scan_key(); // Check button
    if ((v_pong == 0) & (v_chee == 1) & (v_kang == 1) & (v_nang == 1) & (v_koy == 1) & (v_hand == 1))  {
      tmrpcm.play("1.wav"); //Play drum (1)
  ```
  
  ###### If you want to see the full version [Click](https://github.com/macsakarn/Drum-Gloves/tree/master/Code)
  

  
  
  
  ## IMAGES 
  Pictures and other videos [Click](https://github.com/macsakarn/Drum-Gloves/tree/master/Media) 
  ![alt text](https://raw.githubusercontent.com/macsakarn/Drum-Gloves/master/Media/Images/images.jpg "Promote")
  
  ## TEAM
  > University student
  
  | 62070169| 62070190 | 62070203 | 62070206 |
  | --- | --- | --- | --- |
  | Viphavadee Sathaporn | Sakarn Bantadjun | Sukawit Bualoy | Supanida Ploykam |
  
  

  
  
  
  

