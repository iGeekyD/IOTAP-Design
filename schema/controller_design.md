#Details of controller implementation

##Main high-level goals

1. Get information from sensors
2. Pass data to MQTT broker

## First version implementation 

1. Create a mock which will present an edge layer (sensors) abstraction. 
This function should pass raw data like temperature inside another handler function.
2. End-point for sensor. It should simply read data from stream and convert it to 
MQTT format. 
3. MQTT sender. Sends an MQTT message to the MQTT Broker.

##TODO
This is just a start-from-scratch design. It will be changed significantly in the future.

