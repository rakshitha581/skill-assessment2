# skill-assessment2

**AIM**
 To develop an 8051 microcontroller assembly program that uses Timer 1 in Mode 2 to generate a 100 ms delay and toggles an LED connected to Port 2.5. 8051.
 
 **APPARATUS REQUIRED**
 
   1.start the program
   
   2.Load Timer 1 mode 2 into the TMOD register(TMOD=20H)
   
   3.Mode 2 = 8-bit auto-reload mode.
   
   4.Clear TF1 (Timer 1 overflow flag)
   
   5.Start Timer 1 by setting the TR1 bit
   
   6.When overflow count=391:
       Toggle bit p2.5(using CPL p2.5)
       Reset counters and repeat
       
   8.Continue infinitely to toggle P2.5 every 100ms.
   
   **Program**
   ```
ORG 0000H
MOV TMOD, #20H
MOV TH1, #00H
HERE:
    MOV R6, #2
OUTER:
    MOV R5, #196
INNER:
    SETB TR1
WAIT:
    JNB TF1, WAIT
    CLR TR1
    CLR TF1
    DJNZ R5, INNER
    CPL P2.5
    DJNZ R6, OUTER
    SJMP HERE
END
```
**OUTPUT**
<img width="1086" height="482" alt="image" src="https://github.com/user-attachments/assets/ffd3d1ec-7da1-42cf-9dd0-f2807ea6e45f" />
<img width="1387" height="319" alt="Screenshot 2025-10-27 221930" src="https://github.com/user-attachments/assets/1a0ca62f-b47b-4428-87f7-f398c6c00b1d" />
**RESULT**
Successfully designed and verified an 8051 Assembly program to toggle an LED at Port 2.5 with a precise 100 ms interval using Timer 1 in Mode 2. 
Demonstrated timer initialization, delay loop, and I/O port manipulation in 8051 Assembly.
