# **Lab Report 4**

## Step 1: Setup Delete any existing forks of the repository you have on your account
First, I opened up the github page for my fork of th lab7 repository. For me, the link was https://github.com/andrewzpu/lab7.  
![image](https://user-images.githubusercontent.com/66804382/221462616-d13fa4b2-188f-4c1d-8b19-eed2b5e9a8e4.png)
I pressed the settings button to enter the repository settings:  
![image](https://user-images.githubusercontent.com/66804382/221462270-aa6e249c-8c9c-47ed-a1ea-b14e8d5850a1.png)
Once, in the settings, it should look like this:  
![image](https://user-images.githubusercontent.com/66804382/221462350-250bc425-41ba-400d-9133-f12370605577.png)
Then, I scrolled to the bottom and clicked the "Delete this Repository" button:  
![image](https://user-images.githubusercontent.com/66804382/221462439-7727af66-8e5d-4da4-bd2f-5c2374544484.png)

## Setup Fork the repository
Go to the original repository at https://github.com/ucsd-cse15l-w23/lab7:  
![image](https://user-images.githubusercontent.com/66804382/221463019-9af97d5e-f02c-40cb-aac9-6d5f7517f5b0.png)
Press the "Fork" button to fork the repository:  
![image](https://user-images.githubusercontent.com/66804382/221463162-7a1c5702-031c-4972-876d-a180af64248c.png)  
Once you've chosen a name for your fork, press the "Create fork" button at the bottom of the page:  
![image](https://user-images.githubusercontent.com/66804382/221463250-9245768e-8a31-46f4-8d1a-2cdcb15ca04f.png)  
And now you've successfully created your own fork

## The real deal Start the timer!
Have someone with a timer ready to start when you SSH into your machine.

## Log into ieng6
In your bash terminal, run the command ```ssh cs15lwi23***@ieng6.ucsd.edu``` (*** depends on your own specific machine) 
My *** is aug, so I ran the command ```ssh cs15lwi23aug@ieng6.ucsd.edu``` and pressed ```<Enter>``` which resulted in the following screen:  
![image](https://user-images.githubusercontent.com/66804382/221473857-76a62cac-d4ba-43b6-8fed-f496d0a0d519.png)  
I already had the command typed out before the timer was started in order to save time, so all I pressed was ```<Enter>```
I was not required to type in my password because I already set up SSH authorization by generating SSH keys on my local device using ```ssh-keygen``` and secure copying them into the cs15lwi23__@ieng6.ucsd.edu:~/.ssh/authorized_keys file on my ieng6 remote device

## Clone your fork of the repository from your Github account
I already had all my commands written out in a .txt document so I could easily use copy/paste to run the commands
I used ```<ctrl>+<c>```, ```<alt>+<tab>```, and ```<ctrl>+<v>``` to copy my commands from the .txt file into my terminal
To clone the respository, I copy/pasted the command ```git clone git@github.com:andrewzpu/lab7-try1.git```, which should look like this when run:
![image](https://user-images.githubusercontent.com/66804382/221475132-44cb1ce0-b545-4eb7-b97f-a244c4478e39.png)  
I used the SSH link git@github.com:andrewzpu/lab7-try1.git instead of the HTTP link https://github.com/andrewzpu/lab7 because this allows me to utilize my SSH keys for Github, which means I don't have to enter my username and password when pushing.  
I did this by generating SSH keys on my remote device using ```ssh-keygen``` and then copying the keys into my Github in Profile > Settings > Access > SSH and GPG keys > New SSH key

## Run the tests, demonstrating that they fail
Again, I used ```<ctrl>+<c>```, ```<alt>+<tab>```, and ```<ctrl>+<v>``` to copy my commands from the .txt file into my terminal
I first entered the directory by copy/pasting ```cd lab7``` and pressing ```<Enter>``` to run it, where "lab7" was the title of my repository  
![image](https://user-images.githubusercontent.com/66804382/221475314-9fc5a89f-068a-4d8d-8871-964b882bdb00.png)  
Then I copy/pasted ```javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java``` and pressed ```<Enter>``` to compile the java files
![image](https://user-images.githubusercontent.com/66804382/221475627-89adaaca-18be-4ee8-8402-87c512c08d67.png)  
As you can see, all the .java files were compiled into .class files
Finally, I ran the java test file by copy/pasting ```java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests``` and pressing ```<Enter>```, which resulted in the following screen
![image](https://user-images.githubusercontent.com/66804382/221475710-66a73021-04ac-4dc6-b405-7d4ec8ef42bf.png)  

## Edit the code file to fix the failing test
The error in the file that led to the error is that on line 43, the ```index1 += 1;``` line should be ```index2 += 1;``` to avoid an infinite loop  
I fixed this error by using ```<ctrl>+<c>```, ```<alt>+<tab>```, and ```<ctrl>+<v>``` to copy/paste the command ```sed -i '43s/index1 += 1;/index2 += 1;/g' ListExamples.java``` and pressing ```<Enter>```, which replaces the instance of ```index1 += 1;``` on line 43 with ```index2 += 1;```
Here is what lines 41 to 44 of the file looked like before the command was run:  
![image](https://user-images.githubusercontent.com/66804382/221476379-3998e850-0fa8-403b-b85d-dffbd62a2c17.png)  
And here is what these lines look like after the command is run:
![image](https://user-images.githubusercontent.com/66804382/221476719-ad37ff33-150d-4eaf-b75b-27ef3becf378.png)  

## Run the tests, demonstrating that they now succeed
I then used ```<ctrl>+<c>```, ```<alt>+<tab>```, and ```<ctrl>+<v>``` again to  copy/paste the commands to compile and run the tester again, which were ```javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java``` and ```java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests```, pressing ```<Enter>``` after each one. The result should look like this:  
![image](https://user-images.githubusercontent.com/66804382/221477155-348a76dd-61f6-452f-b73f-157ea6127fce.png)  
As you can see, the tests are now successful

## Commit and push the resulting change to your Github account
I then committed and pushed the changes to the Github repository using the commands ```git add ListExamples.java```, ```git commit -m "commit message lol"```, and ```git push```, pressing ```<Enter>``` after each one.
![image](https://user-images.githubusercontent.com/66804382/221478828-955886f0-8cf6-4748-ac10-cc64deceba82.png)  
As I said before, I set up my SSH keys in Github, so I didn't need to enter my Github username and password when I pushed.

## And Then You're Done!!!
