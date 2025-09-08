# 2c : SIMULATING ARP /RARP PROTOCOLS
### Name : Prajin S
### Register Number : 212223230151
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
## PROGRAM - ARP
#### Client.py
```python
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"10.147.162.214":"E0-2E-0B-37-CE-B8","172.20.10.2":"52-D1-9C-21-AC-AD"}
while True:
    ip=c.recv(1024).decode()
    try:
     c.send(address[ip].encode())
    except KeyError:
     c.send("Not Found".encode())
```
#### Server.py
```python
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address : ",s.recv(1024).decode())
```
## OUPUT - ARP
<img width="858" height="112" alt="image" src="https://github.com/user-attachments/assets/02e7a1e4-cad6-480a-99dc-f4507a9a9caa" />
<img width="894" height="183" alt="image" src="https://github.com/user-attachments/assets/e7556525-eed7-4ea4-83e3-92462a819c6d" />


## PROGRAM - RARP
#### Client.py
```python
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"E0-2E-0B-37-CE-B8":"10.147.162.214","52-D1-9C-21-AC-AD":"172.20.10.2"}
while True:
    ip=c.recv(1024).decode()
    try:
     c.send(address[ip].encode())
    except KeyError:
     c.send("Not Found".encode())
```
#### Server.py
```python
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address : ",s.recv(1024).decode())
```
## OUPUT -RARP
<img width="894" height="76" alt="image" src="https://github.com/user-attachments/assets/75bef6f5-9c7e-49ef-8513-0efbd6fd3424" />
<img width="899" height="168" alt="image" src="https://github.com/user-attachments/assets/416677c4-d27e-48ba-a3c8-50a06c4f0740" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
