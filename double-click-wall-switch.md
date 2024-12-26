# Node-RED Flow for adding Double-Click function to a switch.

This Node-RED flow was developed to control a CCT or RGB light strip. So I can change the led strip between warm and cool white with the same button I use to turn it On/Off. 

The goal is to make the LED strip toggle between On/Off and switch between warm and cool white based on the number of clicks.

The only problem I faced with this flow is a small delay between a single press and the light turn On/Off, I have tried several values on the trigger that wait to see if another click will come, but I couldn't notice any difference.

## Flow

![image](https://github.com/user-attachments/assets/7088743d-69b9-4245-a46f-f00e0bb5e4ac)

## Code

    [{"id":"2aad2bc8db630d38","type":"group","z":"f26ac47927bcbb37","style":{"stroke":"#999999","stroke-opacity":"1","fill":"none","fill-opacity":"1","label":true,"label-position":"nw","color":"#a4a4a4"},"nodes":["aca020a21aa0de8c","b869f512f1d8fad4","8829f3092aba968f","1df6aa7c509dd9c8","ab5490d2b6e95959","d63d9aa585c93f35","8b5f6f4958fda4dd","f2bf2c06050a8260","5eea4f48a3af654b","6c226603d7f880cc","function_node"],"x":24,"y":1199,"w":982,"h":222},{"id":"aca020a21aa0de8c","type":"api-call-service","z":"f26ac47927bcbb37","g":"2aad2bc8db630d38","name":"Office Led Strip - Toggle","server":"ce62d31.41e203","version":7,"debugenabled":true,"action":"light.toggle","floorId":[],"areaId":[],"deviceId":["d6d86a84a4d45ed0613f009eeee571ca"],"entityId":[],"labelId":[],"data":"","dataType":"json","mergeContext":"","mustacheAltTags":false,"outputProperties":[],"queue":"none","blockInputOverrides":false,"domain":"light","service":"toggle","x":840,"y":1240,"wires":[[]]},{"id":"b869f512f1d8fad4","type":"counter","z":"f26ac47927bcbb37","g":"2aad2bc8db630d38","name":"","init":"0","step":"1","lower":null,"upper":null,"mode":"increment","outputs":"1","x":120,"y":1340,"wires":[["8829f3092aba968f"]]},{"id":"8829f3092aba968f","type":"switch","z":"f26ac47927bcbb37","g":"2aad2bc8db630d38","name":"","property":"count","propertyType":"msg","rules":[{"t":"neq","v":"0","vt":"num"}],"checkall":"true","repair":false,"outputs":1,"x":225,"y":1340,"wires":[["1df6aa7c509dd9c8"]],"l":false},{"id":"1df6aa7c509dd9c8","type":"change","z":"f26ac47927bcbb37","g":"2aad2bc8db630d38","name":"","rules":[{"t":"set","p":"delay","pt":"msg","to":"count","tot":"msg"},{"t":"change","p":"delay","pt":"msg","from":"1","fromt":"num","to":"1000","tot":"num"},{"t":"change","p":"delay","pt":"msg","from":"2","fromt":"num","to":"1","tot":"num"}],"action":"","property":"","from":"","to":"","reg":false,"x":275,"y":1340,"wires":[["d63d9aa585c93f35"]],"l":false},{"id":"ab5490d2b6e95959","type":"change","z":"f26ac47927bcbb37","g":"2aad2bc8db630d38","name":"reset","rules":[{"t":"set","p":"reset","pt":"msg","to":"true","tot":"bool"}],"action":"","property":"","from":"","to":"","reg":false,"x":430,"y":1340,"wires":[["b869f512f1d8fad4"]]},{"id":"d63d9aa585c93f35","type":"trigger","z":"f26ac47927bcbb37","g":"2aad2bc8db630d38","name":"","op1":"","op2":"","op1type":"nul","op2type":"payl","duration":"0.1","extend":true,"overrideDelay":true,"units":"ms","reset":"","bytopic":"all","topic":"topic","outputs":1,"x":420,"y":1260,"wires":[["8b5f6f4958fda4dd","ab5490d2b6e95959"]]},{"id":"8b5f6f4958fda4dd","type":"switch","z":"f26ac47927bcbb37","g":"2aad2bc8db630d38","name":"clicks","property":"count","propertyType":"msg","rules":[{"t":"eq","v":"1","vt":"num"},{"t":"eq","v":"2","vt":"num"}],"checkall":"true","repair":false,"outputs":2,"x":610,"y":1260,"wires":[["aca020a21aa0de8c"],["function_node"]]},{"id":"f2bf2c06050a8260","type":"server-state-changed","z":"f26ac47927bcbb37","g":"2aad2bc8db630d38","name":"Office - Switch 3","server":"ce62d31.41e203","version":6,"outputs":1,"exposeAsEntityConfig":"","entities":{"entity":["switch.interruptor_escritorio_l3"],"substring":[],"regex":[]},"outputInitially":false,"stateType":"str","ifState":"","ifStateType":"str","ifStateOperator":"is","outputOnlyOnStateChange":true,"for":"0","forType":"num","forUnits":"minutes","ignorePrevStateNull":false,"ignorePrevStateUnknown":false,"ignorePrevStateUnavailable":false,"ignoreCurrentStateUnknown":false,"ignoreCurrentStateUnavailable":false,"outputProperties":[{"property":"payload","propertyType":"msg","value":"press","valueType":"str"}],"x":130,"y":1260,"wires":[["b869f512f1d8fad4"]]},{"id":"5eea4f48a3af654b","type":"api-call-service","z":"f26ac47927bcbb37","g":"2aad2bc8db630d38","name":"Office Led Strip - Warm White","server":"ce62d31.41e203","version":7,"debugenabled":false,"action":"light.turn_on","floorId":[],"areaId":[],"deviceId":[],"entityId":["light.led_escritorio"],"labelId":[],"data":"{\"kelvin\":\"2000\",\"brightness_pct\":\"100\"}","dataType":"json","mergeContext":"","mustacheAltTags":false,"outputProperties":[],"queue":"none","blockInputOverrides":false,"domain":"light","service":"turn_on","x":850,"y":1320,"wires":[[]]},{"id":"6c226603d7f880cc","type":"api-call-service","z":"f26ac47927bcbb37","g":"2aad2bc8db630d38","name":"Office Light Strip - Cool White","server":"ce62d31.41e203","version":7,"debugenabled":false,"action":"light.turn_on","floorId":[],"areaId":[],"deviceId":[],"entityId":["light.led_escritorio"],"labelId":[],"data":"{\"kelvin\":\"6500\",\"brightness_pct\":\"100\"}","dataType":"json","mergeContext":"","mustacheAltTags":false,"outputProperties":[],"queue":"none","blockInputOverrides":false,"domain":"light","service":"turn_on","x":850,"y":1380,"wires":[[]]},{"id":"function_node","type":"function","z":"f26ac47927bcbb37","g":"2aad2bc8db630d38","name":"Output Change","func":"if (msg.payload === \"press\") {\n    // Obter ou inicializar o contador\n    flow.count = (flow.count || 0) + 1;\n\n    if (flow.count === 1) {\n        // Enviar para a primeira saída\n        return [msg, null];\n    } else if (flow.count === 2) {\n        // Enviar para a segunda saída e resetar o contador\n        flow.count = 0;\n        return [null, msg];\n    }\n}\n// Se o payload não for \"press\", ignore\nreturn null;","outputs":2,"timeout":"","noerr":0,"initialize":"","finalize":"","libs":[],"x":600,"y":1340,"wires":[["5eea4f48a3af654b"],["6c226603d7f880cc"]]},{"id":"ce62d31.41e203","type":"server","name":"Home Assistant","addon":true,"rejectUnauthorizedCerts":true,"ha_boolean":"","connectionDelay":false,"cacheJson":false,"heartbeat":false,"heartbeatInterval":"10","statusSeparator":"","enableGlobalContextStore":false}]


## Main Components

### 1. **Office Switch**
   - **Node Type**: `server-state-changed`
   - **Description**: Monitors the state of the switch (`switch.office_switch_l3`). When the state changes, it sends a message with the payload `press`.

### 2. **Click Counter**
   - **Node Type**: `counter`
   - **Description**: Increments the counter with each detected click.

### 3. **Click Control**
   - **Node Type**: `switch`
   - **Description**: Checks if the counter is not zero.

### 4. **Delay Adjustment**
   - **Node Type**: `change`
   - **Description**: Adjusts the `delay` value based on the counter. If `delay` is 1, it adjusts to 1000. If `delay` is 2, it adjusts to 1.
(I need to do some tests on this node, I believe its possible to reduce the delay between single click and the action here.)

### 5. **Trigger**
   - **Node Type**: `trigger`
   - **Description**: Sets an interval of 0.1 milliseconds between messages for the next node.
(This trigger will act as an "wait until" function, so the flow can see if you will press once or twice the button and act after this time. I tried with 1 second and 500 miliseconds and no difference was noted.)

### 6. **Output Control**
   - **Node Type**: `switch`
   - **Description**: Directs the message to the correct output based on the number of clicks:
     - 1 click: `Office LED - Toggle`
     - 2 clicks: `Alternate Output`

### 7. **Office LED - Toggle**
   - **Node Type**: `api-call-service`
   - **Description**: Toggles the state of the office LED.

### 8. **Reset**
   - **Node Type**: `change`
   - **Description**: This node will reset the count of clicks.

### 9. **Alternate Output**
   - **Node Type**: `function`
   - **Description**: Alternates between "warm white" and "cool white" with each double click.
   - **Mode**: On Message
   - **Function**:
    `if (msg.payload === "press") {
    // Obter ou inicializar o contador
    flow.count = (flow.count || 0) + 1;
    if (flow.count === 1) {
        // Enviar para a primeira saída
        return [msg, null];
    } else if (flow.count === 2) {
        // Enviar para a segunda saída e resetar o contador
        flow.count = 0;
        return [null, msg];
    }
    }
       // Se o payload não for "press", ignore
    return null;`


### 10. **Office LED - Warm White**
   - **Node Type**: `api-call-service`
   - **Description**: Sets the office LED to `warm white`.

### 11. **Office LED - Cool White**
   - **Node Type**: `api-call-service`
   - **Description**: Sets the office LED to `cool white`.

## How It Works

1. When the office switch (`switch.interruptor_escritorio_l3`) is triggered, the flow starts.
2. The click counter node increments the counter with each detected click.
3. The click control node checks if the counter is not zero.
4. The delay adjustment node sets the delay value based on the counter.
5. The trigger node sets a 0.1 millisecond interval between messages.
6. The output control node directs the message to the correct output based on the number of clicks:
   - 1 click triggers the `Office LED - Toggle` node to toggle the state of the LED.
   - 2 clicks trigger the `Alternate Output` node to alternate between "warm white" and "cool white".

## Requirements

- **Node-RED**: Ensure Node-RED is installed and configured.
- **Home Assistant**: Home Assistant should be set up and integrated with Node-RED.
- **Devices and Entities**: Have the following entities configured in Home Assistant:
  - `switch.interruptor_escritorio_l3`
  - `light.led_escritorio`

## Installation

1. **Set Up Home Assistant**: Make sure the switch and LED are correctly configured in Home Assistant.
2. **Set Up Node-RED**: Install and configure Node-RED in your Home Assistant.
3. **Import the Flow**: Import the provided JSON flow into Node-RED and adjust as needed.

## Contributions

Feel free to contribute improvements or adjustments to this flow! To do so, simply create a **Pull Request**.

