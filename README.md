# KWSB
Korewana-Web-Server-Builder (KWSB) is a powerful tool to build and configure web servers in a simple and easy way in Java

# Summary
1. [Introduction](#creating-the-kwsb-object)
2. [Useful Methods](#useful-methods)
1. [Code Example](#simple-web-server-example)

## Creating the KWSB Object
The KWSB object is created using its constructor

**Example**:
```java
KWSB kwsb = new KWSB();
```

### Adding routes
With the addition of routes, building the web server really begins. 

**Example**:
```java
kwsb.addRequestHandler("/", new GetRequestHandler() {
   @Override
   public void onRequest(Request req, Response res) {
      res.send("Hello World!");
   }
})
```

## Useful Methods
Here are a lot of useful methods and examples
### `Response#sendFile(File f)`
Send a file to the client. Content-Type will be set automatically

**Example**:
```java
@Override
public void onRequest(Request req, Response res) {
   res.sendFile(new File("path_to_file"));
}
```

## Simple Web-Server Example
```java
public static final int PORT = 80; //the port the server listens to
public static void main(String[] args) {
   KWSB kwsb = new KWSB(); //create the object
   
   //Add a handler to get route "/": localhost:80/
   kwsb.addRequestHandler("/", new GetRequestHandler() {
      @Override
      public void onRequest(Request req, Response res) {
         res.send("<h1>Hello World!</h1>"); //return "Hello World!" in a headline
      }
   });

   kwsb.listen(port, (server) -> { //start the server
      System.out.println("Server listening to "+server.getIPAddress()+":"+port); //print ip and port
   });
}
```
