# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
~~~
Server.py
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
while True:
    conn, addr = s.accept()
    data = conn.recv(1024)
    print('Server received', repr(data))
    filename='mytext.txt'
    f = open(filename,'rb')
    l = f.read(1024)
    while (l):
        conn.send(l)
        print('Sent ',repr(l))
        l = f.read(1024)
    f.close()
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.close()


~~~
~~~
Client.py
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('mytext.txt', 'wb') as f:
 while True:
    print('receiving data...')
    data = s.recv(1024)
    print('data=%s', (data))
    if not data:
        break
    f.write(data)
f.close()
print('Successfully get the file')
s.close()
print('connection closed')
~~~
## OUPUT
server.py and client.py
<img width="1047" height="326" alt="Screenshot 2026-03-17 124316" src="https://github.com/user-attachments/assets/52251350-95d8-4a29-9096-5e47da4f002d" />
<img width="1048" height="196" alt="Screenshot 2026-03-17 144208" src="https://github.com/user-attachments/assets/d7176e2a-6402-4c0f-95ac-7bec7eb5ffae" />





## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
