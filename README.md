# Node-Red
Fluxos Node-Red utilizados para automações no Home Assistant

O intuito deste repositório é compartilhar algumas criações e soluções que utilizo hoje em minhas automações residenciais em conjunto com o Home Assistant.

Muitas residências contam com automações e cenas simples, geralmente controladas pelo aplicativo Tuya, Sonoff ou Smart Life, porém com o Home Assistant e a integração do Node-RED as possibilidades de customizações são quase infinitas.

**Uma casa verdadeiramente automatizada não depende de você pedir para alexa executar uma função, mas sim as fazem automaticamente de acordo com suas necessidades.**


Abaixo vou deixar algumas informações dos principais equipamentos que utilizo.

# Hardware

Atualmente utilizo o home assistant como uma VM do Proxmox, este por sua vez roda em um "Mini PC T8 Plus"
![Sem título](https://github.com/user-attachments/assets/96fc1724-933e-474d-9011-ad0faafee52e)

Configurações: 
Intel Celeron N5095 | 8GB DDR4 | 240GB SSD | Dual Gigabit LAN

Excelente opção para quem precisa de um roteador/firewall com baixissimo consumo de energia.

Obs: É possível fazer upgrade apenas no armazenamento.

Atualmente é possível encontrar versões atualizadas com o Intel N100.

Sonoff ZBDongle Plus:
![Sem título](https://github.com/user-attachments/assets/53117bd2-f1ab-4555-a893-aa9f489b4e87)


# Software

VMs: 
Sophos Firewall - 4 Cores - 4GB RAM
Home Assistant - 4 Cores - 4GB RAM

Containers:
Pi-Hole - 256MB RAM
Cloudflared LXC - 256MB Ram

Home Assistant Add-ons:
Node-RED
ESPHome Device Compiler
Zigbee2MQTT
Studio Code Server

# Dispositivos

**Interruptores:**
Zemismart 1-4 Gang Zigbee Switch (Sala, varanda, escritório)
![Sem título](https://github.com/user-attachments/assets/2f5e1c0e-3510-4572-be07-bdc626eeca93

Moes 1 Gang Zigbee Switch (Campainha)
![Sem título](https://github.com/user-attachments/assets/93687e17-5e9f-409f-b3f2-4aa54ed74ae3)

Zemismart 2 Gang + Socket Zigbee Switch (Banheiro)
![Sem título-1](https://github.com/user-attachments/assets/a616ed4d-71ab-4128-8063-b826f3ce7750)

Mini Interruptor WHD02 (Cozinha, Lavanderia, Quarto)
![Sem título](https://github.com/user-attachments/assets/bc4c257c-8a08-4208-8583-3fb3eba3c32d)

**Controlador LED:**
Gledopto GL-C-008P Led Controller (Escritório e Sala)
![Sem título](https://github.com/user-attachments/assets/fb69c94a-58e5-4505-abb6-885882f416e4)

**Sensores:**
Aqara RTCGQ11LM Moviment Sensor (Todos os comodos)
![Sem título](https://github.com/user-attachments/assets/d43fbce1-11da-4b95-8c5a-99ebe626ec84)

Tuya Zy-M100-L Presence Sensor (Cozinha)
![Sem título](https://github.com/user-attachments/assets/53bbb7dc-cf26-403a-8be1-0d89bbe5c08f)

Sensor de porta NovaDigital Wifi:
![Sem título](https://github.com/user-attachments/assets/3bcfa1e4-ef86-4ffa-a7b7-d73baeb06dac)

**Outros:**
Zemismart TS0044 Botoeira (Quarto e Sala)
![Sem título](https://github.com/user-attachments/assets/179182e5-51d8-42db-8263-a5fa6bebfed9)






