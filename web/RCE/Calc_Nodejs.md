**Introduction**

The challenge presented an application with a seemingly benign functionality, allowing users to evaluate mathematical expressions. However, digging deeper revealed a remote code execution (RCE) vulnerability, eventually leading to the discovery of the challenge's flag.
![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/e2984f09-5ee2-4609-b886-cc9e0bcf6363)

**Identify Vulnerability**

After cheking the source I find the application exposes an API endpoint /calc/:expression which evaluates mathematical expressions provided in the URL. A close inspection of the Util.eval() method in util.js revealed that it uses the dangerous new Function() constructor to evaluate the given expression.


**Gaining RCE**

After some initial tests, we discovered that while many global objects and functions were not directly accessible (e.g., require), we were able to access the process object. This gave us the ability to interact with the underlying Node.js environment. Using lambda expressions like (a => some_code)() allowed us to bypass initial restrictions and execute our desired code.

![image](https://github.com/ZHallen122/CTF-Practice-WriteUp/assets/106571949/e7f43b98-a251-474e-99a1-bf3a4158f45c)


After discover the flag i use this to get the flag
(a => process.mainModule.require('fs').readFileSync('/app/flag.txt', 'utf-8'))()

**Conclusion**

The challenge serves as a reminder of the risks associated with evaluating untrusted input. By chaining together knowledge of JavaScript, Node.js, and the exposed API functionality, I successfully navigated the application environment and captured the flag.
