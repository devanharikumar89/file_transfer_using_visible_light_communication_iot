Host2 Code
SerialConsole.py/SerialFile.py
To execute run: python SerialConsole.py/python SerialFile.py


•Host2 establishes TCP Connection
•Host2 continuously reads from the user input, detection of a 1 indicates beginning of data. Host2 reads 16 bits and checks the checksum**. 
•If checksum checks: Host 2 sends an ACK to RaspberryPi represented by ‘1’. Data is written on the console.
 If checksum does not check: Host 2 sends a NAK to RaspberryPi represented by ‘0’.
•After 3 consecutive NAKS, a SYN signal is sent to RaspberryPi represented by ‘2’. 
•Once a request for SYN is sent, Host2 listens for SYN Stream, and sends a SYNACK to RaspberryPi, represented by ‘4’ on receiving a SYN Stream. If a SYN Stream is not  received for 600msecs, a SYNNAK is sent to RaspberryPi, represented by ‘5’ and Host 2 continues to listen for SYN Stream.    

** Checksum = data^key. key = 137, mutually decided between Host1 and Host2. 
