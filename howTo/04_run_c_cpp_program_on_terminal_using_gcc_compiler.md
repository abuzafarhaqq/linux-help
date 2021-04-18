- Step 1: Open terminal
- Step 2: Type command to install gcc or g++ compiler.
		```
		sudo apt install build-essential
		```
		This will install the necessary C/c++ develpment libraries for your Ubuntu to create C/C++ programs. To check gcc version type this command:
		```
		gcc -version or gcc -v
		```
- Step 3: Now go to that folder where you will create C/C++ programs. I am creating my programs in Documents directory.
		```
		cd ~/Documents
		nvim first.c
		nvim hello.cpp
		```
- Step 4: For C program we created first.c and for C++ program we created hello.cpp. Now, write some code to this files.
  - C code(first.c):
			```
			#include<stdio.h>
			int main()
			{
				printf("\n\nWelcome to my First Program\n\n");

				return 0;
			}
			```
  - C++ code(hello.cpp):
			```
			#include<iostream>
			using namespace std;
			int main()
			{
				cout<<"Hello World in C++ Program"<<endl;

				return 0;
			}
			```
  - Step 5: Save file and exit.
	- Step 6: Compiling C/C++ Codes:
	  - Compiling C codes:
				```
				sudo gcc first.c
				sudo gcc -o first first.c
				```
		- Compiling C++ codes:
				```
				sudo g++ hello.cpp
				sudo g++ -o hello hello.cpp
				```
		The first line of code create an executable file with .out extension named as "first.out" where as second line of code first is executable or object file or first.c program. This rules also applicable for C++ codes also.
	- Step 7: Run the program on terminal:
			```
			./first.out
			./first
			./hello.out
			./hello
			```
			If you compiled first using first method run the program using first method if you prefer socond one then run the program using second method. This rules also applicable for C++ codes.
