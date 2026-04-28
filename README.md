# Ex.No:1 (a)    Study of Socket Programming
## Name : JAIRAM J
## Ref No : 25012221
## Aim: 
To perform a study on Socket Programming
## Introduction:

 	Socket programming is a crucial aspect of network communication, allowing for data exchange between computers over a network. It forms the backbone of various networked applications, enabling communication between clients and servers. This study explores the fundamental concepts of socket programming, its use cases, and provides a practical example to demonstrate its implementation.
## Understanding Socket Programming:
	Socket programming involves the use of sockets, which serve as endpoints for communication. A socket is identified by an IP address and a port number, and it facilitates data transfer between a client and a server. The two main types of sockets are Stream Sockets, which provide a reliable, connection-oriented communication, and Datagram Sockets, which are connectionless and suitable for scenarios where reliability is less critical.
## Key Concepts in Socket Programming:
1.Sockets
•	A socket is a software representation of a communication endpoint in a network.
•	It is identified by an IP address and a port number.
•	Sockets can be classified into two main types: Stream Sockets and Datagram Sockets.
•	Stream Sockets provide a reliable, connection-oriented communication, while Datagram Sockets are connectionless and operate in a best-effort mode.

2. Client-Server Model

•	Socket programming typically follows the client-server model.
•	The server listens for incoming connections from clients, while clients initiate connections to the server.
•	Servers are passive, waiting for connection requests, and clients are active, initiating communication.

3, TCP/IP Protocol:

•	Transmission Control Protocol (TCP) and Internet Protocol (IP) are the foundational protocols for socket programming.
•	TCP provides reliable, connection-oriented communication, ensuring data integrity and order.
•	IP facilitates the routing of data between devices in a network.

4.Basic Socket Functions:

•	Socket programming involves a set of functions provided by the operating system or programming language to create, bind, listen, accept, connect, send, and receive data through sockets.
•	Examples of functions include socket(), bind(), listen(), accept(), connect(), send(), and recv().

## Server-Side Operations:

•	Servers create a socket using socket() and bind it to a specific IP address and port using bind().
•	They then listen for incoming connections with listen() and accept connections with accept().
•	Once a connection is establi
•	shed, servers can send and receive data using send() and recv().

## Client –Server Operations

Clients create a socket using socket() and connect to a server using connect().
After establishing a connection, clients can send and receive data using send() and recv().

## Use Cases of Socket Programming:
Socket programming finds applications in various domains, including web development, file transfer protocols, online gaming, and real-time communication. It is the foundation for protocols like HTTP, FTP, and SMTP, which power the internet. Socket programming enables the development of both server and client applications, facilitating the exchange of information between devices in a networked environment.
## Example Use Cases:

1.	Web servers: Web servers use socket programming to handle incoming HTTP requests from clients, serving web pages and content.
2.	Chat Application: Instant messaging and chat applications use sockets to enable real-time communication between users.
3.	File Transfer Protocol: Protocols like FTP (File Transfer Protocol) utilize socket programming for transferring files between a client and a server.
4.	Networked Games: Online multiplayer games rely on socket programming to facilitate communication between game clients and servers.
5.	RPC mechanisms: which allow processes to execute code on a remote server, often use socket programming for communication.

## CODE's...

### 1) Clint Side
```
import socket
import time

def client():
    time.sleep(1)

    client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    client_socket.connect(('127.0.0.1', 12345))

    messages = [
        "hii buddy!",
        "what is Computer Network?",
        "Thank you"
    ]

    for msg in messages:
        client_socket.send(msg.encode())
        response = client_socket.recv(1024).decode()
        print("Server:", response)
        time.sleep(1)

    client_socket.close()

```
### 2) Server Side
```
import socket
import threading
import time

def server():
    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server_socket.bind(('127.0.0.1', 12345))
    server_socket.listen(1)

    conn, addr = server_socket.accept()
    print("Server connected to client")

    while True:
        data = conn.recv(1024).decode()

        if not data:
            break

        print("Client:", data)

        if "hii buddy!" in data.lower():
            reply = "Hello! Welcome !! What you want  😊"
        elif "what is computer network?" in data.lower():
            reply = "A interconnected group of computing devices (like computers, servers, and phones) that use shared protocols to exchange data and share resources.🔥"
        elif "thank you" in data.lower():
            reply = "Welcome !!If you need anythig come ..... Connection closing..."
            conn.send(reply.encode())
            break
        else:
            reply = "I didn't understand that. Ask about Computer Network related  or say hii buddy"

        conn.send(reply.encode())

    conn.close()
    server_socket.close()
```

## Full Functional Code...
```
import socket
import threading
import time

def server():
    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server_socket.bind(('127.0.0.1', 12345))
    server_socket.listen(1)

    conn, addr = server_socket.accept()
    print("Server connected to client")

    while True:
        data = conn.recv(1024).decode()

        if not data:
            break

        print("Client:", data)

        if "hii buddy!" in data.lower():
            reply = "Hello! Welcome !! What you want  😊"
        elif "what is computer network?" in data.lower():
            reply = "A interconnected group of computing devices (like computers, servers, and phones) that use shared protocols to exchange data and share resources.🔥"
        elif "thank you" in data.lower():
            reply = "Welcome !!If you need anythig come ..... Connection closing..."
            conn.send(reply.encode())
            break
        else:
            reply = "I didn't understand that. Ask about Computer Network related  or say hii buddy"

        conn.send(reply.encode())

    conn.close()
    server_socket.close()


def client():
    time.sleep(1)

    client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    client_socket.connect(('127.0.0.1', 12345))

    messages = [
        "hii buddy!",
        "what is Computer Network?",
        "Thank you"
    ]

    for msg in messages:
        client_socket.send(msg.encode())
        response = client_socket.recv(1024).decode()
        print("Server:", response)
        time.sleep(1)

    client_socket.close()


threading.Thread(target=server).start()
threading.Thread(target=client).start()
```


## Output.
<img width="1287" height="482" alt="Screenshot 2026-04-28 152227" src="https://github.com/user-attachments/assets/aa9de4fd-0467-4296-aa67-a6487405858e" />



## Result:
Thus the study of Socket Programming Completed Successfully
