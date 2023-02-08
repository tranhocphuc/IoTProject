# HIS_Project
High integrity Sistems Project. Frankfurt University of Applied Sciences.
Realized by Phuc Tran and Jaime Sanchez Cotta.
The aim of the project is to create an application which shows the actual temperature.
## Architecture: 
 - MQTT-SN on RIOT application. 
 - MQTT on AwS IoT Core. 
 - Temperature sensor data are collected on the RIOT application side. 
 - Mosquitto package is used on the server to translate MQTT-SN to MQTT (Keep in mind that we also have to set up MQTT-Broker as well). 
 - Border router (Code example can be found on FIT IoT-Lab Documentation) will be set up on A8-M3 node. 

## Used in the project:
- Temperature sensor provided by AWS IoT Core (? --> @Phuc: Is this true?) 
- Two A8-M3 cores provided by FIT IoT-LAB.
## How to connect to Fake Broker (Setup by Prof, ssh to grenoble.iot-lab.info): 
### Ex1:
-- Receiver: 
mosquitto_sub -u iotproject1 -P JointheRIOT  -h iotproject.daham.de -t chat /iotproject1/message/iotproject2

-- Sender: 
mosquitto_pub -h iotproject.dahahm.de -t test -m  "Hallo Welt" 

mosquitto_pub -u iotproject2 - P JointheRIOT -h iotproject.dahahm.de -t chat /iotproject1/message/iotproject2 -m hallo 

#### --> Publisher(iotproject2) sends, Subscriber receives(iotproject1)

### Ex2: 
-- Receiver: 
mosquitto_sub -u iotproject1 -P JointheRIOT  -h iotproject.daham.de -t chat /iotproject1/message/iotproject3

-- Receives all: 
mosquitto_sub -u iotproject1 -P JointheRIOT  -h iotproject.daham.de -t chat /iotproject1/message/+

-- Sender:
mosquitto_pub -u iotproject3 - P JointheRIOT -h iotproject.dahahm.de -t chat /iotproject1/message/iotproject3 -m hallo 

## Information 

MQTT-Broker is created on AwS IoT Core 

On the IoT-Lab Server, setup a translater (likely Mosquitto package)

AwS only support encrypted MQTT TLS.