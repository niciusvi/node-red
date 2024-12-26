# Node-RED Flow for Heater Control

## Information about the Node-RED Flow

This Node-RED flow was developed to manage a heater's power status and provide notifications via Alexa when the heater is on for a certain period.

## Flow

![image](https://github.com/user-attachments/assets/05e8cb78-5100-419e-8d5d-195985086e56)


## Code

    [{"id":"a7cc06243754b3b6","type":"group","z":"0788ddb2e2fd1ae7","style":{"stroke":"#999999","stroke-opacity":"1","fill":"none","fill-opacity":"1","label":true,"label-position":"nw","color":"#a4a4a4"},"nodes":["8f2b3f1343582db0","85949bc3aca8f02a","4d72904b101ac2a4","1809211dd74e1cfc","5c62b347cae9f3cb","b8a8b88eb4658f9e","0404dec927128967","0a8b481ccaa3ea5c","8d95a7f1fbb21cc5","46929cf78470550e","35abf5d58b61b055"],"x":34,"y":1499,"w":1252,"h":342},{"id":"8f2b3f1343582db0","type":"server-state-changed","z":"0788ddb2e2fd1ae7","g":"a7cc06243754b3b6","name":"Aquecedor Power","server":"ce62d31.41e203","version":6,"outputs":1,"exposeAsEntityConfig":"","entities":{"entity":["sensor.aquecedor_power"],"substring":[],"regex":[]},"outputInitially":false,"stateType":"str","ifState":"","ifStateType":"str","ifStateOperator":"is","outputOnlyOnStateChange":true,"for":"30","forType":"num","forUnits":"seconds","ignorePrevStateNull":false,"ignorePrevStateUnknown":false,"ignorePrevStateUnavailable":false,"ignoreCurrentStateUnknown":false,"ignoreCurrentStateUnavailable":false,"outputProperties":[{"property":"payload","propertyType":"msg","value":"","valueType":"entityState"},{"property":"data","propertyType":"msg","value":"","valueType":"eventData"},{"property":"topic","propertyType":"msg","value":"","valueType":"triggerId"}],"x":150,"y":1580,"wires":[["4d72904b101ac2a4"]]},{"id":"85949bc3aca8f02a","type":"change","z":"0788ddb2e2fd1ae7","g":"a7cc06243754b3b6","name":"Command - Start","rules":[{"t":"set","p":"command","pt":"msg","to":"start","tot":"str"}],"action":"","property":"","from":"","to":"","reg":false,"x":530,"y":1580,"wires":[["8d95a7f1fbb21cc5"]]},{"id":"4d72904b101ac2a4","type":"switch","z":"0788ddb2e2fd1ae7","g":"a7cc06243754b3b6","name":"","property":"payload","propertyType":"msg","rules":[{"t":"gte","v":"10","vt":"str"},{"t":"eq","v":"0.0","vt":"str"}],"checkall":"true","repair":false,"outputs":2,"x":290,"y":1660,"wires":[["85949bc3aca8f02a","0a8b481ccaa3ea5c"],["1809211dd74e1cfc","b8a8b88eb4658f9e"]]},{"id":"1809211dd74e1cfc","type":"change","z":"0788ddb2e2fd1ae7","g":"a7cc06243754b3b6","name":"Command - Stop","rules":[{"t":"set","p":"command","pt":"msg","to":"stop","tot":"str"}],"action":"","property":"","from":"","to":"","reg":false,"x":530,"y":1700,"wires":[["5c62b347cae9f3cb"]]},{"id":"5c62b347cae9f3cb","type":"hourglass","z":"0788ddb2e2fd1ae7","g":"a7cc06243754b3b6","name":"","persistId":"","humanizeLocale":"pt-br","x":810,"y":1660,"wires":[["46929cf78470550e"]]},{"id":"b8a8b88eb4658f9e","type":"change","z":"0788ddb2e2fd1ae7","g":"a7cc06243754b3b6","name":"Command - Status","rules":[{"t":"set","p":"command","pt":"msg","to":"status","tot":"str"}],"action":"","property":"","from":"","to":"","reg":false,"x":530,"y":1760,"wires":[["0404dec927128967"]]},{"id":"0404dec927128967","type":"delay","z":"0788ddb2e2fd1ae7","g":"a7cc06243754b3b6","name":"","pauseType":"delay","timeout":"2","timeoutUnits":"seconds","rate":"1","nbRateUnits":"1","rateUnits":"second","randomFirst":"1","randomLast":"5","randomUnits":"seconds","drop":false,"allowrate":false,"outputs":1,"x":700,"y":1800,"wires":[["5c62b347cae9f3cb"]]},{"id":"0a8b481ccaa3ea5c","type":"change","z":"0788ddb2e2fd1ae7","g":"a7cc06243754b3b6","name":"Command - Reset","rules":[{"t":"set","p":"command","pt":"msg","to":"reset","tot":"str"}],"action":"","property":"","from":"","to":"","reg":false,"x":530,"y":1640,"wires":[["5c62b347cae9f3cb"]]},{"id":"8d95a7f1fbb21cc5","type":"delay","z":"0788ddb2e2fd1ae7","g":"a7cc06243754b3b6","name":"","pauseType":"delay","timeout":"2","timeoutUnits":"seconds","rate":"1","nbRateUnits":"1","rateUnits":"second","randomFirst":"1","randomLast":"5","randomUnits":"seconds","drop":false,"allowrate":false,"outputs":1,"x":700,"y":1540,"wires":[["5c62b347cae9f3cb"]]},{"id":"46929cf78470550e","type":"function","z":"0788ddb2e2fd1ae7","g":"a7cc06243754b3b6","name":"Converter payload","func":"msg.payload = \"Seu banho durou, \" + msg.elapsed.human;\nreturn msg;\n","outputs":1,"timeout":0,"noerr":0,"initialize":"","finalize":"","libs":[],"x":990,"y":1660,"wires":[["35abf5d58b61b055"]]},{"id":"35abf5d58b61b055","type":"alexa-remote-routine","z":"0788ddb2e2fd1ae7","g":"a7cc06243754b3b6","name":"TTS nas Alexas","account":"0b0dcfaefb34f2b7","routineNode":{"type":"speak","payload":{"type":"announcement","text":{"type":"msg","value":"payload"},"devices":["G090XG12212403GG"]}},"x":1180,"y":1660,"wires":[[]]},{"id":"ce62d31.41e203","type":"server","name":"Home Assistant","addon":true,"rejectUnauthorizedCerts":true,"ha_boolean":"","connectionDelay":false,"cacheJson":false,"heartbeat":false,"heartbeatInterval":"10","statusSeparator":"","enableGlobalContextStore":false},{"id":"0b0dcfaefb34f2b7","type":"alexa-remote-account","name":"Vinicius","authMethod":"proxy","proxyOwnIp":"192.168.10.8","proxyPort":"3456","cookieFile":"/config/senha","refreshInterval":"1","alexaServiceHost":"pitangui.amazon.com","amazonPage":"amazon.com.br","acceptLanguage":"pt-BR","onKeywordInLanguage":"on","userAgent":"","useWsMqtt":"on","autoInit":"on"}]

## Main Components

### 1. **Heater Power**
   - **Node Type**: `server-state-changed`
   - **Description**: Monitors the state of the heater power (`sensor.aquecedor_power`). When the power state changes and remains for 30 seconds, the flow is triggered.

### 2. **Command - Start**
   - **Node Type**: `change`
   - **Description**: Sets the command to "start".

### 3. **Power State Check**
   - **Node Type**: `switch`
   - **Description**: Checks if the power state is greater than or equal to 10 or exactly 0.0.

### 4. **Command - Stop**
   - **Node Type**: `change`
   - **Description**: Sets the command to "stop".

### 5. **Hourglass Timer**
   - **Node Type**: `hourglass`
   - **Description**: Keeps track of the elapsed time since the heater was turned on.

### 6. **Command - Status**
   - **Node Type**: `change`
   - **Description**: Sets the command to "status".

### 7. **Delay**
   - **Node Type**: `delay`
   - **Description**: Introduces a delay before checking the status again.

### 8. **Command - Reset**
   - **Node Type**: `change`
   - **Description**: Sets the command to "reset".

### 9. **Convert Payload**
   - **Node Type**: `function`
   - **Description**: Converts the payload to include a message about the duration the heater has been on.

### 10. **Alexa Notification**
   - **Node Type**: `alexa-remote-routine`
   - **Description**: Sends a TTS (Text-To-Speech) notification via Alexa devices.

## How It Works

1. When the heater power (`sensor.aquecedor_power`) is monitored and the state remains for 30 seconds, the flow is triggered.
2. The command is set to "start".
3. The power state is checked:
   - If the power is greater than or equal to 10, the command is set to "start", and a delay is introduced before resetting the hourglass timer.
   - If the power is exactly 0.0, the command is set to "stop", and the hourglass timer starts tracking the duration.
4. The status of the heater is checked periodically, introducing a delay between checks.
5. The payload is converted to include a message about how long the heater has been on.
6. Alexa sends a TTS notification via connected devices.

## Requirements

- **Node-RED**: Ensure Node-RED is installed and configured.
- **Home Assistant**: Home Assistant should be set up and integrated with Node-RED.
- **Devices and Entities**: Have the following entities configured in Home Assistant:
  - `sensor.aquecedor_power`
- **Alexa Devices**: Alexa devices configured with Node-RED through the `alexa-remote` add-on.
- **Hourglass Node**: The Hourglass node can be obtained here: [Hourglass Node](https://flows.nodered.org/node/node-red-contrib-hourglass/in/a4YHjoqP9_00).

## Installation

1. **Set Up Home Assistant**: Make sure the heater power sensor is correctly configured in Home Assistant.
2. **Set Up Node-RED**: Install and configure Node-RED in your Home Assistant.
3. **Import the Flow**: Import the provided JSON flow into Node-RED and adjust as needed.

## Contributions

Feel free to contribute improvements or adjustments to this flow! To do so, simply create a **Pull Request**.

