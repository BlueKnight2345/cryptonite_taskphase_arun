# GDB baby step 1

**Flag:** `picoCTF{549698}`

This is something that is completely new to me so I started of by watching the reference videos given in the task phase pdf

I then installed IDA to see disassembled program

I opened up the given file in IDA and saw the mentioned register with the value it contained

![Screenshot 2024-10-30 184534](https://github.com/user-attachments/assets/194af1b5-1ec1-40ea-91a0-f45be1d53670)

converted the value from hexadecimal to decimal and got the flag

What you learned through solving this challenge:

1. Reading basic assembly code
2. Using IDA to dissassemble programs

References

- https://www.youtube.com/watch?v=gh2RXE9BIN8

# ARMssembly 1

**Flag:** `picoCTF{0000005a}`

Given file contained assembly code and flag would be the value which needed to be entered to achieve 'win' condition in the code

The required input is the result of this assembly code:


```
func:
        sub     sp, sp, #32
        str     w0, [sp, 12]
        mov     w0, 68
        str     w0, [sp, 16]
        mov     w0, 2
        str     w0, [sp, 20]
        mov     w0, 3
        str     w0, [sp, 24]
        ldr     w0, [sp, 20]
        ldr     w1, [sp, 16]
        lsl     w0, w1, w0
        str     w0, [sp, 28]
        ldr     w1, [sp, 28]
        ldr     w0, [sp, 24]
        sdiv    w0, w1, w0
        str     w0, [sp, 28]
        ldr     w1, [sp, 28]
        ldr     w0, [sp, 12]
        sub     w0, w1, w0
        str     w0, [sp, 28]
        ldr     w0, [sp, 28]
        add     sp, sp, 32
```

the code first creates a 32 byte stack then stores certain values within in

68 at 16,2 at 20, 3 at 24, and a function argument w0 at 12

it then loads the value at 20 and 16 and performs a left bitwise shift on it

so a shift of 2 on 68 yields 272 and stores it in 28

it then loads the value at 28 and 24 and divides them and stores it back in 28

so 272/3 = 90 (integer division)

then it loads back the result and the stack space is freed

What you learned through solving this challenge:

1. Reading even more assembly code





