[This is the System Setup Part
For SetupIntroduction see point 1]

Setup Instructions:

1.Raspberry_____________________________________________________

- Start Raspberry
- Raspberry Terminal: 
- insert mover folder
- cd /[directory of mover]
- insert your personal data in settings.json
- sudo ./beforeStart.sh
- sudo python start.py
- for camera support ffmpeg has to be installed on the system

2.Windows_______________________________________________________

- Extract mqtt folder to xampp
- Run Webserver (XAMPP Control Panel and start Apache Server)
- Open cmd.exe and type ipconfig
- Note IP-Adress

3.Navigation____________________________________________________

- Open Browser (tested with Google Chrome) in Smartphone
- run index.html: type [Windows-IP-Adress]/mqtt (e.g. 192.168.2.30/mqtt)
- Fill in BrokerIP and Port and Connect

4.Video Livestream______________________________________________
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

5.Own Broker(opional)(hivemq Test broker)__________________________________
- If you don't want a public mqtt broker like broker.mqttdashboard.com you can use
your own hivemq broker (limit to 25 clients)
- Go to mqttBroker -> hivemq-3.0.1 -> conf folder
- In the config.xml insert your ip between the the <tcp-listener> and <websocket-listener> tags
- in the bin folder: run run.bat to start the broker
- For the other configuration you can now use your Ip as the mqtt-broker address

