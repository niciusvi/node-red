# Node-Red
This repository aims to share some creations and solutions I currently use in my home automations using Home Assistant with Node-Red Add-on.

Many homes rely on simple automations and scenes, often controlled by apps like Tuya, Sonoff, or Smart Life. However, with Home Assistant and Node-RED integration, the customization possibilities are almost endless.

**A truly automated home doesn't depend on you asking Alexa to execute a function but instead performs actions automatically based on your needs.**

Below, I’ll share some details about the key devices I use.

# Hardware

Currently, I use Home Assistant as a VM on Proxmox, which runs on a "Mini PC T8 Plus".

![Sem título](https://github.com/user-attachments/assets/96fc1724-933e-474d-9011-ad0faafee52e)

**Specifications:**

- Intel Celeron N5095 | 8GB DDR4 | 240GB SSD | Dual Gigabit LAN

An excellent option for those who need a router/firewall with very low power consumption.

Note: Storage is upgradable.

Updated versions with Intel N100 are also available.

**Sonoff ZBDongle Plus:**

![Sem título](https://github.com/user-attachments/assets/53117bd2-f1ab-4555-a893-aa9f489b4e87)

Used for Zigbee communication.

# Software

**Virtual Machines (VMs)s:**

- Sophos Firewall - 4 Cores - 4GB RAM

- Home Assistant - 4 Cores - 4GB RAM

**Containers:**

- Pi-Hole - 256MB RAM

- Cloudflared LXC - 256MB Ram

**Home Assistant Add-ons:**

  Node-RED

- ESPHome Device Compiler

- Zigbee2MQTT

- Studio Code Server

# Dispositivos

**Interruptores:**
- Zemismart 1-4 Gang Zigbee Switch (Living Room, Balcony, Office, Kitchen)

![Sem título](https://github.com/user-attachments/assets/2f5e1c0e-3510-4572-be07-bdc626eeca93)

- Moes 1 Gang Zigbee Switch (Doorbell)

![Sem título](https://github.com/user-attachments/assets/93687e17-5e9f-409f-b3f2-4aa54ed74ae3)

- Zemismart 2 Gang + Socket Zigbee Switch (Bathroom)

![Sem título-1](https://github.com/user-attachments/assets/a616ed4d-71ab-4128-8063-b826f3ce7750)

- Mini Interruptor WHD02 (Kitchen, Laundry, Bedroom)

![Sem título](https://github.com/user-attachments/assets/bc4c257c-8a08-4208-8583-3fb3eba3c32d)

**Controlador LED:**
- Gledopto GL-C-008P RGB Led Controller (Office and Living Room)

![Sem título](https://github.com/user-attachments/assets/fb69c94a-58e5-4505-abb6-885882f416e4)

- Tuya TS0502B CCT Led Controller (Kitchen)

![Sem título](https://github.com/user-attachments/assets/274d9335-48fe-4ce4-970c-9fabcff0d48f)

**Sensors:**
- Aqara RTCGQ11LM Moviment Sensor (All rooms)

![Sem título](https://github.com/user-attachments/assets/d43fbce1-11da-4b95-8c5a-99ebe626ec84)

- Tuya Zy-M100-L Presence Sensor (Kitchen)

![Sem título](https://github.com/user-attachments/assets/53bbb7dc-cf26-403a-8be1-0d89bbe5c08f)

- Sensor de porta NovaDigital Wifi (Entrance)

![Sem título](https://github.com/user-attachments/assets/3bcfa1e4-ef86-4ffa-a7b7-d73baeb06dac)

**Others:**
- Zemismart TS0044 Push Button (Bedroom and Living Room)

![Sem título](https://github.com/user-attachments/assets/179182e5-51d8-42db-8263-a5fa6bebfed9)






