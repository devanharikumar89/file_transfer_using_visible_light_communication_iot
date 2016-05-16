Data Transfer via Visible Light Communication

This is our implementation of Data Transfer via Visible Light Communication, which is implemented using Python 2.7.

Here are some of the salient features of the project:
	•Support for Real-time transfer of data from Host1 to Host2 using the RaspberryPi and the Arduino. 
	•Support for generic file transfer from Host1 to Host2 using RaspberryPi and the Arduino. 
	•Provision of reliability using ACKs, NAKs and SYNC messages.  
	•In-order delivery of data
	•Guaranteed data delivery 

Requirements:
	•Python 2.7 
	•Raspberry Pi
	•Arduino
	•Eclipse IDE(Optional) 
	•Arduino IDE
	•Hardware Components: LED, Photodiode, Resistors

Operating Systems Tested on:
	•Linux
	•Raspbian 

Instructions to Run: 
1.For Real-Time Data Transfer: 
	•Make sure the server process (Pi.py) is running on the Raspbian. 
	•Execute the Host 1 process(Reader.py) and enter the port number for Host 1
	•Execute the Host 2 process(SerialConsole.py) for real-time transfer and enter the port number for Host 2
	•Type/Paste data onto console in Host 1.
2.For File-Transfer: 
	•Make sure the file to be transferred is present in the same directory as the code on Host 1. 
	•Make sure the server process is running on the Raspbian. 
	•Execute the Host 1 process(Reader.py) and enter the port number for Host 1
	•Execute the Host 2 process(SerialFile.py) for file transfer, enter the file name for the required file to be transferred and the port number for Host 2. 
