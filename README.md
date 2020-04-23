# Drum-Gloves Project

## ABOUT THIS PROJECT
  
  dasdasdasdasdasd
  

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
  
  ![alt text](https://github.com/macsakarn/Drum-Gloves/blob/master/images/Schematic.jpg "SCHEMATICS")
  
  ## Code
  
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
  pinMode (kang, INPUT_PULLUP);
  pinMode (nang, INPUT_PULLUP);
  pinMode (koy, INPUT_PULLUP);
  pinMode (hand, INPUT_PULLUP);
  ```
  #### Set speaker librarie
  ```c
  TMRpcm tmrpcm;
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
  

  
  
  
  ### Images
  ![alt text](https://github.com/macsakarn/Drum-Gloves/blob/master/images/images.jpg "Promote")
  
  ### Team
  > university student
  
  | 62070169| 62070190 | 62070203 | 62070206 |
  | --- | --- | --- | --- |
  | Viphavadee Sathaporn | Sakarn Bantadjun | Sukawit Bualoy | Supanida Ploykam |
  
  

  
  
  
  

