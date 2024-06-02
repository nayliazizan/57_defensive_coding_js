this is just exercise that i did when learning fullstack engineer at codecademy. therefore, the whole code wasnt mine. i only put a few lines to complete exercise

goal of this exercise is to apply what i've learn abt defensive coding in javascript.

what i've done in this exercise:

STATIC CODE ANALYSIS
1. first i run eslint . in terminal to find any potential issues. and then i run eslint --fix . to automatically fix most issues found. the balance will be fix manually.

STRICT MODE

2. run npm start to see which errors have been triggered. and one by one i fix and run npm start.
- i remove the "delete hostname;" in main.js
- i remove the "delete port;" in main.js
- i remove the duplicated "response" parameter in calculator.js
- i add "const" for these variables: hostname, port, app at the top section of main.js
3. now run npm start again and test out the form submission. here, i see that when i input the "/proc/cpuinfo" in the form, the website display the content of that file (this is vulnerable)

FIXING FILE SYSTEM VULNERABILITY IN MAIN MENU
4. so i change the filePath to current working directory using path method. from this:
const filename = name;
to this:
const filename = path.join(process.cwd(), name);
5. this time when i enter the input in the form, the website display the file not found.

FIXING VULNERABILITIES IN CALCULATOR

6. the calculator features uses eval to evaluate JS expressions and display result. so i change it to safe-eval. 
7. first i add "import safeEval from "safe-eval";" at top section of calculator.js.
8. in calculator_callback function, i change the answer variable from this: 
const answer = eval(expression);
to this: 
const answer = safeEval(expression);

FIXING VULNERABILITIES IN LINUX EMULATOR

9. the linux emulator form uses exec. so i change it to execFile.
10. first change the exec function to execFile at top section of linux.js.
and then change the method name from exec() to execFile() in linux_callback function.

FIXING VULNERABILITIES IN CONTACT FORM

11. the contact form use some risky regular expressions to validate user input. so i replace all unsafe expressions i found with the regular expression ".*" in formValidator.js.

