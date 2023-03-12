# **Lab Report 5**

## Lab 7 Speed Competition

In order to save time for this competition, I put all the commands I used into a txt document, and then I copied them into the terminal all together so they would all run consecutively  
I first SSHed into my machine using the following command: ```ssh cs15lwi23aug@ieng6.ucsd.edu```  
Then, within the machine, the commands I used were as follows:
```
git clone git@github.com:andrewzpu/lab7-try1.git  
cd lab 7  
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java  
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests  
sed -i '43s/index1 += 1;/index2 += 1;/g' ListExamples.java  
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java  
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests  
git add ListExamples.java  
git commit -m "commit message lol"  
git push
```  
Instead of using vim or nano to edit the text document, I used the ```sed``` command to edit the file without physically using a text editor.

I could've have made this simpler by putting all the commands I listed into a bash script and just running the bash script.  
Another member of my lab group also performed the task extremely quickly by SSHing into the machine before the competition and cacheing the connection to avoid the
delay caused by the initial connecting through SSH.
