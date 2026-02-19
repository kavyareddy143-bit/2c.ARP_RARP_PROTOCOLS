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
```
client.py
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
server.py

import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True: 
    ip=input("Enter logical Address : ") 
    s.send(ip.encode()) 
    print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
<img width="1385" height="503" alt="image" src="https://github.com/user-attachments/assets/fc0cc9c2-30c4-4185-998e-7044dc7d5c77" />
<img width="1417" height="521" alt="image" src="https://github.com/user-attachments/assets/6cd16894-8859-4f0c-8efc-6b3f91861d81" />

## PROGRAM - RARP
```
client.py
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
server.py
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
    ip=input("Enter MAC Address : ")
    s.send(ip.encode()) 
    print("Logical Address",s.recv(1024).decode())

```
## OUPUT -RARP
<img width="1009" height="251" alt="image" src="https://github.com/user-attachments/assets/3cf2f048-c87a-4d7f-91c9-acb24f8ec794" />
<img width="1018" height="394" alt="image" src="https://github.com/user-attachments/assets/5b0eaab7-bd41-4e31-84a9-5a5f7aa589a7" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
