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

* The 'Call Service' Node setup I use:

![Image description](https://github.com/3ative/Making-TTS-Better-NodeRed/blob/master/Alexa-Call-Service-Node-Setup.jpg)

---
### 🤝 Found this useful, want to say 'Thanks' and support my efforts. CHEERS🍺
| Buy me a Coffee | PATREON |
|-----------------|---------|
| [![Buy Me A Coffee](https://img.shields.io/badge/Buy%20Me%20A%20Coffee-donate-yellow.svg?style=flat-square&logo=buy-me-a-coffee)](https://www.buymeacoffee.com/3ative) | [![Patreon](https://img.shields.io/badge/Patreon-support-red.svg?style=flat-square&logo=patreon)](https://www.patreon.com/3ative) |
---
