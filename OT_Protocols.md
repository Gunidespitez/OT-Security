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
* Modbus RTU - Serial communication that uses a master slave architecture. For eg PLC (master) ---> Sensors(field devices/slaves). Uses Client-Server model.
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
