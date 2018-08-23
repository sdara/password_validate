10-21-2004
CSC153-02
Project #06

Psuedocode



Include header files, function prototypes, and global variables for use within the program.

Split the code into functions, so the main function has little code in it.

Call the getpass() function to read in a users password. Through this function, we will call another function which will validate the password based on simple rules.

Call the validatepass function within the getpass function to validate a users input. The validatepass function which make sure the length of the entered string is at least 6 characters long, the string contains at least one uppercase character, the string contains at least one lowercase character, and the string contains at least one digit.

If the password fails at any of these (length, upper, lower, digit) warn the user and display that the entered password it invalid. Otherwise, display that it is a valid password.


Source Code

//header files
#include <iostream.h>
#include <string.h>
#include <ctype.h>
 
//function prototypes
bool validatepass(char array[], int length);
void getpass(void);
 
//global and contant variable
//defines the maxlength of the password
//that can be entered...81 allows 80 characters + 1 null
//character.
const passwordMaxLen=81;
 
void main(void)
{
//call the getpass function
	getpass();
 
	//after the function ends, thank the user
cout<<endl<<"Thank you for using the program!"<<endl<<endl;
}
 
/*
this is the validatepass function which takes an 
array of characters (string) and length, and checks
each cell (character in the string) to see if it is
either uppercase, lowercase, or a numeric digit
*/
bool validatepass(char array[],int length)
{
 
	//assume that password is invalid
bool valid=false;
 
//make sure the size is greater than 6 characters
	if(length<6)
	valid=false;
	else
	valid=true;
 
	//if it is under 6 characters, warn the user and return to
	//the the function that called this - dont continue to check
	//because it already failed the first test
if(valid==false)
{
cout << " *** This password is under 6 characters long. ***"<<endl;
return valid;
}
 
//if it passes the first test, assume that it will fail the next
valid=false;
 
//checks to find an uppercase character
for(int x=0;x<=length;x++){
	if(isupper(array[x]))
	{
		valid=true;
		break;
	}
}
 
 
//if there are no uppercase characters, warn the user and return
//to the function that called this function
if(valid==false)
{
cout << " *** ERROR: This password must contain at least one uppercase character. ***"<<endl;
return valid;
}
 
 
//if it passes the second test, assume that it will fail the next
valid=false;
 
//checks to find a lowercase character
for(int y=0;y<=length;y++){
	if(islower(array[y]))
	{
		valid=true;
		break;
	}
}
 
 
//if there are no lowervase characters, warn the user and return
//to the function that called this function
if(valid==false)
{
cout << " *** ERROR: Password must contain at least one lowercase character. ***"<<endl;
return valid;
}
 
//if it passes the third test, assume that it will fail the last test
valid=false;
 
//checs to find a digit
for(int z=0;z<=length;z++){
	if(isdigit(array[z]))
	{
		valid=true;
		break;
	}
}
 
//if there are no digits, warn the user and return to the function
//that called this function
if(valid==false)
{
cout << " *** ERROR: Password must at least one digit. ***"<<endl;
return valid;
}
}
 
//this is the getpass function that gets password data
//and calls the validatepass function using the entered
//string. based on the returned results, it will display
//if the user entered a valid or invalid password.
void getpass(void)
{
 
char password[passwordMaxLen];
cout<<"Please enter a password between 6 and 80 characters."<<endl;
 
cin.getline(password,passwordMaxLen);
cout<<endl;
if(validatepass(password,strlen(password))){
cout<<"This is a valid password.";
}else{
cout<<endl;
cout<<"This is an invalid password.";
}
cout<<endl;
}

Program Output

Please enter a password between 6 and 80 characters.
123
 
 *** This password is under 6 characters long. ***
 
This is an invalid password.
 
Thank you for using the program!
 
Press any key to continue
 
========================================
 
Please enter a password between 6 and 80 characters.
125555
 
 *** ERROR: This password must contain at least one uppercase character. ***
 
This is an invalid password.
 
Thank you for using the program!
 
Press any key to continue
 
========================================
 
Please enter a password between 6 and 80 characters.
111A33
 
 *** ERROR: Password must contain at least one lowercase character. ***
 
This is an invalid password.
 
Thank you for using the program!
 
Press any key to continue
 
========================================
 
Please enter a password between 6 and 80 characters.
aaAAaa
 
 *** ERROR: Password must at least one digit. ***
 
This is an invalid password.
 
Thank you for using the program!
 
Press any key to continue
 
========================================
 
Please enter a password between 6 and 80 characters.
1A65v1
 
This is a valid password.
 
Thank you for using the program!
 
Press any key to continue



