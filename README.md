# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM
## SERVER
~~~
import socket

# Create socket
s = socket.socket()

# Bind IP and port
s.bind(('localhost', 8000))

# Start listening
s.listen(5)
print("Server is waiting for connection...")

# Accept connection
c, addr = s.accept()
print("Connected to:", addr)

while True:
    # Receive message from client
    client_message = c.recv(1024).decode()

    # Stop if client disconnects
    if not client_message:
        break

    print("Client >", client_message)

    # Input message from server
    msg = input("Server > ")

    # Send message to client
    c.send(msg.encode())

# Close connection
c.close()
s.close()

~~~
## CLIENT
~~~
import socket

# Create socket
s = socket.socket()

# Connect to server
s.connect(('localhost', 8000))

print("Connected to server")

while True:
    # Take input from client
    msg = input("Client > ")

    # Send message to server
    s.send(msg.encode())

    # Receive message from server
    server_reply = s.recv(1024).decode()

    print("Server >", server_reply)

# Close socket
s.close()
~~~
## RESULT
## CLIENT 
<img width="297" height="110" alt="image" src="https://github.com/user-attachments/assets/cec6930a-65cf-4384-9c98-009331b5d7d4" />
~~~
## SERVER
<img width="591" height="117" alt="image" src="https://github.com/user-attachments/assets/a5598260-a9eb-4f6a-b671-8fd14ceff33f" />
~~~


Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
