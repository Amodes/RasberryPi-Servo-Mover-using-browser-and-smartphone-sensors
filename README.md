<h1> RasberryPi-Servo-Mover-using-browser-and-smartphone-sensors</h1>

<h2>Setup & Installation<h2>

<h3>1. Raspberry Pi Configuration</h3>

- Start Raspberry
- create new folder with the files of the mover-folder
- insert your personal data in settings.json . ```ip``` and ```port``` number of your mqtt broker. You can use a public one like the broker from hivemq (http://www.hivemq.com/demos/websocket-client/ and its port number 1883)  or you can use your own mqtt broker. In ```systemid``` you can insert any string. ```targetip``` is needed if you use the video livestream. Therefore you have to insert the ip adress of the hosting system of your webapplication.
- sudo ./beforeStart.sh
- sudo python start.py
- (for camera support ffmpeg has to be installed on the system (See 4. Video Livestream))

<h3> 2. Webapplication Configuration </h3>

- Extract mqtt folder to your webserver directory
- Open cmd.exe and type ipconfig
- Note IP-Adress

<h3>3.On your smartphone: </h3>

- Open Browser (tested with Google Chrome) in Smartphone
- run index.html: type [Windows-IP-Adress]/mqtt (e.g. 192.168.2.30/mqtt)
- Fill in BrokerIP and Port and Connect

<h3> 4. Video Livestream (optional)</h3>

- Just visible for Desktop Browser
- Install node.js on Windows
- Restart System and open cmd
- npm install npm -g
- npm install jsmpeg
- npm install ws
- cd C:/xampp/htdocs/mqtt/jsmpeg
- node stream-server.js admin    // admin is the password. Has to be the same like in the startVideo class on raspberry
- open index.html in mqtt folder and insert your Windows-IP
  var client = new WebSocket( 'ws://WINDOWS_IP:8084/' ); 
- Desktop Browser: [Windows-IP-Adress]/mqtt
- Press Livestream Button on Smartphone and you can see the stream 
  on your Desktop Browser

<h3>5.Own Broker(opional)(hivemq Test broker)</h3>
- If you don't want a public mqtt broker like broker.mqttdashboard.com you can use your own hivemq broker (limit to 25 clients)
- Download mqtt broker (http://www.hivemq.com/downloads/)
- In the config.xml insert your ip between the the <tcp-listener> and <websocket-listener> tags
- in the bin folder: run run.bat to start the broker
- For the other configuration you can now use your Ip as the mqtt-broker address

