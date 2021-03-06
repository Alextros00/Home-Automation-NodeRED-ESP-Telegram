# Home-Automation-NodeRED-ESP-Telegram
<!-- PROJECT SHIELDS -->
<!--[![Contributors][contributors-shield]][contributors-url]-->
<!--[![Forks][forks-shield]][forks-url]-->
<!--[![MIT License][license-shield]][license-url]-->
<!--![GitHub search hit counter](https://img.shields.io/github/search/Alextros00/Home-Automation-NodeRED-ESP-Telegram/hit?style=for-the-badge)-->
[![LinkedIn][linkedin-shield]][linkedin-url]
[![Stargazers][stars-shield]][stars-url]
[![Features][issues-shield]][issues-url]
[![GitHub last commit](https://img.shields.io/github/last-commit/Alextros00/Home-Automation-NodeRED-ESP-Telegram?style=for-the-badge)](https://github.com/Alextros00/Home-Automation-NodeRED-ESP-Telegram)
[![My Projects Website](https://img.shields.io/badge/MyProjects-Website-red?style=for-the-badge)](https://alextros00.wixsite.com/alex-trostle)

<!-- PROJECT LOGO -->
<br />
<p align="center">
  <a href="https://github.com/Alextros00/Home-Automation-NodeRED-ESP-Telegram">
    <img src="images/ESP32_RelayControl_Hardware.jpg" alt="ESP32 Wired to control a light via relay" width="30%" height="30%">
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
	<li><a href="#mosquitto-mqtt-broker">Mosquitto MQTT</a></li>
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
There were many parts to this project. Some sub-projects that I did in order to build up to this complexity can be found on [my github](https://github.com/Alextros00).

#### Main Components
* [Raspberry Pi 4](https://www.raspberrypi.org/products/raspberry-pi-4-model-b/?resellerType=home&variant=raspberry-pi-4-model-b-8gb). <sup>&dagger;</sup>
  * [MQTT through Mosquitto](https://mosquitto.org/)
  * [NodeRED](https://nodered.org/)
* [ESP32](https://www.espressif.com/en/products/socs/esp32)
* [Telegram](https://telegram.org/)

<sup>&dagger;: I us 8GB but don't really think it is required.</sup>

### Architecture
<p align="center">
  <a href="https://github.com/Alextros00/Home-Automation-NodeRED-ESP-Telegram">
    <img src="images/Auto_Home_Architecture.png" alt="Architecture" width="60%" height="60%">
  </a>
</p>

<!-- GETTING STARTED -->
## Getting Started
These steps will take you through the overall home automation system. The system consists of other repos for specifics linked throughout this README doc.

<!-- Prerequisites -->
### Prerequisites
The software used is free and mostly open source.<br/>
It would help to have the hardware below.
* Laptop
* Smartphone
* At least one [ESP32](https://www.espressif.com/en/products/socs/esp32)
* [Raspberry Pi 4](https://www.raspberrypi.org/products/raspberry-pi-4-model-b/?variant=raspberry-pi-4-model-b-8gb) <sup>&dagger;</sup> <sup>&Dagger;</sup> <br/>
<sup>&dagger;: Raspberry Pi 4 should be running [Raspbian Operating System](https://projects.raspberrypi.org/en/projects/noobs-install)</sup><br/>
<sup>&Dagger;: Needs to be connected to and using a 2.4GHz network. This is because the ESP32 currently(Dec 2020) cannot connect to 5GHz networks.</sup><br/>

<!-- ESP32 -->
### ESP32
You can get really cheap knock off ESP32s on [AliExpress](https://www.aliexpress.com/)<br/>
Some ESP devices that I use are: ESP-WROOM-32, ESP-32S, ESP32-CAM, ESP-EYE<br/>

#### ESP-IDF
1. Use the installer for [Windows](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/get-started/windows-setup.html), [Linux](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/get-started/linux-setup.html) or [Mac OS](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/get-started/macos-setup.html). <br/>
<sup>&Dagger;:Check the [official site](https://esp-idf.readthedocs.io/en/latest/get-started/index.html) for more info.</sup>
2. Fork my repo and Clone my ESP32 MQTT Light Control repository using this command. Replace the xxxxx with the repo.<br/>
   ```git clone -b --recursive https://github.com/Alextros00/xxxxxxxxxxx```

##### Commands to Remember
Build and flash the project onto your device.<br/>
```idf.py build & flash```<br/>
Monitor the logs of your device<br/>
```idf.py monitor```<br/>
To exit the monitor us `Ctrl + ]` or `Ctrl` and  `]` at the same time

#### ESP32 Repos
1. [Light(Relay) Control over MQTT.](https://github.com/Alextros00/ESP32-MQTT-Relay-Control)
2. [MC38 Door Sensor to track opening and closing of doors or windows](https://github.com/Alextros00/ESP32_MC38_DOOR_SENSOR)

<!-- Mosquitto -->
### Mosquitto MQTT Broker
> MQTT is a machine-to-machine (M2M)/"Internet of Things" connectivity protocol. It was designed as an extremely lightweight publish/subscribe messaging transport. It is useful for connections with remote locations where a small code footprint is required and/or network bandwidth is at a premium [[mqtt.org](http://mqtt.org)]. The Mosquitto broker will be installed on your Raspberry Pi as the broker and your ESP devices will be clients. [Learn more here.](http://www.steves-internet-guide.com/mqtt-works/)

Navigate to the terminal and follow these steps for the installation.
1. Update your Raspberry Pi<br/>
```sudo apt-get update```
2. Install Mosquitto<br/>
```sudo apt-get install mosquitto```
3. Install Mosquitto Client<br/>
```sudo apt-get install mosquitto-clients```
<br/><sup>&Dagger;: Note for later: Port of your Mosquitto Broker, most likely 1883; Server Mosquitto Broker is running on, most likely the ip address of your Raspberry Pi</sup><br/>
<img src="http://www.steves-internet-guide.com/wp-content/uploads/mqtt-message-flow.jpg" width="30%" height="30%">

<!-- NodeRED -->
### NodeRED
>[NodeRED](http://nodered.org) is a low-code programming tool for wiring together hardware devices, APIs and online services for event driven applications. The browser-based editor that makes it easy to wire together flows using the wide range of nodes in the palette that can be deployed to its runtime in a single-click.

[Install NodeRED on your Raspberry Pi](https://nodered.org/docs/getting-started/local)

#### Flows
Many of the flows used can be found in [my collection at nodered.org](https://flows.nodered.org/collection/RV7rLt9tjepZ). Here the general functionality of each flow will be described and more details(and the flow itself:) are provided on [my NodeRED page](https://flows.nodered.org/user/Alextros00).

##### Functionality
Light Control: lights can be controlled through a Telegram command, a button by the lamp, a button on my NodeRED Dashboard, and a webhook on my phone's home screen
* Light Control: Lights can be controled through time of day, a [Telegram Command using a inline keyboard](https://flows.nodered.org/flow/c8194f9d056455018d2da8ef7e109733), the NodeRED Dashboard, a webhook on my phone homescreen, or even a good old button by the lamp
* Raspberry Pi Status: The Raspberry Pi 4 has been rumored to overheat. I monitor the temperature and recieve notification and text if it goes to high
* Local Free Listings: The dashboard displays local free listings from FreeCycle and Craigslist
* Motivational Dashboard: When idol the dashboard displays a motivational image, quote and Bible verse that rotate regularly. I also recieve a [daily motivational message.]()

##### Flow Gallery
<p float="middle">
  <img src="images/NodeRED3.png" width="30%" height="30%" />
  <img src="images/NodeRED_Flow_webhooks.png" width="30%" height="30%" />
  <img src="images/NodeRED_Flow_FreeStuff.png" width="30%" height="30%" />
  <img src="images/NodeRED_Flow_DailyQuote.png" width="30%" height="30%" />
  <img src="images/NodeRED_Flow_DeviceAlive.png" width="30%" height="30%" />
  <img src="images/NodeRED_Flow_DoorLight.png" width="30%" height="30%" />
  <img src="images/NodeRED_Flow_RandomPhoto.png" width="30%" height="30%" />
  <img src="images/NodeRED_Flow_WhoIsOnWifi.png" width="30%" height="30%" />
</p>

<!-- Telegram -->
### Telegram
Telegram adds the ability to control the system from your phone but is not required for use. You could stricktly use the NodeRED dashboard to control your system. In this implementation, Telegram does not directly control any devices but rather goes through NodeRED using the [node-red-contrib-telegrambot](https://flows.nodered.org/node/node-red-contrib-telegrambot) library.<br/>
#### Commands
* `/water` 	    - records that I drank a bottle of water
* `/poop` 	    - records that I took a poop
* `/piss` 	    - records that I took a pee
* `/lights`	    - displays inline keyboard to choose which light to change and what to do with it
* `/doorlighton`    - turns on door light... I know its redundant just use `/lights`
* `/doorlightoff`   - turns off door light... I know its redundant just use `/lights`
* `/bedsidelalmpon` - turns on bedside light... I know its redundant just use `/lights`
* `/bedsidelalmpoff`- turns off bedside light... I know its redundant just use `/lights`
* `/sleepin`	    - delays the auto turn on of my lights by 30 minutes
* `/motivation`     - changes the motivational display on the dashboard and sends motivational image over Telegram
* `/whoishome` 	    - replys with who is on my home wifi
* `/alive` 	    - replys with what devices are responding on the system
* `/temp`	    - replys with the temp of each device that is connected
* `/help` 	    - responds with the Telegram ChatId 
#### Notifications
* `Raspberry Pi is over 65 degree C` - Tells me when the Raspberry Pi has reached temperatures over 65C.
* `Motivational Image` - at 11am daily I recieve a motivational quote to keep me going until lunch!
* `Motivational Quote` - at 2pm daily I recieve a motivational image to keep me going until dinner!

<!-- USAGE EXAMPLES -->
## Usage
The system can be utilized in two ways, through the Telegram-Bot or through the NodeRED Dashboard.<br/>
#### Usage through Telegram
Telegram sends me [notifications](#notifications) and I can send it [commands](#commands).
#### Usage through the NodeRED Dashboard
The NodeRED Dashboard can be used to control the system through buttons, text boxes and switches, but also displays alot of information.<br/>


<!-- ROADMAP -->
## Roadmap
See the [open issues](https://github.com/Alextros00/Home-Automation-NodeRED-ESP-Telegram/issues) for a list of proposed features (and known issues).<br/>
This project will continue to grow in my free time to automate everything... except for working out... that I just have to do.

<!-- LICENSE -->
## License
Distributed under the MIT License. See `LICENSE` for more information but basically you can take my code but I would appreciate a coffee!

<!-- CONTACT -->
## Contact
##### Alex Trostle - [GitHub](https://github.com/Alextros00) - [Email](Alextros00@gmail.com) - [LinkedIn](https://www.linkedin.com/in/alex-trostle/) - [Instagram](https://www.instagram.com/alextros0/) - [My Website](https://alextros00.wixsite.com/alex-trostle)<br />
<a href="https://www.buymeacoffee.com/AlexTrostle" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee" style="height: 41px !important;width: 174px !important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 3px 2px 0px     rgba(190,190, 190, 0.5) !important;" ></a><br/>

<!-- ACKNOWLEDGEMENTS -->
## Acknowledgements
* [Nice README page I refferenced and got me started](https://github.com/ETS-PoliTO/esp32-sniffer/edit/master/README.md)

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

<!--
LINKS USED IN THE CREATION OF THIS PAGE:
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
-->

<!--
Notes to remember on using Markdown:
[![Product Name Screen Shot][product-screenshot]](https://example.com)
-->
