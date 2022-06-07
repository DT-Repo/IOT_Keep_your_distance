# IOT_Keep_your_distance
This is the Project of 054323 - INTERNET OF THINGS course of POLITECNICO DI MILANO assigned in 2019/2020.
|<img src="https://github.com/DT-Repo/IOT_Keep_your_distance/blob/master/Images/tinyos.jpg" width="250" height="100"> | <img src="https://github.com/DT-Repo/IOT_Keep_your_distance/blob/master/Images/node-red-logo.png" width="150" height="150"> | <img src="https://github.com/DT-Repo/IOT_Keep_your_distance/blob/master/Images/ifttt-logo.png" width="250" height="100"> 
|---|---|---|
## Cooja
In the solution, all the motes are configured to send a **broadcast** message sharing its ID every $T_{timer} = 500 ms$. 
The motes are also configured to use the serial port, then everytime a mote receives a message will print it in the serial port together with its ID.

![alt text](https://github.com/DT-Repo/IOT_Keep_your_distance/blob/master/Images/cooja.PNG)
As can be noticed in the figure, everytime a pair of motes are inside their range, configured in cooja, they will receive 
the broadcast message and will print it in the serial port. <br>
To integrate the cooja simulation with node-red, we assign to each mote a port in the localhost.


## NodeRed
To build the requests needed to use the IFTTT service by the **POST** method, we just read the port 
of each mote and build the proper JSON containing the ID of the mote which is sending the message and the ID of the mote which is near it.
<img src="https://github.com/DT-Repo/IOT_Keep_your_distance/blob/master/Images/node-red.png" width="600" height="250">

## IFTTT
<img src="https://github.com/DT-Repo/IOT_Keep_your_distance/blob/master/Images/ifttt.png" width="230" height="250">
The IFTTT request needs the name of the project connected to this service and the payload, which it's just 
a string with the content we want to notify to the client's mobile phone. According to the NodeRed-IFTTT tutorial, the applet 
built is triggered when it receives a Web Request from node-red ("IF THIS" part of the service) and it sends a notification containing a 
String to IFTTT app ("THEN THAT" part).

## Testing Configurations
To test the solution, it's chosen to work with 5 motes and trace the alarm that must be notified when two of them are close enough to receive 
the other's message. 

### Motes out of range
<img src="https://github.com/DT-Repo/IOT_Keep_your_distance/blob/master/Images/no_comunication.png" width="600" height="250">

### Two motes in the range
|<img src= "https://github.com/DT-Repo/IOT_Keep_your_distance/blob/master/Images/1-4comunication.png" width="600" height="250">|<img src= "https://github.com/DT-Repo/IOT_Keep_your_distance/blob/master/Images/first.png" width="200" height="450">|
|---|---|

As we can see in figure notifications are correctly sent to the app.

### All motes in range
<img src="https://github.com/DT-Repo/IOT_Keep_your_distance/blob/master/Images/all_in_range.png" width="600" height="250">

<img src= "https://github.com/DT-Repo/IOT_Keep_your_distance/blob/master/Images/uno.png" width="200" height="450"> |<img src= "https://github.com/DT-Repo/IOT_Keep_your_distance/blob/master/Images/due.png" width="200" height="450"> | <img src= "https://github.com/DT-Repo/IOT_Keep_your_distance/blob/master/Images/tre.png" width="200" height="450"> |<img src= "https://github.com/DT-Repo/IOT_Keep_your_distance/blob/master/Images/quattro.png" width="200" height="450"> 
|---|---|---|---|
