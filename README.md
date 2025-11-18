
# Serial Transfer of Single Byte / Character using 8051 (Keil)

## AIM
To write and execute an Embedded C Program for Serial Transfer of Single Byte / Character using 8051 in Keil.

## APPARATUS REQUIRED
- Personal Computer  
- Keil µVision Software  

## PROGRAM

### (i) Serial Port Transfer a Single Character

```
ORG 00H 
MOV TMOD, #20H 
MOV TH1, #0FDH 
MOV SCON, #50H 
SETB TR1 
MAIN_LOOP:
MOV SBUF, #'B' 
WAIT_TI:
JNB TI, WAIT_TI 
CLR TI 
END

FOR C CODE

#include<reg51.h>
void main(void)
{
TMOD=0X20; //TIMER 1, MODE 2
TH1=0XFA;
SCON=0X50;
TR1=1;
while(1)
{
SBUF='A';
while(TI==0);
T1=0;
}
}

```
### (ii) Serial Port to Transfer a Message

```

ORG 00H
MOV TMOD,#20H
MOV TH1,#0FCH
MOV SCON,#40H
SETB TR1
MOV DPTR,#4500H
AGAIN:MOVX A,@DPTR
MOV SBUF,A
WAIT:JNB TI,WAIT
CLR TI
INC DPTR
SJMP AGAIN
END

Void main(void)
{
unsigned char msg[]="KAILAASH";
unsigned char i;
TMOD=0X20; //TIMER 1, MODE 2
TH1=0XFA;
SCON=0X50;
TR1=1;
for(i-0;i<=12;i++)
{
SBUF=msg[i];
while(TI==0);
TI=0;
}
while(1);
}

```

### OUTPUT:
<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/431f024c-cd2f-4591-823f-8ed760d615af" />
<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/50b10013-fad4-4d78-bb45-be35502896f3" />
<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/4345128e-0c40-4be4-a32c-b8c36290c621" />
<img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/4df0934d-affb-4513-a645-d6dcba75d316" />

### RESULT:
Thus the Serial transfer of Single Byte / Character using 8051 KEIL was done and shown the output.
