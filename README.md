# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
```
DONE BY:JAI HARISH R
REG NO:212224040124
```
### server
```python
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
    while(i<len(l)):
        st +=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
            print(ack)
            i+=s
```
### client
```python
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())
```
## OUPUT

### server
<img width="1479" height="931" alt="image" src="https://github.com/user-attachments/assets/672bab33-f8bb-4936-83d2-8162cf364339" />



### client

<img width="1493" height="918" alt="image" src="https://github.com/user-attachments/assets/b9851989-9037-4645-9933-e0e45e58346c" />



## RESULT

Thus, python program to perform stop and wait protocol was successfully executed
