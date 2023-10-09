# XSS relate question
## The web application is to send report about error
![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/1f7c4be6-99b4-4a58-a3ed-0d2022844405)
![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/fa475879-22f8-427a-bb80-a82187956dff)

## Solving
based on the hint about https://owasp.org/www-community/attacks/xss/ /n
The first thing we need to do is to find the script that can trigger the page to run alert()
![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/3b3c7a9c-9a93-4be5-9728-6b26399f421f)

![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/1aea6a8d-88fe-4b7c-a9db-ccb4dce8d9cf)

Now lets try get the admin cookie ！！！！！！！！！
![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/e32279a6-ec60-4760-8fe2-2399007d7b6f)
![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/273422fc-43fe-4d70-a548-3aa5791731c5)
![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/4274bd69-7ddc-4f09-b209-5d3e8732df0e)
And then wee need to make another call to api/flag with the cookie we get to get the Flag!
