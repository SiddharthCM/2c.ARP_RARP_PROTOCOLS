# 2c.SIMULATING ARP /RARP PROTOCOLS
## Date - 4.11.26
## Name: Siddharth CM
## Reg.no: 212225040413
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

```py
server.py

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


client.py

import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())

```


## OUPUT - ARP
server:

<img width="824" height="702" alt="image" src="https://github.com/user-attachments/assets/07729432-abd0-4e09-b837-3eb7e6aedbb1" />

client:

<img width="816" height="170" alt="image" src="https://github.com/user-attachments/assets/75053fe9-b943-41eb-92d0-56f8db0f921a" />

## PROGRAM - RARP
```py
server.py

import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())

client.py

import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())

```

## OUPUT -RARP

server:

<img width="880" height="694" alt="image" src="https://github.com/user-attachments/assets/c1aded61-5753-4e2f-8508-2fde1d617a3f" />


client:
<img width="890" height="700" alt="image" src="https://github.com/user-attachments/assets/844503c3-d2b0-4729-bd38-ca3dc73724b5" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
