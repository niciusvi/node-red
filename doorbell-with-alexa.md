# Node-RED Flow for Doorbell Notification via Alexa

This flow was developed in Node-RED, allowing Alexa to notify when someone rings the doorbell, and send a new message if no one open the door after a designated time.

## Flow

![image](https://github.com/user-attachments/assets/0f9524ab-c10c-4d5b-b817-ca0821d94da4)

## Code

     [{"id":"aa039913b4a52166","type":"group","z":"19bcf5f111b3132d","style":{"stroke":"#999999","stroke-opacity":"1","fill":"none","fill-opacity":"1","label":true,"label-position":"nw","color":"#a4a4a4"},"nodes":["32b496a054d7c541","9d168bbc71f6ef18","3e2d1f15e0353705","37bb3a98bdcc261c","540b0c62ab12dca7","864e1235a116ac04","3adfe608b76e5fb8","8b801f279bad1b16","c0db0d6e5a6ab94a","1eaead34517f6c56","d9d31ccfea9c4cac"],"x":54,"y":2359,"w":812,"h":342},{"id":"32b496a054d7c541","type":"server-state-changed","z":"19bcf5f111b3132d","g":"aa039913b4a52166","name":"Switch Doorbell - ON","server":"ce62d31.41e203","version":6,"outputs":2,"exposeAsEntityConfig":"","entities":{"entity":["switch.campainha"],"substring":[],"regex":[]},"outputInitially":false,"stateType":"str","ifState":"off","ifStateType":"str","ifStateOperator":"is","outputOnlyOnStateChange":false,"for":"0","forType":"num","forUnits":"minutes","ignorePrevStateNull":false,"ignorePrevStateUnknown":false,"ignorePrevStateUnavailable":false,"ignoreCurrentStateUnknown":false,"ignoreCurrentStateUnavailable":false,"outputProperties":[{"property":"payload","propertyType":"msg","value":"","valueType":"entityState"}],"x":170,"y":2440,"wires":[["9d168bbc71f6ef18","8b801f279bad1b16","37bb3a98bdcc261c"],[]]},{"id":"9d168bbc71f6ef18","type":"delay","z":"19bcf5f111b3132d","g":"aa039913b4a52166","name":"","pauseType":"delay","timeout":"2","timeoutUnits":"milliseconds","rate":"1","nbRateUnits":"1","rateUnits":"second","randomFirst":"1","randomLast":"5","randomUnits":"seconds","drop":false,"allowrate":false,"outputs":1,"x":450,"y":2460,"wires":[["3e2d1f15e0353705"]]},{"id":"3e2d1f15e0353705","type":"api-call-service","z":"19bcf5f111b3132d","g":"aa039913b4a52166","name":"Switch Campainha - OFF","server":"ce62d31.41e203","version":7,"debugenabled":true,"action":"switch.turn_on","floorId":[],"areaId":[],"deviceId":[],"entityId":["switch.campainha"],"labelId":[],"data":"","dataType":"json","mergeContext":"","mustacheAltTags":false,"outputProperties":[],"queue":"none","blockInputOverrides":false,"domain":"switch","service":"turn_on","x":730,"y":2460,"wires":[[]]},{"id":"37bb3a98bdcc261c","type":"alexa-remote-routine","z":"19bcf5f111b3132d","g":"aa039913b4a52166","name":"TTS - Alexa","account":"0b0dcfaefb34f2b7","routineNode":{"type":"speak","payload":{"type":"announcement","text":{"type":"str","value":"A Campainha tocou"},"devices":["G090XG12210201R1","G090XG1221760K8K","G090XG1221760K70"]}},"x":450,"y":2400,"wires":[[]]},{"id":"540b0c62ab12dca7","type":"api-current-state","z":"19bcf5f111b3132d","g":"aa039913b4a52166","name":"Door is closed?","server":"ce62d31.41e203","version":3,"outputs":2,"halt_if":"off","halt_if_type":"str","halt_if_compare":"is","entity_id":"binary_sensor.porta_de_entrada_door","state_type":"str","blockInputOverrides":false,"outputProperties":[{"property":"payload","propertyType":"msg","value":"","valueType":"entityState"}],"for":"0","forType":"num","forUnits":"seconds","override_topic":false,"state_location":"payload","override_payload":"msg","entity_location":"data","override_data":"msg","x":380,"y":2540,"wires":[["c0db0d6e5a6ab94a"],[]]},{"id":"864e1235a116ac04","type":"delay","z":"19bcf5f111b3132d","g":"aa039913b4a52166","name":"Rate Limit","pauseType":"rate","timeout":"5","timeoutUnits":"seconds","rate":"1","nbRateUnits":"1","rateUnits":"minute","randomFirst":"1","randomLast":"5","randomUnits":"seconds","drop":true,"allowrate":false,"outputs":1,"x":600,"y":2600,"wires":[["3adfe608b76e5fb8"]]},{"id":"3adfe608b76e5fb8","type":"switch","z":"19bcf5f111b3132d","g":"aa039913b4a52166","name":"","property":"payload","propertyType":"msg","rules":[{"t":"eq","v":"off","vt":"str"}],"checkall":"true","repair":false,"outputs":1,"x":750,"y":2600,"wires":[["d9d31ccfea9c4cac"]]},{"id":"8b801f279bad1b16","type":"change","z":"19bcf5f111b3132d","g":"aa039913b4a52166","name":"Converter Payload","rules":[{"t":"change","p":"payload","pt":"msg","from":"off","fromt":"str","to":"on","tot":"str"}],"action":"","property":"","from":"","to":"","reg":false,"x":190,"y":2540,"wires":[["540b0c62ab12dca7"]]},{"id":"c0db0d6e5a6ab94a","type":"delay","z":"19bcf5f111b3132d","g":"aa039913b4a52166","name":"","pauseType":"delay","timeout":"40","timeoutUnits":"seconds","rate":"1","nbRateUnits":"1","rateUnits":"second","randomFirst":"1","randomLast":"5","randomUnits":"seconds","drop":false,"allowrate":false,"outputs":1,"x":630,"y":2520,"wires":[["864e1235a116ac04"]]},{"id":"1eaead34517f6c56","type":"server-state-changed","z":"19bcf5f111b3132d","g":"aa039913b4a52166","name":"Door is open?","server":"ce62d31.41e203","version":6,"outputs":2,"exposeAsEntityConfig":"","entities":{"entity":["binary_sensor.porta_de_entrada_door"],"substring":[],"regex":[]},"outputInitially":false,"stateType":"str","ifState":"on","ifStateType":"str","ifStateOperator":"is","outputOnlyOnStateChange":true,"for":"0","forType":"num","forUnits":"minutes","ignorePrevStateNull":false,"ignorePrevStateUnknown":false,"ignorePrevStateUnavailable":false,"ignoreCurrentStateUnknown":false,"ignoreCurrentStateUnavailable":false,"outputProperties":[{"property":"payload","propertyType":"msg","value":"","valueType":"entityState"},{"property":"data","propertyType":"msg","value":"","valueType":"eventData"},{"property":"topic","propertyType":"msg","value":"","valueType":"triggerId"}],"x":370,"y":2600,"wires":[["864e1235a116ac04"],[]]},{"id":"d9d31ccfea9c4cac","type":"alexa-remote-routine","z":"19bcf5f111b3132d","g":"aa039913b4a52166","name":"TTS - Alexa","account":"0b0dcfaefb34f2b7","routineNode":{"type":"speak","payload":{"type":"announcement","text":{"type":"str","value":"Atenção, tem alguém te ámolando lá fora"},"devices":["G090XG12210201R1","G090XG1221760K8K","G090XG1221760K70"]}},"x":470,"y":2660,"wires":[[]]},{"id":"ce62d31.41e203","type":"server","name":"Home Assistant","addon":true,"rejectUnauthorizedCerts":true,"ha_boolean":"","connectionDelay":false,"cacheJson":false,"heartbeat":false,"heartbeatInterval":"10","statusSeparator":"","enableGlobalContextStore":false},{"id":"0b0dcfaefb34f2b7","type":"alexa-remote-account","name":"Vinicius","authMethod":"proxy","proxyOwnIp":"192.168.10.8","proxyPort":"3456","cookieFile":"/config/senha","refreshInterval":"1","alexaServiceHost":"pitangui.amazon.com","amazonPage":"amazon.com.br","acceptLanguage":"pt-BR","onKeywordInLanguage":"on","userAgent":"","useWsMqtt":"on","autoInit":"on"}]


## Main Components

### 1. **Doorbell Switch**
   - **Description**: Detects when the doorbell switch is triggered in Home Assistant.
   - **Node Type**: `server-state-changed`
   - **Action**: When the state of the switch (`switch.doorbell`) changes to `off`, the flow is triggered.
     (Here, I used the inverse off/on function, this way the LED on the switch stays on, making it easier for people to see.)

### 2. **Delay**
   - **Description**: Introduces a small delay and then returns the switch to its previous state.
   - **Node Type**: `delay`
   - **Time**: 2 milliseconds of delay.

### 3. **API Call Service**
   - **Description**: Turns the doorbell switch back on.
   - **Node Type**: `api-call-service`
   - **Action**: Calls the `switch.turn_on` service to reset the switch state.

### 4. **Alexa Routine - Doorbell Ring**
   - **Description**: Triggers an Alexa routine to announce the doorbell ring.
   - **Node Type**: `alexa-remote-routine`
   - **Message**: "The doorbell rang"
   - **Devices**: Echo Dots.
     
### 5. **Converter Payload**
   - **Description**: This node is only needed if you want to change the default state of the switch to `off` to keep the led on.
   - **Node Type**: `change`
   - **Action**: If the msg.payload is (`off`), change it to (`on`).
     (I will do some test to see if this node is really necessary)
     
### 6. **Door State Check**
   - **Description**: If someone open the door it will send a message so the rate limiter can't pass new ones.
   - **Node Type**: `api-current-state`
   - **Entity**: `binary_sensor.front_door`
   - **Action**: If the door is open (`on`), the flow will stop at the rate limiter
     
### 7. **Door State Check**
   - **Description**: Checks if the door is closed before proceeding.
   - **Node Type**: `api-current-state`
   - **Entity**: `binary_sensor.front_door`
   - **Action**: If the door is closed (`off`), the flow continues

### 8. **Delay**
   - **Description**: Introduces a delay to see if someone opens the door, if not flow continues.
   - **Node Type**: `delay`
   - **Time**: 40 seconds of delay.

### 9. **Payload Rate Limiter**
   - **Description**: Prevents sending messages at too fast a rate.
   - **Node Type**: `rate-limit`
   - **Rate**: 1 msg per 1 minute.

### 10. **Switch**
   - **Description**: Checks if the door is closed before proceeding.
   - **Node Type**: `msg.payload`
   - **Action**: If the msg.payload is (`off`), the flow continues.

### 11. **Alexa Routine - Alert Someone at the Door**
   - **Description**: Triggers a second Alexa routine to alert that someone is at the door.
   - **Node Type**: `alexa-remote-routine`
   - **Message**: "Attention, someone is bothering you outside"
   - **Devices**: Echo dots.

## How It Works

- When the doorbell (switch) is triggered, the flow starts.
- The first Alexa Notification will run.
- Node-RED checks the state of the door to ensure it's closed before sending the next notification.
- Alexa sent another notification if the door wasn't open after `x` seconds, alerting that someone is outside.
- Delays and checks are used to ensure that notifications are not sent repeatedly, too quickly or if the door was open in time .

## Requirements

- **Home Assistant** with the doorbell switch device.
- **Node-RED** running in the Home Assistant environment.
- **Alexa** configured with Node-RED through the `alexa-remote` add-on.
- **Alexa Devices** set up to receive routine notifications.

## Installation

1. **Set Up Home Assistant**: Make sure the doorbell switch is correctly configured in Home Assistant.
2. **Set Up Node-RED**: Install Node-RED in your Home Assistant and configure the integration with Alexa using the `alexa-remote` add-on.
3. **Import the Flow**: Import this flow into Node-RED and adjust as needed.
4. **Test**: When the doorbell is rung, Alexa should announce the configured message.

## Contributions

Feel free to contribute improvements or adjustments to this flow! To do so, simply create a **Pull Request**.


