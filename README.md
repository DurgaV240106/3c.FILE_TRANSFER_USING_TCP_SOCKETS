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
```
Server

import socket

def send_file(client_socket, file_path):
    with open(file_path, 'rb') as file:
        data = file.read(1024)
        while data:
            client_socket.send(data)
            data = file.read(1024)

def main():
    host = '127.0.0.1'
    port = 12345

    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server_socket.bind((host, port))
    server_socket.listen(1)

    print(f"Server listening on {host}:{port}")

    client_socket, client_addr = server_socket.accept()
    print(f"Connection from {client_addr}")

    file_path = 'example.txt'

    send_file(client_socket, file_path)

    client_socket.close()
    server_socket.close()

if __name__ == "__main__":
    main()
```
```
Client

import socket

def receive_file(server_socket, file_path):
    with open(file_path, 'wb') as file:
        data = server_socket.recv(1024)
        while data:
            file.write(data)
            data = server_socket.recv(1024)

def main():
    host = '127.0.0.1'
    port = 12345

    client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    client_socket.connect((host, port))

    print(f"Connected to {host}:{port}")

    file_path = 'received_file.txt'

    receive_file(client_socket, file_path)

    client_socket.close()

if __name__ == "__main__":
    main()
```
## OUPUT

![Screenshot 2024-03-12 135716](https://github.com/DurgaV240106/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/144870878/597ec6b3-66b8-48c6-b46e-2354a8c9e812)
![Screenshot 2024-03-12 135809](https://github.com/DurgaV240106/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/144870878/a39c4945-0eca-4188-97fc-fe4b2d13718d)


## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
