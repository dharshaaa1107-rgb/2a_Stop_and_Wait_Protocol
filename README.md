# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)

print("Server started... Waiting for connection...")
c, addr = s.accept()
print("Connected with:", addr)

while True:
    i = input("Enter data: ")
    c.send(i.encode())

    ack = c.recv(1024).decode()

    if ack:
        print("Client:", ack)
        continue
    else:
        c.close()
        break
```
server code:

```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    data = s.recv(1024).decode()
    if not data:
        break
    print(data)
    s.send("Acknowledgement Received".encode())
```

## OUTPUT
<img width="1186" height="276" alt="image" src="https://github.com/user-attachments/assets/b12f9d11-0c9f-4b19-9e4a-86995d075b73" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
