# Sliding-Window-Protocol
## AIM 
## ALGORITHM:
1.Start the program.

2.Get the frame size from the user

3.To create the frame based on the user request.

4.To send frames to server from the client side.

5.If your frames reach the server it will send ACK signal to client

6.Stop the Program

## PROGRAM
## SERVER
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True: 
 print(s.recv(1024).decode())
 s.send("acknowledgement received from the server".encode())
```
## CLIENT
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
## OUPUT
## SERVER

<img width="1123" height="426" alt="image" src="https://github.com/user-attachments/assets/299ac9fb-5c00-4b54-afb7-8c30a2e536e6" />

## CLIENT

<img width="1196" height="433" alt="image" src="https://github.com/user-attachments/assets/1855abb3-8174-4484-afc7-5673a4b2561d" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
