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

client program:
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)

print("Waiting for connection...")
conn, addr = s.accept()
print("Connected to", addr)

while True:
    data = conn.recv(1024).decode()
    if not data:
        break

    print("Frame received:", data)
    conn.send("ACK".encode())

conn.close()

```

server program:

```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

n = int(input("Enter number of frames: "))

for i in range(n):
    msg = input("Enter frame: ")
    s.send(msg.encode())

    ack = s.recv(1024).decode()
    print("Received:", ack)

s.close()
```

## OUTPUT

CLIENT OUTPUT:

<img width="1917" height="1078" alt="Screenshot 2026-11-04 100025" src="https://github.com/user-attachments/assets/5f021260-7805-4f05-9fd9-5707b16de2b9" />

SERVER OUTPUT:

<img width="1917" height="1077" alt="Screenshot 2026-11-04 100033" src="https://github.com/user-attachments/assets/a2075e08-5a0e-4095-9104-04a919cc2a36" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
