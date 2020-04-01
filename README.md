# Making TTS Better - NodeRed version

Watch the full video here: https://youtu.be/Ib8RffCYcfo

Below in the code I used in the 'Function' Nodes.

* Example 1 - speak_bedroom_temperature:
```yaml
msg.payload =

"The temperature is "+
"{{states.sensor.bedroom_temperature.state}}"+ ", " +

"The thermostat is "+
"{{states.input_boolean.heating_auto.state}}"+ ", " +

"and that is set to "+
"{{states.climate.bedroom_cooling.attributes.temperature}}"

return msg
```
* Example 2 - Random made TTS:
```yaml
var line1 = ["Awesome, ", "Oh wow, ", "Excellent, ", "Super, "]
var line2 = [
        "This bloke ", "3a tiv ", "Your mate ", "That guy ", "3a tiv "
        ]
var line3 = [
        "has made ",
        "has only gone and made ",
        "has got ",
        "has uploaded ",
        "Shared "
        ]
var line4 = [
        "an excellent video, ", "a super tutorial, ", "another great tutorial, ", "a great video, "
        ]
var line5 = [
        "tell everyone.", "dont forget to hit the like button.", "Subscribe.", "did you like it?"
        ]

msg.payload =

line1[Math.floor(Math.random() * line1.length)]+
line2[Math.floor(Math.random() * line2.length)]+
line3[Math.floor(Math.random() * line3.length)]+
line4[Math.floor(Math.random() * line4.length)]+
line5[Math.floor(Math.random() * line5.length)]

return msg
```
* Example 3 - Random made TTS and Sensor Data:

```yaml
var beg = ["The temperature is ", "Its currently ", "Looks like its ", "I see its "]
var mid = ["The thermostat is ", "thermostat ", "thermostat status "]
var end = ["and is set to ", "and set at ", "and its set to ", "and that is set to "]

msg.payload =

beg[Math.floor(Math.random() * beg.length)]+
"{{states.sensor.bedroom_temperature.state}}"+ ", "+

mid[Math.floor(Math.random() * mid.length)]+
"{{states.input_boolean.heating_auto.state}}"+ ", "+

end[Math.floor(Math.random() * end.length)]+
"{{states.climate.bedroom_cooling.attributes.temperature}}"

return msg
```
* Set Thermo Node:
```yaml
if (msg.payload === "on") {

msg.payload =
global.get('homeassistant').homeAssistant.states["sensor.bedroom_temperature"].state;  
}

return msg
```


<a href="https://www.buymeacoffee.com/3ative" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-blue.png" alt="Buy Me A Coffee" style="height: 51px !important;width: 217px !important;" ></a>

