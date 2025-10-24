# Elfin-EW11A-VSR-300-HOME-ASSISTANT
Connection based on Modbus. RS485 &lt;-> WIFI. System Air VSR 300 + Elfin EW11A

EW11A settings:

l: admin
p: admin

<img width="1437" height="1250" alt="Image" src="https://github.com/user-attachments/assets/eefdc16a-b074-4433-af4e-7a129d16521d" />

<img width="1442" height="810" alt="Image" src="https://github.com/user-attachments/assets/bfc11831-4a02-4f03-a093-0ce4e6f4878a" />

<img width="1468" height="775" alt="Image" src="https://github.com/user-attachments/assets/da744d9c-492a-49dc-b12c-779c2189062c" />

VSR 300 settings

p: 1111

![Image](https://github.com/user-attachments/assets/a0c8f888-c084-4935-ae1b-a8f3c7185b58)
![Image](https://github.com/user-attachments/assets/288bead6-c5d6-463d-bdc2-954e5a3ec196)
![Image](https://github.com/user-attachments/assets/8447cf90-b828-48db-9fc3-f8135ecc7f18)

yaml:

#### type: rtuovertco doesn't work for me, port: 8432 and 502 also doesn't work.
modbus:
  - name: vsr
    type: tcp
    host: 192.168.18.98
    port: 8899
    rtu_over_tcp: true

    climates:
      - name: vent_VSR300
        unique_id: vent_VSR300
        address: 12102
        slave: 1
        scale: 0.1
        offset: 0
        precision: 1
        max_temp: 30
        min_temp: 15
        temp_step: 1
        target_temp_register: 2000

    sensors:
      - name: vsr300_outdoor_temperature
        unique_id: vsr300_outdoor_temperature
        #hub: VSR300
        device_class: temperature
        slave: 1
        address: 12101
        input_type: holding
        unit_of_measurement: °C
        scale: 0.1
        offset: 0
        precision: 1
        data_type: int16

      - name: vsr300_exhaust_temperature
        unique_id: vsr300_exhaust_temperature
        #hub: VSR300
        device_class: temperature
        slave: 1
        address: 12543 
        input_type: holding
        unit_of_measurement: °C
        scale: 0.1
        offset: 0
        precision: 1
        data_type: uint16

I based it on: https://github.com/cmragnar/HomeAssistant-VSR300-Modbus/tree/main
