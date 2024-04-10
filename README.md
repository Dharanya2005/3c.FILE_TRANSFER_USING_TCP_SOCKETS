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
# client:
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
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
```
# server:
```
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
```
## OUTPUT
# client:
![Screenshot 2024-04-10 142823](https://github.com/Dharanya2005/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/145742468/95ed6808-bfc0-46fe-aea4-3bb2602fb25d)
# server:
![Screenshot 2024-04-10 142806](https://github.com/Dharanya2005/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/145742468/717ad11b-8bd3-4061-bbe6-5ac506646c4e)
## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
