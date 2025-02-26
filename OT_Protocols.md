# Operational Technology:
* OT refers to physical world and systems that kkeeps industries running.
---------------------
## Consists of :<br />
### **Scada**(*Supervisory control and data acquisition*)- to monitor and control real time data and industrial processes.<br />
### **PLC**(*Programmable logic controllers*)- For automations like amusement rides, traffic light signal.<br />
### **ICS**(*Industrial control systems*)- Used in managing and automating industrial processes.<br />
### **HMI**(*Humar-Machine Interface*)- Displays data acquired by scada and allows to control Opertaion system.<br />
---------------------
## Communication Networks:(most important ones)
### Modbus- 
* Modbus RTU - Serial communication that uses a master slave architecture. For eg PLC (master) ---> Sensors(field devices/slaves). Uses Client-Server model. It organizes data in structures. The data types are - Coils,Discrete Inputs,Input Registers,Holding Registers.
Input registers is used to store data from sensors, while HR stores data that can be read or changed.
The modbus server runs on port 502.
It's Frame structure is like:
- Transaction ID (2 bytes and helps match request and responses , and also unique for each request.
- Protocol ID (2 bytes and always 0 for Modbus)
- Length	(2 bytes which is the remaining bytes in the message.)
- Unit Identifier	(1 byte	which is the address of the slave.)
- Function Code	(1 byte	which tells which action to perform , i.e like read/write)
- Data	(N bytes	which is the actual Data, that is stored in the register values).
Coils is used for simple ON/OFF information and Discrete Inputs is used to read the status of inputs from devices.
* Modbus TCP - Operates over Ehernet / IP networks to communicate over a network. It supports multiple devices easily. And it uses a Master-Slave communication
### OPC (Open platform communication)
* It allows different software and hardware in industrial systems to communicate easily. And acts like a translator between control systems like SCADA anf field ddvices like sensors.
* eg- Allows SCADA systems to communicate with PLCs 
### Profibus (Process Field Bus)
* It is used for factory automation and process automation systems for real-time communication between control systems and field devices.
* Further divided into two that is DP and PA
* DP- For high speed serial communication with sensors and actuators.
* PA- for communication in hazardous environments
### DNP3 (Distributed Network Protocol 3)
* Primarily used in Utility Industries such as water and electric systems, for SCADA systems and remote terminal unit (RTU) communications.
* It is Event-driven and secure
