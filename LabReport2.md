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
Any port number between 1024 and 49151 should work (replace 4000)

## StringServer in action:
First Input:  
![StringServerExample](Lab%202/Hello.png)  
1. Runs the handleRequest() method with the URI object with url "http://localhost:4000/add-message?s=Hello" as the parameter.  
2. This in turn also runs the getPath() method with the same URI, which should return "add-message"  
3. This is compared to the expected String "add-message" using the .equals method, and since they are the same, the if block is executed  
4. The getQuery() method is run with the same URI, which should return "s=Hello"  
5. The .split command separates the query with "=" as the delimeter
6. The queryParam String array is then set to {"s", "Hello"}  
7. The .equals method compares queryParam[0] to "s", and since they are equivalent, this if block is also run, which adds "Hello\n" to the end of the output, which was initially an empty String  
8. output is then returned, which causes it to be displayed on the page as:  
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
2. This in turn also runs the getPath() method with the same URI, which should return "add-message"  
3. This is compared to the expected String "add-message" using the .equals method, and since they are the same, the if block is executed  
4. The getQuery() method is run with the same URI, which should return "s=Even Though I Look Like A Burnt Chicken Nugget"  
Note: The "%20"s are converted back to space characters
5. The .split command separates the query with "=" as the delimeter
6. The queryParam String array is then set to {"s", "Even Though I Look Like A Burnt Chicken Nugget"}  
7. The .equals method compares queryParam[0] to "s", and since they are equivalent, this if block is also run, which adds "Even Though I Look Like A Burnt Chicken Nugget\n" to the end of the output, which was initially just "Hello\n"
8. output is then returned, which causes it to be displayed on the page as:  
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
public void reversedTestFail() {
  int[] input1 = {1};
  assertArrayEquals(new int[]{1}, ArrayExamples.reversed(input1));
}
```

2. The following JUnit test resulted in a success:
```
@Test
public void reversedTestPass() {
  int[] input1 = {0};
  assertArrayEquals(new int[]{1}, ArrayExamples.reversed(input1));
}
```

3.
Here is what it looks like when these two tests are run. As you can see, the first test failed because the returned array was {0} instead of {1}.
![JUnit Tests](https://user-images.githubusercontent.com/66804382/215600161-e211d6fc-e64e-4dab-8bc2-e93438f7ba03.png)

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
  return newArray;
}
```
The new code works because we switched the "newArray" and "arr" in the 4th line  
The original code sets the input array (arr) equal to the reverse of the newly created array (newArray), which just sets all the values to 0.  
After we fixed the code, each element of the new array (newArray) is replaced by the elements of the input array (arr) in reverse order, and then the newArray (reversed array) is returned, which is correct.

# **Part 3: Reflect**
Before lab 2, I didn't know how to set up a web server through Java. In the lab, I learned how to host a web server from my own device and through SSHing into another device.
