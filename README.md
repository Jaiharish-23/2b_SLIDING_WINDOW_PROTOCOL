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
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())
```
### client
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
## OUPUT

### server
<img width="1344" height="843" alt="{2F580F88-2780-4A0F-9A62-688BADD7FD2B}" src="https://github.com/user-attachments/assets/159a96f3-af1b-4bd3-ab0e-9d5b5dd19e1b" />


### client

<img width="1350" height="912" alt="{387C7A0A-1E7D-49AB-9C44-9709C6D19206}" src="https://github.com/user-attachments/assets/bb658068-ff49-4660-9214-7c209e65dac3" />



## RESULT

Thus, python program to perform stop and wait protocol was successfully executed
