Description
-------------

- FIGWAY is an opensource tool to work with FIWARE Orion ContextBroker and/or FIWARE IDAS.4.x.  

- The newest version is all under the "python-IDAS4/" folder. It is written in python and it has been tested in RaspberryPI and MacbookPro
 with OSX 10.9.3. It should work fine in any linux or any other system with Python2.7 installed. 

-  The "c++/" folder holds the previous version written in C++ and working only in RaspberryPI platform. You will find in
 that folder specific instructions while the remaining text within this file refers to the newest one at "python/".

- The "python" folder holds a previous python version to work with IDAS 3.x and lower versions (before April 2015).

- Prior to use this software, you need to configure it at "python-IDAS/config.ini":
 * Note that to obtain the "username" & "token" within "[user]" configuration section, you need to have an account at 
   http://www.fi-ware.org/lab/ and then execute the script "python/get_token.py".
 * In the local [local] configuration section you need to configure the "host_type" (use "RaspberryPI" or "MAC" or "Linux", etc.)
   and the "host_id=" (use the 3 lower bytes in hexa of one of your Ethernet MACs or your e-mail if you do not know how to obtain
   the first).


- Current available folders:
python-IDAS4/ContextBroker/  -> Specific tools to talk to a ContextBroker. Use ContextBroker to read FIWARE IoT Data.
                           There is an specific README.md file in this directory.
                           Meanwhile, execute the commands with no arguments to get help.
python-IDAS4/SensorsUL20/    -> Specific tools to talk to IDAS2.6 to send IoT Data to FIWARE and to simulate virtual sensors (using Ultralight 2.0).
                           There is an specific README.md file in this directory.


How to init
-------------
```bash
git clone https://github.com/itmo-swm/fiware-python-client
cd fiware-python-client/Sensors_UL20
python CreateService.py my_test 4jggokgpepnvsb2uv4s40d59ou
python RegisterDevice.py SENSOR_TEMP Sensor1 TempTest1
python SendObservation.py Sensor1 't|24'
python ../ContextBroker/GetEntityById.py TempTest1
```

How to send new value
-------------
```bash
cd fiware-python-client/Sensors_UL20
python SendObservation.py Sensor1 't|24'
```

How to get current value
-------------
```bash
cd fiware-python-client/Sensors_UL20
python ../ContextBroker/GetEntityById.py TempTest1
```
