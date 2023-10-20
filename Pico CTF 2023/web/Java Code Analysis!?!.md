# Java Code Analysis!?!

## Description
BookShelf Pico, my premium online book-reading service. I believe that my website is super secure. I challenge you to prove me wrong by reading the 'Flag' book! Here are the credentials to get you started:

    Username: "user"
    Password: "user"
## solution
Lets first check the web page

This is after login

![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/899d542c-2f9f-4fed-be9f-b381644fbac4)

![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/08cf6c80-929d-40e5-9217-ef917acdc92a)

I dont have permission for the flag book. I need to be Admin role to get the flag.

This Challenge do give us the source code for this application. Let's analys it.
![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/c4037e97-c183-4eaa-a378-c38a1cdbbaf8)

This is how to get the pdf

![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/fa8b1ca4-e4b4-491f-91a4-f6bb5a40bcb4)

Then check user service, All imortant method do need Admin role to access lets check how it generate the JWT.

![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/65d1104f-6d45-440b-9407-71d647299b1e)

I see one interesting thing 'SECRET_KEY' If I know the secret key then I may change the jwt.
![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/39df9920-fa47-48e4-a4b8-d1e5221879dc)

Here there is one security problem. After the Web Application run if it fail to read the 'SERVER_SECRET_FILENAME'. Then it will use the 'generateRandomString' as the key.
![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/d8d41146-aaa7-44b8-9030-677be3987ff8)
![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/5f6c802d-5de3-4db3-9549-7c5f35ac9fc2)

Lets try change the token role using generateRandomString 1234.

You can go to this website https://jwt.io/
![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/3a26a7f5-8687-48cc-bbfb-4049ab0291e5)

Try the modified token to get the users. It work! Now we know the admin id!
![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/204c746a-9b65-4212-8efd-1b9974d4a0c6)

Modify the token again use the id from the last step.
![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/f5fc722e-ac20-45dc-a43e-5f66c03a5ef9)

We get the Flag!
![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/84d08263-63d4-45b3-8154-13c5d791f616)


# Conclusion
This question involve token modify and misconfig problem. To prevent those do more check and have stronger key .
