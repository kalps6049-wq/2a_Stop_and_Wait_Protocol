# 2a_Stop_and_Wait_Protocol
## AIM:
To write a python program to perform stop and wait protocol
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM:
### Server:
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
### Client:

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


## OUTPUT:
### Server:
<img width="1853" height="777" alt="Screenshot 2026-05-15 092538" src="https://github.com/user-attachments/assets/0992221f-00ed-4267-a2ea-c76744ec7f50" />

### Client:

<img width="1893" height="700" alt="Screenshot 2026-05-15 092558" src="https://github.com/user-attachments/assets/e9adc10f-a9d7-4216-99e9-ffdf5e894852" />


## RESULT:
Thus, python program to perform stop and wait protocol was successfully executed.
