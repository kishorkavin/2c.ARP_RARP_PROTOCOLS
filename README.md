# 2c.SIMULATING ARP /RARP PROTOCOLS

## Register Number: 212224230132
## Name: KISHORE KAVIN S

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
## Client Program:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
``` 
## Server Program:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical address: ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
````
## OUPUT - ARP
## Server
![image](https://github.com/Ragupathi1/2c.ARP_RARP_PROTOCOLS/assets/143526042/12f24d31-0288-480e-80d6-b687aaca8a9a)

## PROGRAM - RARP
PROGRAM - RARP
## Client Progam:
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"}
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not found".encode())    
```
## Server Program:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter mac address: ")
    s.send(ip.encode())
    print("Logical address",s.recv(1024).decode())
```
## OUPUT -RARP
 ## Server
![image](https://github.com/Ragupathi1/2c.ARP_RARP_PROTOCOLS/assets/143526042/4e28a981-aef7-472f-9bee-868871425210)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
