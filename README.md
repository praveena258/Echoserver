# Echoserver
Echo server and client using python socket
# AIM:

To develop a simple webserver to serve html programming pages.

## DESIGN STEPS:

### Step 1:

HTML content creation is done

### Step 2:

Design of webserver workflow

### Step 3:

Implementation using Python code

### Step 4:

Serving the HTML pages.

### Step 5:

Testing the webserver

## PROGRAM:
server.py
```
import socket


HOST = "127.0.0.1" 
PORT = 65432  


with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.bind((HOST, PORT))
    s.listen()
    conn, addr = s.accept()
    with conn:
        print(f"Connected by {addr}")
        while True:
            data = conn.recv(1024)
            if not data:
                break
            conn.sendall(data)

```
client.py
```
import socket
from datetime import datetime

HOST = "127.0.0.1"  # The server's hostname or IP address
PORT = 65432        # The port used by the server

current_date = datetime.now().strftime("%d-%m-%Y")
message = f"PRAVEENA- 212224040248 - {current_date}"

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.connect((HOST, PORT))
    s.sendall(message.encode())
    
    data = s.recv(1024)

print(f"Received {data!r}")
```
##  Architecture Diagram

```bash
+--------------------------+
|  User's Web Browser      |
|  (Client: Chrome/Firefox)|
+-----------+--------------+
            |
            |  HTTP Request (GET /)
            v
+-----------+--------------+
|   Python Web Server      |
| (http.server + Handler)  |
| - Listens on Port 8000   |
| - Handles GET Requests   |
| - Sends HTML Response    |
+-----------+--------------+
            |
            |  HTML Response
            v
+--------------------------+
|  User Sees Rendered Page |
|  <h1>Hello Web Server</h1>|
+--------------------------+
```


## OUTPUT:
<img width="1486" height="884" alt="image" src="https://github.com/user-attachments/assets/26dd8663-372f-4a72-860a-cef7416c55ac" />

### CLIENT OUTPUT:
<img width="1386" height="304" alt="image" src="https://github.com/user-attachments/assets/e98de0d7-9046-443d-a957-a016473c2715" />

### SERVER OUTPUT:
<img width="1395" height="290" alt="image" src="https://github.com/user-attachments/assets/4cd220d0-7cf4-4df8-8dc3-5826a35c0f91" />


## RESULT:
The program is executed succesfully
