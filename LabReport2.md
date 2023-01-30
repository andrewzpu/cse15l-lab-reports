# **Part 1: String Server**

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
1. Runs the handleRequest() method with the URI object with url "http://localhost:4000/add-message?s=Even%20Though%20I%20Look%20Like%20A%20Burnt%20Chicken%20Nugget" as the parameter.  
Note: A space character in the path or query is changed to "%20"
3. This in turn also runs the getPath() method with the same URI, which should return "add-message"  
4. This is compared to the expected String "add-message" and since they are the same, the if block is executed  
5. The getQuery() method is run with the same URI, which should return "s=Even Though I Look Like A Burnt Chicken Nugget"  
Note: The "%20"s are converted back to space characters
7. The queryParam String array is then set to {"s", "Even Though I Look Like A Burnt Chicken Nugget"}  
8. Since queryParam[0] is equivalent to "s", this if block is also run, which adds "Even Though I Look Like A Burnt Chicken Nugget\n" to the end of the output, which was initially just "Hello\n"
9. output is then returned, which causes it to be displayed on the page as:  
"Hello  
Even Though I Look Like A Burnt Chicken Nugget"
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

# **Part 2: Bugs**
Here is the reversed method that we were given:
```
static int[] reversed(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = newArray[arr.length - i - 1];
  }
  return arr;
}
```

1. The following JUnit test resulted in a failure:
```
@Test
public void reversedTest() {
  int[] input1 = {1};
  assertArrayEquals(new int[]{1}, ArrayExamples.reversed(input1));
}
```

2. The following JUnit test resulted in a success:
```
@Test
public void reversedTest() {
  int[] input1 = {0};
  assertArrayEquals(new int[]{1}, ArrayExamples.reversed(input1));
}
```

3.
*** Incomplete ***

4. Here is the original incorrect code and fixed code for the reversed method  
Before:
```
static int[] reversed(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = newArray[arr.length - i - 1];
  }
  return arr;
}
```
After:
```
static int[] reversed(int[] arr) {
  int[] newArray = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    newArray[i] = arr[arr.length - i - 1];
  }
  return arr;
}
```
This code works because we switched the "newArray" and "arr" in the 4th line  
The original code sets the input array (arr) equal to the reverse of the newly created array (newArray), which just sets all the values to 0.  
After these two values are switched, each element of the new array (newArray) is replaced by the elements of the input array (arr) in reverse order, which is correct.

# **Part 3: Reflect**
Before lab 2, I didn't know how to set up a web server through Java. In the lab, I learned how to host a web server from my own device and through SSHing into another device.
