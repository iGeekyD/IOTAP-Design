#Details of controller implementation

##Main high-level goals

1. Get information from sensors (any type, any device)
2. Pass data to MQTT broker

## First version implementation 

1. Create a mock which will present an edge layer (sensors) abstraction. 
This function should pass raw data like temperature inside another handler function.
2. End-point for sensor. It should simply read data from stream and convert it to 
MQTT format. 
3. MQTT sender. Sends an MQTT message to the MQTT Broker.
### Details of implementation
1. Each controller is thread or process to support non-blocking reading from sensors.
This should be controlled by user by passing special key to the controller. For example::
Running Controller in thread mode. So there will be one process with multiple threads for
each sensor. Process mode will be implemented through several docker containers also
with multiple threads inside:

entrypoint:
    sensors = get_sensors_from_config_file()
    broker = get_broker_from_config_file()
    run_controller(sensors)
globals:
    MQTT broker
class Controller(sensor) inherits Thread:
    function run():
        with newThread():
            getData(sensor)
            sendData(broker)

##Update
1. Make slots mechanism for sensors. Needs to register any number of 
different sensors (in real-time as well) 
2. Mechanism for non blocking interconnection with MQTT Broker


##TODO
This is just a start-from-scratch design. It will be changed significantly in the future.

