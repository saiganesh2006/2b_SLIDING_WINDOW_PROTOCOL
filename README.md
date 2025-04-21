# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM:
### Client:
```
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
    st+=s
    c.send(str(l[i:st]).encode())
    ack=c.recv(1024).decode()
    if ack:
    print(ack)
    i+=s
```

### Server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
  print(s.recv(1024).decode())
  s.send("acknowledgement received from the server".encode())
```
## OUPUT:

### Client:
![image](https://github.com/user-attachments/assets/9626cab9-a1b9-4822-9f2e-053497e8aa45)

### Server:
![image](https://github.com/user-attachments/assets/398c5833-49bd-4b10-a2f5-5b155bb94410)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
