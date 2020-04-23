# Code Project Drum-Gloves
###### If you want to use Code, click sketch_apr12a.ino or [Click](https://github.com/macsakarn/Drum-Gloves/blob/master/Code/sketch_apr12a.ino)

### Part 1
> Set up libraries
```c
#include <SD.h>
#define SD_ChipSelectPin 4
#include <TMRpcm.h>
#include <SPI.h>
```
> Set up Value
```c
int pong = 10;
int nang = 8;
int kang = 7;
int koy = 6;
int chee = 5;
int hand = 3;
int v_pong;
int v_chee;
int v_kang;
int v_nang;
int v_koy;
int v_hand;
int time_delay=50;
```
### Part 2
> Set Function setup
```c
void setup() {
  pinMode (pong, INPUT_PULLUP);
  pinMode (chee, INPUT_PULLUP);
  pinMode (kang, INPUT_PULLUP);
  pinMode (nang, INPUT_PULLUP);
  pinMode (koy, INPUT_PULLUP);
  pinMode (hand, INPUT_PULLUP);

  tmrpcm.speakerPin = 9; //5,6,11 or 46 on Mega, 9 on Uno, Nano, etc

  Serial.begin(9600);
  if (!SD.begin(SD_ChipSelectPin)) {  // see if the card is present and can be initialized:
    Serial.println("SD fail");
  }
}
```
> Set Function scan_key
```c
void scan_key() {
  v_pong = digitalRead(pong);
  v_chee = digitalRead(chee);
  v_kang = digitalRead(kang);
  v_nang = digitalRead(nang);
  v_koy = digitalRead(koy);
  v_hand = digitalRead(hand);
}
```

### Part 3 (Enjoy)
> loop Program for playing music
```c
void loop() {
  scan_key();
  if (v_pong == 0) {
    delay(time_delay);
    scan_key();
    if ((v_pong == 0) & (v_chee == 1) & (v_kang == 1) & (v_nang == 1) & (v_koy == 1) & (v_hand == 1))  {
      tmrpcm.play("1.wav");
    } else {
      chk();
    }
    scan_key();
    while (v_pong == 0) {
      delay(5);
      scan_key();
    }
  }
  if (v_chee == 0) {
    delay(time_delay);
    scan_key();
    if ((v_pong == 1) & (v_chee == 0) & (v_kang == 1) & (v_nang == 1) & (v_koy == 1) & (v_hand == 1))  {
      tmrpcm.play("2.wav");
    } else {
      chk();
    }
    scan_key();
    while (v_chee == 0) {
      delay(5);
      scan_key();
    }
  }
  if (v_kang == 0) {
    delay(time_delay);
    scan_key();
    if ((v_pong == 1) & (v_chee == 1) & (v_kang == 0) & (v_nang == 1) & (v_koy == 1) & (v_hand == 1))  {
      tmrpcm.play("3.wav");
    } else {
      chk();
    }
    scan_key();
    while (v_kang == 0) {
      delay(5);
      scan_key();
    }
  }
  if (v_nang == 0) {
    delay(time_delay);
    scan_key();
    if ((v_pong == 1) & (v_chee == 1) & (v_kang == 1) & (v_nang == 0) & (v_koy == 1) & (v_hand == 1))  {
      tmrpcm.play("4.wav");
    } else {
      chk();
    }
    scan_key();
    while (v_nang == 0) {
      delay(5);
      scan_key();
    }
  }
  if (v_koy == 0) {
    delay(time_delay);
    scan_key();
    if ((v_pong == 1) & (v_chee == 1) & (v_kang == 1) & (v_nang == 1) & (v_koy == 0) & (v_hand == 1))  {
      tmrpcm.play("5.wav");
    } else {
      chk();
    }
    scan_key();
    while (v_koy == 0) {
      delay(5);
      scan_key();
    }
  }
  if (v_hand == 0) {
    delay(time_delay);
    scan_key();
    if ((v_pong == 1) & (v_chee == 1) & (v_kang == 1) & (v_nang == 1) & (v_koy == 1) & (v_hand == 0))  {
      tmrpcm.play("6.wav");
    } else {
      chk();
    }
    scan_key();
    while (v_hand == 0) {
      delay(5);
      scan_key();
    }
  }
}
```
> If the program detects more than 1 button press
```c
void chk() {
  if ((v_pong == 0) & (v_chee == 0) & (v_kang == 1) & (v_nang == 1) & (v_koy == 1) & (v_hand == 1)) {
    tmrpcm.play("12.wav");
  }
  if ((v_pong == 0) & (v_chee == 1) & (v_kang == 0) & (v_nang == 1) & (v_koy == 1) & (v_hand == 1)) {
    tmrpcm.play("13.wav");
  }
  if ((v_pong == 0) & (v_chee == 1) & (v_kang == 1) & (v_nang == 0) & (v_koy == 1) & (v_hand == 1)) {
    tmrpcm.play("14.wav");
  }
  if ((v_pong == 0) & (v_chee == 1) & (v_kang == 1) & (v_nang == 1) & (v_koy == 0) & (v_hand == 1)) {
    tmrpcm.play("15.wav");
  }
  if ((v_pong == 0) & (v_chee == 1) & (v_kang == 1) & (v_nang == 1) & (v_koy == 1) & (v_hand == 0)) {
    tmrpcm.play("16.wav");
  }
  if ((v_pong == 1) & (v_chee == 0) & (v_kang == 0) & (v_nang == 1) & (v_koy == 1) & (v_hand == 1)) {
    tmrpcm.play("23.wav");
  }
  if ((v_pong == 1) & (v_chee == 0) & (v_kang == 1) & (v_nang == 0) & (v_koy == 1) & (v_hand == 1)) {
    tmrpcm.play("24.wav");
  }
  if ((v_pong == 1) & (v_chee == 0) & (v_kang == 1) & (v_nang == 1) & (v_koy == 0) & (v_hand == 1)) {
    tmrpcm.play("25.wav");
  }
  if ((v_pong == 1) & (v_chee == 0) & (v_kang == 1) & (v_nang == 1) & (v_koy == 1) & (v_hand == 0)) {
    tmrpcm.play("26.wav");
  }
  if ((v_pong == 1) & (v_chee == 1) & (v_kang == 0) & (v_nang == 0) & (v_koy == 1) & (v_hand == 1)) {
    tmrpcm.play("34.wav");
  }
  if ((v_pong == 1) & (v_chee == 1) & (v_kang == 0) & (v_nang == 1) & (v_koy == 0) & (v_hand == 1)) {
    tmrpcm.play("35.wav");
  }
  if ((v_pong == 1) & (v_chee == 1) & (v_kang == 0) & (v_nang == 1) & (v_koy == 1) & (v_hand == 0)) {
    tmrpcm.play("36.wav");
  }
  if ((v_pong == 1) & (v_chee == 1) & (v_kang == 1) & (v_nang == 0) & (v_koy == 0) & (v_hand == 1)) {
    tmrpcm.play("45.wav");
  }
  if ((v_pong == 1) & (v_chee == 1) & (v_kang == 1) & (v_nang == 0) & (v_koy == 1) & (v_hand == 0)) {
    tmrpcm.play("46.wav");
  }
  if ((v_pong == 1) & (v_chee == 1) & (v_kang == 1) & (v_nang == 1) & (v_koy == 0) & (v_hand == 0)) {
    tmrpcm.play("56.wav");
  }
  if ((v_pong == 0) & (v_chee == 0) & (v_kang == 0) & (v_nang == 1) & (v_koy == 1) & (v_hand == 1)) {
    tmrpcm.play("123.wav");
  }
  if ((v_pong == 0) & (v_chee == 0) & (v_kang == 1) & (v_nang == 0) & (v_koy == 1) & (v_hand == 1)) {
    tmrpcm.play("124.wav");
  }
  if ((v_pong == 0) & (v_chee == 0) & (v_kang == 1) & (v_nang == 1) & (v_koy == 0) & (v_hand == 1)) {
    tmrpcm.play("125.wav");
  }
  if ((v_pong == 0) & (v_chee == 0) & (v_kang == 1) & (v_nang == 1) & (v_koy == 1) & (v_hand == 0)) {
    tmrpcm.play("126.wav");
  }
  if ((v_pong == 0) & (v_chee == 1) & (v_kang == 0) & (v_nang == 0) & (v_koy == 1) & (v_hand == 1)) {
    tmrpcm.play("134.wav");
  }
  if ((v_pong == 0) & (v_chee == 1) & (v_kang == 0) & (v_nang == 1) & (v_koy == 0) & (v_hand == 1)) {
    tmrpcm.play("135.wav");
  }
  if ((v_pong == 0) & (v_chee == 1) & (v_kang == 0) & (v_nang == 1) & (v_koy == 1) & (v_hand == 0)) {
    tmrpcm.play("136.wav");
  }
  if ((v_pong == 0) & (v_chee == 1) & (v_kang == 1) & (v_nang == 0) & (v_koy == 0) & (v_hand == 1)) {
    tmrpcm.play("145.wav");
  }
  if ((v_pong == 0) & (v_chee == 1) & (v_kang == 1) & (v_nang == 0) & (v_koy == 1) & (v_hand == 0)) {
    tmrpcm.play("146.wav");
  }
  if ((v_pong == 0) & (v_chee == 1) & (v_kang == 1) & (v_nang == 1) & (v_koy == 0) & (v_hand == 0)) {
    tmrpcm.play("156.wav");
  }
  if ((v_pong == 1) & (v_chee == 0) & (v_kang == 0) & (v_nang == 0) & (v_koy == 1) & (v_hand == 1)) {
    tmrpcm.play("234.wav");
  }
  if ((v_pong == 1) & (v_chee == 0) & (v_kang == 0) & (v_nang == 1) & (v_koy == 0) & (v_hand == 1)) {
    tmrpcm.play("235.wav");
  }
  if ((v_pong == 1) & (v_chee == 0) & (v_kang == 0) & (v_nang == 1) & (v_koy == 1) & (v_hand == 0)) {
    tmrpcm.play("236.wav");
  }
  if ((v_pong == 1) & (v_chee == 0) & (v_kang == 1) & (v_nang == 0) & (v_koy == 0) & (v_hand == 1)) {
    tmrpcm.play("245.wav");
  }
  if ((v_pong == 1) & (v_chee == 0) & (v_kang == 1) & (v_nang == 0) & (v_koy == 1) & (v_hand == 0)) {
    tmrpcm.play("246.wav");
  }
  if ((v_pong == 1) & (v_chee == 0) & (v_kang == 1) & (v_nang == 1) & (v_koy == 0) & (v_hand == 0)) {
    tmrpcm.play("256.wav");
  }
  if ((v_pong == 1) & (v_chee == 1) & (v_kang == 0) & (v_nang == 0) & (v_koy == 0) & (v_hand == 1)) {
    tmrpcm.play("345.wav");
  }
  if ((v_pong == 1) & (v_chee == 1) & (v_kang == 0) & (v_nang == 0) & (v_koy == 1) & (v_hand == 0)) {
    tmrpcm.play("346.wav");
  }
  if ((v_pong == 1) & (v_chee == 1) & (v_kang == 0) & (v_nang == 1) & (v_koy == 0) & (v_hand == 0)) {
    tmrpcm.play("356.wav");
  }
  if ((v_pong == 1) & (v_chee == 1) & (v_kang == 1) & (v_nang == 0) & (v_koy == 0) & (v_hand == 0)) {
    tmrpcm.play("456.wav");
  }
  if ((v_pong == 0) & (v_chee == 0) & (v_kang == 0) & (v_nang == 0) & (v_koy == 1) & (v_hand == 1)) {
    tmrpcm.play("1234.wav");
  }
  if ((v_pong == 0) & (v_chee == 0) & (v_kang == 0) & (v_nang == 1) & (v_koy == 0) & (v_hand == 1)) {
    tmrpcm.play("1235.wav");
  }
  if ((v_pong == 0) & (v_chee == 0) & (v_kang == 0) & (v_nang == 1) & (v_koy == 1) & (v_hand == 0)) {
    tmrpcm.play("1236.wav");
  }
  if ((v_pong == 0) & (v_chee == 0) & (v_kang == 1) & (v_nang == 0) & (v_koy == 0) & (v_hand == 1)) {
    tmrpcm.play("1245.wav");
  }
  if ((v_pong == 0) & (v_chee == 0) & (v_kang == 1) & (v_nang == 0) & (v_koy == 1) & (v_hand == 6)) {
    tmrpcm.play("1246.wav");
  }
  if ((v_pong == 0) & (v_chee == 0) & (v_kang == 1) & (v_nang == 1) & (v_koy == 0) & (v_hand == 0)) {
    tmrpcm.play("1256.wav");
  }
  if ((v_pong == 0) & (v_chee == 1) & (v_kang == 0) & (v_nang == 0) & (v_koy == 0) & (v_hand == 1)) {
    tmrpcm.play("1345.wav");
  }
  if ((v_pong == 0) & (v_chee == 1) & (v_kang == 0) & (v_nang == 0) & (v_koy == 1) & (v_hand == 0)) {
    tmrpcm.play("1346.wav");
  }
  if ((v_pong == 0) & (v_chee == 1) & (v_kang == 0) & (v_nang == 1) & (v_koy == 0) & (v_hand == 0)) {
    tmrpcm.play("1356.wav");
  }
  if ((v_pong == 0) & (v_chee == 1) & (v_kang == 1) & (v_nang == 0) & (v_koy == 0) & (v_hand == 0)) {
    tmrpcm.play("1456.wav");
  }
  if ((v_pong == 1) & (v_chee == 0) & (v_kang == 0) & (v_nang == 0) & (v_koy == 0) & (v_hand == 1)) {
    tmrpcm.play("1456.wav");
  }
  if ((v_pong == 1) & (v_chee == 0) & (v_kang == 0) & (v_nang == 0) & (v_koy == 0) & (v_hand == 1)) {
    tmrpcm.play("2345.wav");
  }
  if ((v_pong == 1) & (v_chee == 0) & (v_kang == 0) & (v_nang == 0) & (v_koy == 1) & (v_hand == 0)) {
    tmrpcm.play("2346.wav");
  }
  if ((v_pong == 1) & (v_chee == 0) & (v_kang == 0) & (v_nang == 1) & (v_koy == 0) & (v_hand == 0)) {
    tmrpcm.play("2356.wav");
  }
  if ((v_pong == 1) & (v_chee == 0) & (v_kang == 1) & (v_nang == 0) & (v_koy == 0) & (v_hand == 0)) {
    tmrpcm.play("2456.wav");
  }
  if ((v_pong == 1) & (v_chee == 1) & (v_kang == 0) & (v_nang == 0) & (v_koy == 0) & (v_hand == 0)) {
    tmrpcm.play("3456.wav");
  }
  if ((v_pong == 0) & (v_chee == 0) & (v_kang == 0) & (v_nang == 0) & (v_koy == 0) & (v_hand == 1)) {
    tmrpcm.play("12345.wav");
  }
  if ((v_pong == 0) & (v_chee == 0) & (v_kang == 0) & (v_nang == 0) & (v_koy == 1) & (v_hand == 0)) {
    tmrpcm.play("12346.wav");
  }
  if ((v_pong == 0) & (v_chee == 0) & (v_kang == 0) & (v_nang == 1) & (v_koy == 0) & (v_hand == 0)) {
    tmrpcm.play("12356.wav");
  }
  if ((v_pong == 0) & (v_chee == 0) & (v_kang == 1) & (v_nang == 0) & (v_koy == 0) & (v_hand == 0)) {
    tmrpcm.play("12456.wav");
  }
  if ((v_pong == 0) & (v_chee == 1) & (v_kang == 0) & (v_nang == 0) & (v_koy == 0) & (v_hand == 0)) {
    tmrpcm.play("13456.wav");
  }
  if ((v_pong == 1) & (v_chee == 0) & (v_kang == 0) & (v_nang == 0) & (v_koy == 0) & (v_hand == 0)) {
    tmrpcm.play("23456.wav");
  }
  if ((v_pong == 0) & (v_chee == 0) & (v_kang == 0) & (v_nang == 0) & (v_koy == 0) & (v_hand == 0)) {
    tmrpcm.play("123456.wav");
  }
}
```
###### If you want to use Code, click sketch_apr12a.ino or [Click](https://github.com/macsakarn/Drum-Gloves/blob/master/Code/sketch_apr12a.ino)
