# **String Server**

## Setting Up The Server
First, I have to have the initial Server.java file that makes a simple web server using Java's HttpServer package:
![Server.java](Lab%202/Server.png)  

Here is the code for my own StringServer java file:
![StringServer.java](Lab%202/StringServer.png)

To initialize the server, use the following terminal commands:
```
javac Server.java StringServer.java
java StringServer 4000
```
Any port number between 1024 and 49151 (replace 4000)

## StringServer in action:
First Input:  
![StringServerExample](Lab%202/Hello.png)  
1. Runs the handleRequest() method with the URI object with url "http://localhost:4000/add-message?s=Hello" as the parameter.  
2. This in turn also runs the getPath() method with the same URI, which should return "add-message"  
3. This is compared to the expected String "add-message" and since they are the same, the if block is executed  
4. The getQuery() method is run with the same URI, which should return "s=Hello"  
5. The queryParam String array is then set to {"s", "Hello"}  
6. Since queryParam[0] is equivalent to "s", this if block is also run, which adds "Hello\n" to the end of the output, which was initially an empty String  
7. output is then returned, which causes it to be displayed on the page as:  
"Hello"
```
public String handleRequest(URI url) {
    if (url.getPath().equals("/add-message")) {
        String[] queryParam = url.getQuery().split("=");
        if (queryParam[0].equals("s")) {
            output += queryParam[1] + "\n";
            return output;
        }
    }
    
    return "404 Not Found!";
}
```

Second Input:  
![StringServerExample2](Lab%202/Chicken.png)
