Pi.py
To execute run: python Pi.py on Raspbian

•RaspberryPi is the server and is always on. It waits for connection from Host1 and Host2. 
•On establishing the connection, RaspberryPi waits on listening for a message (i.e. data byte) from Host1. 
•The received message is formatted using formatPacket() which calculates and appends checksum for the data byte represented in its binary form using getAscii() method. 
•This formatted data is stored as unacked data which can be used if retransmission is required.  
•The sendToLED() function is sued to send data to LED i.e. to control the LED.
•The RaspberryPi then listens for an ACK/NAK/SYN from Host2. Different actions are taken in the event of each message as follows:
	ACK received (stat = 1):
	Read next byte from Host 1, update unacked and send to LED. 
	NAK received (stat = 0):
	Retransmit data in unacked. 
	SYN received (stat = 2):
	Transmit the Synchronization stream (111111111111111100000000) to Arduino till a SYNACK (stat = 4) is received from Host 2. If a SYNNAK (stat = 5) is received 	from Host2, continue sending Synchronization stream. This helps to regain synchronization and prevents any drift in reading of bytes. 

Loss of ACK
A timer is used to wait for an ACK, if the timer times-out, the data in unacked is retransmitted. 


                                                                  ::::Methods used::::

•sendToLED (self,listmesg):: Controls the LED connected to GPIO port 18. LED is ON for 25msecs for a bit  ‘1’  and  it is OFF for 25msecs for a bit ‘0’ 

•formatPacket(self,payload):: Generates checksum and creates and returns packet to be transmitted. 

•getAscii(self,character):: returns binary representation of a character in the form of a string. 

•sync(self):: transmits the synchronization stream and continues to do so every time a SYNNAK is received. It returns only when a SYNACK is received. 

•generateChecksum(payload):: returns checksum for the payload. Checksum = key^payload and key =137, mutually decided between Host1 and Host2.
