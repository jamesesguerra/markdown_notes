---
attachments: [Clipboard_2022-07-30-20-18-08.png, Clipboard_2022-07-30-20-27-14.png]
tags: [Notebooks/Head First Java]
title: 'Chapter 13: Networking'
created: '2022-07-30T06:13:52.725Z'
modified: '2022-07-31T14:00:30.712Z'
---

# Chapter 13: Networking

Connecting to the outside world is made easy with Java by the classes in the `java.net` library. Sending and receiving data over a network is just I/O with a slightly different connection stream at the end of the chain. 

### Connecting, Sending, and Receiving

1. __Connect__ - Client connects to the server by establishing a __Socket__ connection.
2. __Send__ - Client __sends__ a message to the server.
3. __Receive__ - Client __gets__ a message from the server.

### Socket Connection

You need a Socket connection to connect to another machine. A __Socket__ (`java.net.Socket` class) is an object that represents a network connection between two machines. A connection is a relationship between two machines where two pieces of software know about each other. They know how to communicate by sending bits to each other. 

To make a Socket connection, you need to know two things about the server: who it is and which port it's running on. In other words, __IP Address and TCP port number.__ A socket connection means two machines have information about each other, including IP address and TCP port.

```java
Socket mySocket = new Socket("196.164.1.103", 5000);
```

### Ports

A TCP port is just a 16-bit number that identifies a specific program on the server. They're just numbers representing an application. Without port numbers, the server would have no way of knowing which application a client wanted to connect to. 

When you write a server program, you'll include code that tells the program which port number you want it to run on. Ideally this is a number between 1024 and 65,535 since TCP port numbers from 0 to 1023 are reserved for well-known services.

### Reading from a Socket

To read data from a Socket, use a `BufferedReader`. You can use regular I/O streams since most of your I/O work won't care what your high-level chain stream is actually connected to. You can use a `BufferedReader` just like how you would when you write to a file. The only difference is that the underlying connection stream is connected to a Socket rather than a file.

1. __Make a Socket connection to the server__
```java
// localhost IP address
Socket mySocket = new Socket("127.0.0.1", 5000);
```

2. __Make an `InputStreamReader` chained to the Socket's low-level (connection) input stream__
`InputStreamReader` is a "bridge" between a low-level byte stream (like the one coming from a Socket) and a high-level character stream (like the `BufferedReader` we're after as our top of the chain stream).

All you have to do is ask the Socket for an input stream:
```java
InputStreamReader stream = new InputStreamReader(mySocket.getInputStream());
```

3. __Make a `BufferedReader` and read__
Chain the `BufferedReader` to the `InputStreamReader` (which was chained to the low-level connection stream we got from the Socket)

```java
BufferedReader reader = new BufferedReader(stream);
String message = reader.readLine();
```
![](@attachment/Clipboard_2022-07-30-20-18-08.png)

### Writing to a Socket

When you're writing one `String` at a time, using `PrintWriter` is the standard choice. Its two key method are `print()` and `println()`.

1. __Make a Socket connection to the server__
```java
Socket mySocket = new Socket("127.0.0.1", 5000);
```

2. __Make a `PrintWriter` chained to the Socket's low-level (connection) output stream__
`PrintWriter` acts as its own bridge between character data and the bytes it gets from the Socket's low-level output stream. By chaining a `PrintWriter` to the Socket's output stream, we can write `String`s to the Socket connection.

The Socket gives us a low-level connection stream and we chain it to the `PrintWriter` by giving it to the `PrintWriter` constructor.
```java
PrintWriter writer = new PrintWriter(mySocket.getOutputStream());
```

3. __Write something__
```java
// println adds a new line at the end
writer.println("message to send");
// print doesnt add the new line
writer.print("another message");
```

![](@attachment/Clipboard_2022-07-30-20-27-14.png)

### Writing a server application

All you need to write a server application is a `ServerSocket` which waits for client requests (when a client makes a new `Socket()`) and a plain old Socket socket to use for communication with the client.

1. Server application makes a `ServerSocket` on a specific port. This starts the server application listening for client requests coming in for port 4242.
```java
ServerSocket serverSock = new ServerSocket(4242);
```

2. Client makes a Socket connection to the server application. Client knows the IP address and port number.
```java
Socket sock = new Socket("190.165.1.103", 4242);
```

3. Server makes a new Socket to communicate with this client. The `accept()` method blocks (just sits there) while it's waiting for a client Socket connection. When a client finally tries to connect, the method returns a plain old Socket (on a different port) that knows how to communicate with the client. The Socket is on a different port than the ServerSocket, so that the ServerSocket can go back to waiting for other requests.

#### Client code
```java
import java.io.*;
import java.net.*;

public class AdviceClient {
	
	public static void main(String[] args) {
		try {
			Socket s = new Socket("127.0.0.1", 5000);
			
			InputStreamReader streamReader = new InputStreamReader(s.getInputStream());
			BufferedReader reader = new BufferedReader(streamReader);
			
			String advice = reader.readLine();
			System.out.println("Today you should " + advice);
			
			reader.close();
		} catch(IOException ioe) {
			ioe.printStackTrace();
		}
	}
}
```

#### Server code
```java
import java.io.*;
import java.net.*;

public class Main {
	
	public static void main(String[] args) {
		try {
			ServerSocket serverSock = new ServerSocket(5000);
			System.out.println("Server running on port 5000...");
			
			while (true) {
				Socket sock = serverSock.accept();
				
				PrintWriter writer = new PrintWriter(sock.getOutputStream());
				String advice = "get a life";
				
				writer.println(advice);
				writer.close();
			}
		} catch(IOException ioe) {
			ioe.printStackTrace();
		}		
	}
}
 
```

### Writing a ChatClient

You can send messages to the server but you don't get to read any messages from other participants. 

__Big question:__ how do you get messages from the server? Doing option three is reading messages as soon as they're sent. However, how do you do two things at the same time? Threads (see threads).




