# SKILL2_MPMC_AMBIKA



## Aim
To write an assembly language program for the **8051 microcontroller** to generate a **2-second delay** using **Timer 0 in Mode 1 (16-bit mode)** and **blink an LED connected to Port 3.7**.

---

## Apparatus Required

Personal computer with keil software

---

## Algorithm
1. Start the program.  
2. Configure **Timer 0** in **Mode 1 (16-bit)** by loading `TMOD` with `01H`.  
3. Connect the LED to **Port 3.7 (P3.7)**.  
4. Toggle the LED using the **CPL** instruction.  
5. Call the **delay subroutine** to generate a total delay of 2 seconds.  
6. Inside the delay routine, load **TH0** and **TL0** registers to create a 100 ms delay.  
7. Repeat the 100 ms delay 20 times (20 × 100 ms = 2 s).  
8. Continue toggling the LED indefinitely using a loop.  

---

## Assembly Language Program

```
ORG 0000H

MAIN:
    MOV TMOD, #01H      
AGAIN:
    CPL P3.7             
    ACALL DELAY
    SJMP AGAIN

DELAY:
    MOV R7, #20          
DELAY_LOOP:
    MOV TH0, #0B1H
    MOV TL0, #0E0H
    SETB TR0
WAIT:
    JNB TF0, WAIT
    CLR TR0
    CLR TF0
    DJNZ R7, DELAY_LOOP
    RET

END
```

## OUTPUT

<img width="820" height="600" alt="Screenshot 2025-11-05 084545" src="https://github.com/user-attachments/assets/67b0fa55-78c4-4fbb-81d0-7be41033fa31" />

<img width="882" height="665" alt="Screenshot 2025-11-05 084743" src="https://github.com/user-attachments/assets/23bcf590-7874-450d-9c1b-06227e66b372" />


## RESULT

The LED connected to Port 3.7 of the 8051 microcontroller blinks continuously with a 2-second delay between ON and OFF states, confirming successful delay generation using Timer 0 in Mode 1.
