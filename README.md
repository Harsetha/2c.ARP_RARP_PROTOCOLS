# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
### Client:
import socket   
s=socket.socket()    
s.bind(('localhost',8000))    
s.listen(5)    
c,addr=s.accept()    
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}; while True:    
ip=c.recv(1024).decode()    
try:    
c.send(address[ip].encode())   
except KeyError:   
c.send("Not Found".encode())   

### Server:
import socket    
s = socket.socket()    
s.connect(('localhost',8000))    
while True:   
ip = input("Enter logical address: ")   
s.send(ip.encode())    
print("MAC Address",s.recv(1024).decode())    

## OUPUT - ARP
### client:
![320836752-f29e2182-0d63-40e0-b953-0e7ec5749fca](https://github.com/Harsetha/2c.ARP_RARP_PROTOCOLS/assets/149985878/15ad4580-9e2a-4b1b-8106-81e9a09ab262)

### Server:
![320836871-57768d61-b90b-4fa1-8709-ae97ecdc6e3b](https://github.com/Harsetha/2c.ARP_RARP_PROTOCOLS/assets/149985878/0387f564-b43d-4d2e-b481-1e2b79eecaef)

## PROGRAM - RARP

### Client:
```
import socket   
s = socket.socket()    
s.bind(('localhost',8000))   
s.listen(5)    
c,addr = s.accept()    
address = {"6A:08:AA:C2":"165.165.80.1","8A:BC:E3:FA":"165.165.79.1"}   
while True:   
ip = c.recv(1024).decode()   
try:    
c.send(address[ip].encode())   
except KeyError:    
c.send("Not Found".encode())   
```
### Server:
```
import socket   
s = socket.socket()    
s.connect(('localhost',8000))   
while True:    
ip = input("Enter MAC address: ")    
s.send(ip.encode())   
print("Logical Address",s.recv(1024).decode())
```   

## OUPUT -RARP

### client:

![320838357-84b84a2b-9049-4d38-b8c4-4b518287dee3](https://github.com/Harsetha/2c.ARP_RARP_PROTOCOLS/assets/149985878/25d0a969-09dc-4a84-a819-805d8c043512)


### server:

![320839199-1fb76e5a-b398-4253-8147-990588ced9c4](https://github.com/Harsetha/2c.ARP_RARP_PROTOCOLS/assets/149985878/bbb3095a-b70a-4f9a-aebd-260ce6745c78)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
