# **Lab Report 3**

## Grep Command
The grep command is used to look for a certain String inside the contents of a file
The default format is as follows:
```
grep [String] [Filename]
```
Here is what it looks like when the default grep command is run with no options:
![image](https://user-images.githubusercontent.com/66804382/218346159-8fc7eb91-0e48-4fe3-b3ad-1ecbd74c4b3f.png)
In each location where the String pattern is found, the grep command prints the file it was found in, followed by the text that contains the String

## -l option
[Info from grep man page](https://linuxcommand.org/lc3_man_pages/grep1.html)

The -l option lists all the files that the String was found in and does not include the actual text
Here are the commands we ran before but with the -l option
![image](https://user-images.githubusercontent.com/66804382/218346408-59c4a8dd-d580-4707-aa4f-ba1f3e72e3f7.png)
As you can see, the same files are returned as the default grep we ran earlier, but the excess text after the file path are removed

## -f option
[Info from grep man page](https://linuxcommand.org/lc3_man_pages/grep1.html)

The -f option allows us to input a file, and the contents of the file are used as the String pattern
In the following code, we input the String pattern into a file before using the -f option to search
![image](https://user-images.githubusercontent.com/66804382/218346593-e8513cf5-4b94-4302-84c5-4dd8c0a5ba01.png)
Here, the output is exactly the same as the original commands we ran. The only difference is that we input a file as the String pattern.

## -r option
[Info from grep man page](https://linuxcommand.org/lc3_man_pages/grep1.html)

The -r option reads for the String pattern recursively through all the files in a directory
In the following code, we use the -r option and remove the "\*.txt" from the end of the file path. This command uses a directory as input instead of a file, and it will look through the entire directory.
![image](https://user-images.githubusercontent.com/66804382/218346768-a293d8c1-89a4-4b62-9a34-13b47dde84ec.png)
As you can see, the output is exactly the same since we looked through the same directory.

## -i option
[Info from grep man page](https://linuxcommand.org/lc3_man_pages/grep1.html)

The -i option means that the command will ignore the case of the characters
In the following code, we ran the original commands with the -i option. In the String pattern, we input the same pattern but in all lowercase.
![image](https://user-images.githubusercontent.com/66804382/218346916-55d47396-b288-4461-80aa-ed14fe448bb8.png)
As you can see, when we run the command without the -i option, nothing returns because the String pattern doesn't match. When we add the -i, the case doesn't matter and the pattern "lucayans" can match with "Lucayans."



