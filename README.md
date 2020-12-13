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
You will need [NodeRED](http://nodered.org) to be installed on your Raspberry Pi. To do so follow [these steps](https://nodered.org/docs/getting-started/local).

The only flow that is required to start controlling an ESP32 is the ESP32 MQTT flow. The rest of my flows can be found on my NodeRED flow project.
<br/><img src="images/NodeRED3.png" width="50%" height="50%">

#### Example Flows


### ESP32
What ESP32 should not matter much. Be sure you have a pinout of the device as you will need to choose your own pin to use.<br/>
The code for your ESP32 and how to configure it to control a relay through MQTT can be found [here](https://github.com/Alextros00/ESP32-MQTT-Relay-Control-Project).

### Telegram
Telegram can be used to add the ability to control NodeRED from your phone and automate more processes but is not required for use. You could stricktly use the NodeRED dashboard to control your system.<br/>
#### Commands <br/>
* `/water` - records that I drank a bottle of water
* `/poop` - records that I took a poop
* `/piss` - records that I took a pee
* `/whoishome` - replys with who is on my home wifi
* `/alive` - replys with what devices are responding on the system
* `doorlighton` - turns on the light by the door 
* `doorlightoff` - turns off the light by the door
* `bedsidelampon` - turns on the light by my bed
* `bedsidelampoff` - turns off the light by my bed
#### Notifications <br/>
* `Raspberry Pi is over 65 degree C` - Tells me when the Raspberry Pi has reached temperatures over 65C. 

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
