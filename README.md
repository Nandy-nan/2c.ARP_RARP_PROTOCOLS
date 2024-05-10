# 2c.SIMULATING ARP /RARP PROTOCOLS
NANDHANA.R(212223040124)
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
CLIENT PROGRAM
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
SERVER PROGRAM
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical address: ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```

## OUPUT - ARP
SERVER
![Screenshot 2024-05-10 211217](https://github.com/Nandy-nan/2c.ARP_RARP_PROTOCOLS/assets/153698914/ca929647-3ba0-4ad5-91ed-a490a304fbee)

CLIENT 
![Screenshot 2024-05-10 211207](https://github.com/Nandy-nan/2c.ARP_RARP_PROTOCOLS/assets/153698914/f557db14-6614-4c5b-9fb4-223d6a6185f7)


## PROGRAM - RARP
CLIENT
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
SERVER
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
![Screenshot 2024-05-10 212346](https://github.com/Nandy-nan/2c.ARP_RARP_PROTOCOLS/assets/153698914/6fe27423-f6d2-4e12-b57a-cfa8ea0f562e)

![Screenshot 2024-05-10 212339](https://github.com/Nandy-nan/2c.ARP_RARP_PROTOCOLS/assets/153698914/7c75bc1f-8825-4eeb-b6f3-37a76ed14339)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
