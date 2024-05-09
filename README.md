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
### CLIENT:
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
### SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True: 
 print(s.recv(1024).decode())
 s.send("acknowledgement recived from the server".encode())
```
## OUPUT
### CLIENT:
![Screenshot 2024-03-09 113420](https://github.com/Harevasu/2b_SLIDING_WINDOW_PROTOCOL/assets/147985044/d7c652b7-676b-4294-8808-c53cec509f26)
### SERVER:
![Screenshot 2024-03-09 113443](https://github.com/Harevasu/2b_SLIDING_WINDOW_PROTOCOL/assets/147985044/ae5ba94f-6563-4e78-af04-c22915fa354a)
## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
