# MITM Attack using Modbus Simulator
## INTRODUCTION TO THE TASK:
The modbus TCP works on client server model which is a request response model, where the client requests server for some particular data and the server responds to it. IN MITM the client thinks it’s talking directly to the server and the server thinks it’s talking directly to the client but actually, MITM is intercepting everything between them, and sends a changed data to the client. Instead of connecting to the Server's port , the client gets connected to the MITM proxy port. When the client asks for register values, MITM forwards this request to the real server,and then MITM intercepts the server's response. 

-------------------
## SERVER
The server waits for requests from the client, that is the person asking questions, and it then responds with the correct value. 
![server](https://github.com/user-attachments/assets/49ca2a16-8232-43d6-a726-9fb9c1d0dfb8)
### Working:
* Imported important libraries:
    - imported StartTcpServer ( which is used to start a Modbus TCP server) from the pymodbus Library
    - imported ModbusSequentialDataBlock ( which stores Modbus registers like a list and we are using it to represent holding registers the server will hold.
    - imported ModbusSlaveContext and ModbusServerContext ( which are used to represent the data for slave and server device respectively)
* Set a variable reg for storing data in the registers, where the starting address is O and it creates a list of 100 registers with all the value of 10.
* We then create a slave to hold the slave data.
* hr = reg means we are assigning all the registers in the form of holding registers to the Slave.
* We then make a variable server to hold all server data and by doing slaves = slave we assign slave data to server. Further , single = true tells us there's only one slave device.
* We then start the Modbus TCP server and we define the address and port where the server will be running.
* The address 0.0.0.0 means server will listen on all available network interfaces
* 5025 is the port number that the server listens to and the client must connect using the same port number.
--------------------
## CLIENT
### Working:
![client](https://github.com/user-attachments/assets/bc330944-5333-467b-a2aa-1fb0b886c716)
* We import ModbusTcpClient that is the client part of PyModbus which can communicate with the Modbus server over TCP.
* We define a variable client to store client data and it runs on address of localhost that is (127.0.0.1) and we connect it to the port where the server is listening.
* We then create a loop so the client can keep asking which register they want to see and it asks for a user input and reads the particular register.
* Then we read the holding register at the address specified by user input a and we store it in a var called response.
* The response will contain the value retrieved from the server
* It then checks if theres an error in getting data , if not it prints the value of requested register
* Then we manually close the connection.

--------------------
## MAN IN THE MIDDLE 
### Working:
![MITM](https://github.com/user-attachments/assets/ed45de90-375f-4744-91c5-57ba2bd3a924)
* MITM Script intercepts the data and modifies it.
* Here in our script we are going to modify all even registers to 50 and odd registers remain same - 10
* We import socket library; which allows python to create network connections.
* We then define all the connection parameters, i.e , the server host port and mitm host port
* We then create a mitm socket , AF_INET specifies that the addresses are IPv4 type and SOCK_Stream specifies its a TCP connection
* We bind the MITM to host and port and we listen for any incoming connections
* We create a client_socket to communicate with the client.
* The var server_socket forwards client requests to the actual server.
* Then we make a loop which continously sends and recieves data in 4096 bytes, if data is not recieved connection is closed.
* Since the modbus TCP has the first 7 bytes already reserved for connection management and then theres a function code so register address always starts at 9
* We then shift the high bit by 8 bits to the left , which is same as multiplying it with 256 and add a low byte as the  full number is a combination of high and low bit
* We then send the client's request directly to the server from mitm and waits to recv a response.
* We convert the response that we get into a bytearray, so we can modify the data later.
* since the actual register value starts at 9, we set the index as 9.
* We then convert it to original value of register by multiplying thr high byte w 256 and add the low byte at index 10
* We at last modify the register value based on the reg number, as if irt is even the value changes to 50 else it remains same.
* Wr again reconstruct it in the format suitable for client by dividing high byte by 256 and modulus gives the low byte.
* We then send the modified server response back to the client.
The client now sees manipulated data for even-numbered registers and original data for odd-numbered registers.

### Before MITM:
![Before MITM](https://github.com/user-attachments/assets/ad7a074b-298d-4418-8c1f-9466276c8b2a)

### After MITM:
![After MITM](https://github.com/user-attachments/assets/b7925cc0-f88f-46fc-b48f-94d47af01707)
