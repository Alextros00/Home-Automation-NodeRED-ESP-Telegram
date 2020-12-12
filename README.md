# Home-Automation-NodeRED-ESP-Telegram
<!-- PROJECT SHIELDS -->
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]


<!-- PROJECT LOGO -->
<br />
<p align="center">
  <a href="https://github.com/Alextros00/Home-Automation-NodeRED-ESP-Telegram">
    <img src="images/logo.png" alt="Image of me laying on the floor covered in electronics" width="80" height="80">
  </a>

  <h3 align="center">Home Automation</h3>

  <p align="center">
    A cheap way to automate anything and everything!
    <br />
    <a href="https://github.com/Alextros00/Home-Automation-NodeRED-ESP-Telegram"><strong>Explore the docs »</strong></a>
    <br />
    <a href="https://github.com/Alextros00/Home-Automation-NodeRED-ESP-Telegram">View Demo</a>
    ·
    <a href="https://github.com/Alextros00/Home-Automation-NodeRED-ESP-Telegram/issues">Report Bug</a>
    ·
    <a href="https://github.com/Alextros00/Home-Automation-NodeRED-ESP-Telegram/issues">Request Feature</a>
    <br />
    <a href="https://www.buymeacoffee.com/AlexTrostle" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee" style="height: 41px !important;width: 174px !important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 3px 2px 0px     rgba(190,190, 190, 0.5) !important;" ></a>
  </p>
</p>

<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#mosquitto">Mosquitto</a></li>
        <li><a href="#nodered">NodeRED</a></li>
        <li><a href="#esp32">ESP32</a></li>
        <li><a href="#telegram">Telegram</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgements">Acknowledgements</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## About The Project
This project is about automating all aspects of my home that I can. Why turn on my lights every morning at 7am and turn them off every night at 10:45pm when it can be done for me! I want to spend as little time as possible dealing with repetitive tasks and focusing on the things that matter most to me.

This project consists of many smaller projects. Here is where they are all put together and additional features are added.

### Built With
There were many parts to this project. Some sub-projects that I did in order to build up to this complexity can be found on my [here](https://github.com/Alextros00).

#### Main Components
* [Raspberry Pi 4](https://www.raspberrypi.org/products/raspberry-pi-4-model-b/?resellerType=home&variant=raspberry-pi-4-model-b-8gb). <sup>&dagger;</sup>
  * [MQTT through Mosquitto](https://mosquitto.org/)
  * [NodeRED](https://nodered.org/)
* [ESP32](https://www.espressif.com/en/products/socs/esp32)
* [Telegram](https://telegram.org/)

<sup>&dagger;: I us 8GB but don't really think it is required.</sup>

<!-- GETTING STARTED -->
## Getting Started
These steps will take you through getting your own project up and running.

<!-- Prerequisites -->
### Prerequisites
The software used is free and mostly open source.
* [ESP-IDF]() installed. <sup>&dagger;</sup> <br/>
<sup>&dagger;: You do not need to know how to use it.</sup>

The hardware below you will need to have or to purchase.
* Smartphone
* At least one [ESP32]()
* [Raspberry Pi 4]() <sup>&dagger;</sup> <sup>&Dagger;</sup> <br/>
<sup>&dagger;: Raspberry Pi 4 needs to be running [Raspbian Operating System](linke to how to do).</sup><br/>
<sup>&Dagger;: Needs to be connected to and using a 2.4GHz network. This is because the ESP32's currently(Dec 2020) cannot connect to 5GHz networks.</sup><br/>

<!-- Mosquitto -->
### Mosquitto
The Mosquitto broker will need to be installed on your Raspberry Pi for the MQTT protocol to work.
1. Update your Raspberry Pi<br/>
```sudo apt-get update```
2. Install Mosquitto<br/>
```sudo apt-get install mosquitto```
3. Install Mosquitto Client<br/>
```sudo apt-get install mosquitto-clients```

Be sure to note for later:
* The port of your mosquitto broker. Will automatically be Port 1883
* The server your mosquitto broker is running on. If it is running on your Raspberry Pi then it will be the ip address of your Raspberry Pi.

<!-- NodeRED -->
### NodeRED
[NodeRED](http://nodered.org) will need to be installed on your Raspberry Pi. To do so follow [these steps](https://nodered.org/docs/getting-started/local).

The only flow that is required to start controlling an ESP32 is the ESP32 MQTT flow. Once that is done you may want to [skip to ESP32 setup](#ESP32)

#### Example Flows
* This flow will determine who is on the wifi that the Raspberry Pi is connected to. The flow will start by either by sending a command to the telgram bot or by clicking a button on the NodeRed dashboard. If you only want to use one one of these option you can delete them. You could also add an insert block on an interval to scan the wifi network on a regular basis. Once the flow has run there are one of two outputs. Either a dislay on the NodeRED dashboard or messages from the Telegram Bot.
  ```Javasript
  [{"id":"cd932589.d84fa8","type":"exec","z":"47cca1f5.5a7a5","g":"461804ba.5e11fc","command":"sudo nmap -sP 192.168.1.0/24","addpay":false,"append":"","useSpawn":"false","timer":"","oldrc":false,"name":"","x":430,"y":1300,"wires":[["a8622075.79d05"],[],[]]},{"id":"5f6055aa.77027c","type":"function","z":"47cca1f5.5a7a5","g":"461804ba.5e11fc","name":"Separate Mac Addresses Blocks","func":"for(var i = 0; i<1000; i++){\n    if(msg.payload[i]== 'A'){\n        i++;\n        if(msg.payload[i]== 'd'){\n            i++;\n            if(msg.payload[i]== 'd'){\n                i++;\n                if(msg.payload[i]== 'r'){\n                    i++;\n                    if(msg.payload[i]== 'e'){\n                        i++;\n                        if(msg.payload[i]== 's'){\n                            i++;\n                            if(msg.payload[i]== 's'){\n                                i++;\n                                if(msg.payload[i]== ':'){\n                                    i++;\n                                    if(msg.payload[i]== ' '){\n                                        return msg;\n                                    }\n                                }\n                            }\n                        }\n                    }\n                }\n            }\n        }                \n    }\n}","outputs":1,"noerr":0,"initialize":"","finalize":"","x":430,"y":1360,"wires":[["1cd3bfd8.868f8"]]},{"id":"a8622075.79d05","type":"split","z":"47cca1f5.5a7a5","g":"461804ba.5e11fc","name":"","splt":"\\n","spltType":"str","arraySplt":1,"arraySpltType":"len","stream":false,"addname":"","x":650,"y":1300,"wires":[["5f6055aa.77027c"]]},{"id":"1cd3bfd8.868f8","type":"split","z":"47cca1f5.5a7a5","g":"461804ba.5e11fc","name":"","splt":" ","spltType":"str","arraySplt":1,"arraySpltType":"len","stream":false,"addname":"","x":630,"y":1360,"wires":[["5026a5c9.de99bc"]]},{"id":"5026a5c9.de99bc","type":"function","z":"47cca1f5.5a7a5","g":"461804ba.5e11fc","name":"Separate Mac Addresses","func":"for(var i = 0; i<20; i++){\n    if (msg.payload[i] == \":\"){\n        i++;\n        i++;\n        i++;\n        if (msg.payload[i] == \":\"){\n            return msg;\n        }\n    }\n}\nreturn;","outputs":1,"noerr":0,"initialize":"","finalize":"","x":170,"y":1420,"wires":[["e134255b.a0fe28"]]},{"id":"e134255b.a0fe28","type":"function","z":"47cca1f5.5a7a5","g":"461804ba.5e11fc","name":"If phone is on wifi","func":"var temp = msg.payload;\nmsg.payload.chatId = 'xxxxxxxx';\nmsg.payload = null;\nif (temp == \"xx:xx:xx:xx:xx:xx\"){\n    msg.payload = \"Alex's 1st phone\";\n}\nif (temp == \"xx:xx:xx:xx:xx:xx\"){\n   msg.payload = \"GF's Phone\";\n}\nif (temp == \"xx:xx:xx:xx:xx:xx\"){\n   msg.payload = \"Alex's 2nd Phone\";\n}\nif (msg.payload !== null){\n    return msg;\n}","outputs":1,"noerr":0,"initialize":"","finalize":"","x":390,"y":1420,"wires":[["93a46325.35aa6","6f3fdc8a.1e5ee4"]],"info":"Need to enter the mac addresses of the devices you want to see if are on the wifi"},{"id":"f696ef40.d999e","type":"ui_button","z":"47cca1f5.5a7a5","g":"461804ba.5e11fc","name":"","group":"62c17ab5.5a7d74","order":3,"width":3,"height":1,"passthru":true,"label":"Who is on the Wifi?","tooltip":"","color":"","bgcolor":"","icon":"","payload":"xxx","payloadType":"str","topic":"","x":150,"y":1340,"wires":[["cd932589.d84fa8","ff9b0f43.ecf17"]]},{"id":"f7562bda.058078","type":"comment","z":"47cca1f5.5a7a5","g":"461804ba.5e11fc","name":"Determines who is on the Wifi Network","info":"","x":390,"y":1220,"wires":[]},{"id":"93a46325.35aa6","type":"file","z":"47cca1f5.5a7a5","g":"461804ba.5e11fc","name":"Create and Append phoneOnWifi.txt","filename":"Documents/NodeRed/phoneOnWifi.txt","appendNewline":true,"createDir":false,"overwriteFile":"false","encoding":"utf8","x":210,"y":1480,"wires":[["d012c9.4400bd38"]]},{"id":"d012c9.4400bd38","type":"file in","z":"47cca1f5.5a7a5","g":"461804ba.5e11fc","name":"Read phoneOnWifi.txt","filename":"Documents/NodeRed/phoneOnWifi.txt","format":"utf8","chunk":false,"sendError":false,"encoding":"utf8","x":480,"y":1480,"wires":[["c46f20ae.71c2d"]]},{"id":"c46f20ae.71c2d","type":"ui_text","z":"47cca1f5.5a7a5","g":"461804ba.5e11fc","group":"62c17ab5.5a7d74","order":5,"width":6,"height":1,"name":"Phone on Wifi","label":"On the WIFI:","format":"{{msg.payload}}","layout":"col-center","x":700,"y":1480,"wires":[]},{"id":"9a0246bd.e02b18","type":"file","z":"47cca1f5.5a7a5","g":"461804ba.5e11fc","name":"Delete phoneOnWifi.txt","filename":"Documents/NodeRed/phoneOnWifi.txt","appendNewline":true,"createDir":false,"overwriteFile":"delete","encoding":"utf8","x":630,"y":1260,"wires":[[]]},{"id":"ff9b0f43.ecf17","type":"file","z":"47cca1f5.5a7a5","g":"461804ba.5e11fc","name":"Create phoneOnWifi.txt","filename":"Documents/NodeRed/phoneOnWifi.txt","appendNewline":true,"createDir":false,"overwriteFile":"false","encoding":"utf8","x":390,"y":1260,"wires":[["9a0246bd.e02b18"]]},{"id":"d4620964.2282c8","type":"telegram sender","z":"47cca1f5.5a7a5","g":"461804ba.5e11fc","name":"","bot":"","haserroroutput":false,"outputs":1,"x":710,"y":1420,"wires":[[]]},{"id":"6f3fdc8a.1e5ee4","type":"change","z":"47cca1f5.5a7a5","g":"461804ba.5e11fc","name":"set","rules":[{"t":"move","p":"payload","pt":"msg","to":"payload.content","tot":"msg"},{"t":"set","p":"payload.type","pt":"msg","to":"message","tot":"str"},{"t":"set","p":"payload.chatId","pt":"msg","to":"xxxxxxxxxx","tot":"str"}],"action":"","property":"","from":"","to":"","reg":false,"x":550,"y":1420,"wires":[["d4620964.2282c8"]]},{"id":"3577991d.1eaae6","type":"telegram command","z":"47cca1f5.5a7a5","g":"461804ba.5e11fc","name":"/whoishome","command":"/whoishome","bot":"","strict":false,"hasresponse":false,"useregex":false,"removeregexcommand":false,"outputs":1,"x":110,"y":1260,"wires":[["f696ef40.d999e","ff9b0f43.ecf17"]],"info":"need to add your telegram bot.\nsending your telegram bot the command they will activate the button"},{"id":"62c17ab5.5a7d74","type":"ui_group","z":"","name":"General","tab":"377d7947.f2eda6","order":1,"disp":true,"width":6,"collapse":false},{"id":"377d7947.f2eda6","type":"ui_tab","z":"","name":"Alex's Home Automation GUI","icon":"dashboard","disabled":false,"hidden":false}]
  ```
  You will need to configure your Telgram Bot in both the sender and reciever, enter in the mac addresses of the devices you would like to be notified about in the 'If phone   is on wifi node', and choose a NodeRED display group for the button and text nodes.

* Example flow
```
  insert flow code here
```
  Description

### ESP32
What ESP32 should not matter much. Be sure you have a pinout of the device as you will need to choose your own pin to use.<br/>
The code for your ESP32 and how to configure it to control a relay through MQTT can be found [here](https://github.com/Alextros00/ESP32-MQTT-Relay-Control-Project).

### Telegram
Telegram can be used to add the ability to control NodeRED from your phone and automate more processes but is not required for use. You could stricktly use the NodeRED dashboard to control your system.<br/>
My current commands that I can use are:<br/>
* `/water` - records that I drank a bottle of water
* `/poop` - records that I took a poop
* `/piss` - records that I took a pee
* `/whoishome` - replys with who is on my home wifi
* `/alive` - replys with what devices are responding on the system
* `doorlighton` - turns on the light by the door 
* `doorlightoff` - turns off the light by the door
* `bedsidelampon` - turns on the light by my bed
* `bedsidelampoff` - turns off the light by my bed

<!-- USAGE EXAMPLES -->
## Usage
The system can be utilized in two ways, through the Telegram-Bot or through the NodeRED Dashboard.<br/>
_For more examples, please refer to the [Documentation](https://example.com)_



<!-- ROADMAP -->
## Roadmap
See the [open issues](https://github.com/Alextros00/Home-Automation-NodeRED-ESP-Telegram/issues) for a list of proposed features (and known issues).<br/>
This project will continue to grow in my free time to automate everything... except working out... that you just have to do.

<!-- LICENSE -->
## License
Distributed under the MIT License. See `LICENSE` for more information but basically you can take my code but I would appreciate a coffee!

<!-- CONTACT -->
## Contact
##### Alex Trostle
Alextros00@gmail.com - [LinkedIn](https://www.linkedin.com/in/alex-trostle/) - [Instagram](https://www.instagram.com/alextros0/) <br />
<a href="https://www.buymeacoffee.com/AlexTrostle" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee" style="height: 41px !important;width: 174px !important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 3px 2px 0px     rgba(190,190, 190, 0.5) !important;" ></a><br/>
Project Link: [https://github.com/Alextros00/Home-Automation-NodeRED-ESP-Telegram](https://github.com/Alextros00/Home-Automation-NodeRED-ESP-Telegram)

<!-- ACKNOWLEDGEMENTS -->
## Acknowledgements
##### ESP
* []()
* []()
##### NodeRED
* []()
* []()
##### Other
* []()
* []()

Links used in the creation of this page:
* [GitHub Emoji Cheat Sheet](https://www.webpagefx.com/tools/emoji-cheat-sheet)
* [Img Shields](https://shields.io)
* [Choose an Open Source License](https://choosealicense.com)
* [GitHub Pages](https://pages.github.com)
* [Animate.css](https://daneden.github.io/animate.css)
* [Loaders.css](https://connoratherton.com/loaders)
* [Slick Carousel](https://kenwheeler.github.io/slick)
* [Smooth Scroll](https://github.com/cferdinandi/smooth-scroll)
* [Sticky Kit](http://leafo.net/sticky-kit)
* [JVectorMap](http://jvectormap.com)
* [Font Awesome](https://fontawesome.com)

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/Alextros00/Home-Automation-NodeRED-ESP-Telegram.svg?style=for-the-badge
[contributors-url]: https://github.com/Alextros00/Home-Automation-NodeRED-ESP-Telegram/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/Alextros00/Home-Automation-NodeRED-ESP-Telegram.svg?style=for-the-badge
[forks-url]: https://github.com/Alextros00/Home-Automation-NodeRED-ESP-Telegram/network/members
[stars-shield]: https://img.shields.io/github/stars/Alextros00/Home-Automation-NodeRED-ESP-Telegram.svg?style=for-the-badge
[stars-url]: https://github.com/Alextros00/Home-Automation-NodeRED-ESP-Telegram/stargazers
[issues-shield]: https://img.shields.io/github/issues/Alextros00/Home-Automation-NodeRED-ESP-Telegram.svg?style=for-the-badge
[issues-url]: https://github.com/Alextros00/Home-Automation-NodeRED-ESP-Telegram/issues
[license-shield]: https://img.shields.io/github/license/Alextros00/Home-Automation-NodeRED-ESP-Telegram.svg?style=for-the-badge
[license-url]: https://github.com/Alextros00/Home-Automation-NodeRED-ESP-Telegram/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/alex-trostle/
