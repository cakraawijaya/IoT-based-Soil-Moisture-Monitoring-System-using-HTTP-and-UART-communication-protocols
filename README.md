[![Open Source Love](https://badges.frapsoft.com/os/v1/open-source.svg?style=flat)](https://github.com/ellerbrock/open-source-badges/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?logo=github&color=%23F7DF1E)](https://opensource.org/licenses/MIT)
![GitHub last commit](https://img.shields.io/github/last-commit/cakraawijaya/IoT-based-Soil-Moisture-Monitoring-System-using-HTTP-and-UART-communication-protocols?logo=Codeforces&logoColor=white&color=%23F7DF1E)
![Project1](https://img.shields.io/badge/Project-%2D1-Arduino-light.svg?style=flat&logo=arduino&logoColor=white&color=%23F7DF1E)
![Project2](https://img.shields.io/badge/Project-%2D2-ESP-%2D01-light.svg?style=flat&logo=espressif&logoColor=white&color=%23F7DF1E)
![Type](https://img.shields.io/badge/Type-Personal%20Experiment-light.svg?style=flat&logo=gitbook&logoColor=white&color=%23F7DF1E)

# IoT-based-Soil-Moisture-Monitoring-System-using-HTTP-and-UART-communication-protocols
ESP-01-based IoT systems generally use AT commands to be able to perform actions in a network. These AT commands are known to be many. In addition, the combination of commands is difficult to understand for a beginner. Therefore, this project was created to improve the convenience of the ESP-01-based IoT system. In this case, the author used the UART protocol on the development board side. This project has been implemented and took approximately 2 weeks. Two types of development boards were used. Arduino Uno R3 is used to retrieve soil moisture data from the sensor which is then sent to ESP-01 via UART communication: Serial Software. Meanwhile, ESP-01 is used to receive data from Arduino Uno via UART communication: Hardware Serial and then send the data to Ubidots via HTTP protocol.

<br><br>

## Project Requirements
| Part | Description |
| --- | --- |
| Development Board | • Arduino Uno R3<br>• ESP-01 |
| Code Editor | Arduino IDE |
| Programmer Tools | CH340-ESP01 USB |
| Driver | CH340 USB Driver |
| IoT Platform | Ubidots |
| Communications Protocol | • Hypertext Transfer Protocol (HTTP)<br>• Universal Asynchronous Receiver-Transmitter (UART) |
| IoT Architecture | 3 Layer |
| Programming Language | C/C++ |
| Arduino Library | • SoftwareSerial (default)<br>• Ubidots-ESP8266 |
| Sensor | Capacitive Soil Moisture Sensor (x1) |
| Other Components | • USB type B cable - USB type A (x1)<br>• Jumper cable (1 set)<br>• ESP-01 Adapter (x1) |

<br><br>

## Download & Install
1. Arduino IDE

   <table><tr><td width="810">
         
   ```
   https://bit.ly/ArduinoIDE_Installer
   ```

   </td></tr></table><br>
   
2. CH340 USB Driver

   <table><tr><td width="810">
   
   ```
   https://bit.ly/CH340_USBdriver
   ```
   
   </td></tr></table>
   
<br><br>

## Project Designs
<table>
<tr>
<th width="840">Infrastructure</th>
</tr>
<tr>
<td><img src="Assets/Documentation/Diagram/Infrastructure.jpg" alt="infrastructure"></td>
</tr>
</table>
<table>
<tr>
<th width="840">Block Diagram</th>
</tr>
<tr>
<td><img src="Assets/Documentation/Diagram/Block Diagram.jpg" alt="block-diagram"></td>
</tr>
</table>
<table>
<tr>
<th width="420">Pictorial Diagram</th>
<th width="420">Wiring</th>
</tr>
<tr>
<td><img src="Assets/Documentation/Diagram/Pictorial Diagram.jpg" alt="pictorial-diagram"></td>
<td><img src="Assets/Documentation/Table/Device Wiring.jpg" alt="wiring"></td>
</tr>
</table>

<br><br>

## Basic Knowledge
• <strong>Serial Communication</strong>

Basically, a device can be communicated with other devices either wirelessly or by cable. Communication between commonly used hardware is ``` Serial Communication ```. It can be known that there are three types of ``` Serial Communication ```, which include: ``` UART (Universal Asynchronous Receiver-Transmitter) ```, ``` SPI (Serial Peripheral Interface) ```, and ``` I2C (Inter Integrated Circuit) ```. ``` Serial UART communication ``` allows each device to act as a ``` master ``` or ``` slave ``` in a limited way. ``` Master ``` is the primary device that has full authority over the control of the Slave, while the ``` Slave ``` is the secondary device that is under the authority of the Master device. There are two kinds of ``` UART Serial Communication ```, namely ``` Hardware Serial ``` and ``` Software Serial ```. ``` Hardware serial communication ``` can be done by connecting the ``` TX ``` and ``` RX ``` pins ``` crosswise ``` on each development board, for example: ``` RX-TX ```, then ``` TX-RX ```. The ``` TX ``` pin is for ``` sending data ```, while the ``` RX ``` pin is for ``` receiving data ```. ``` Serial Software Communication ``` is more or less the same as ``` Serial Hardware Communication ``` in terms of cabling, but there are differences in terms of coding. By using this ``` Serial Software ``` you can overcome the constraints of the limitations of ``` RX ``` and ``` TX ``` pins on the development board. To communicate with this ``` Serial Software ``` is quite easy, namely by using certain ``` Digital Pins ``` as a ``` substitute for TX pins and RX pins ```.<br><br>

• <strong>Internet of Things</strong>

``` Internet of Things (IoT) ``` is a concept where things connected to a network can perform one or more actions in achieving a goal. These actions include data collection, data transmission, data reception, or data processing. Every IoT project requires devices that can connect to WiFi such as ESP. ESP consists of 2 types, namely ``` ESP8266 ``` and ``` ESP32 ```. This is on the market very diverse models, for that you need to readjust to the needs in the project so as not to cause disappointment.

<br><br>

## Arduino IDE Setup
1. Open the ``` Arduino IDE ``` first, then open the project by clicking ``` File ``` -> ``` Open ``` :

   <table><tr><td width="810">
   
      • ``` Master.ino ```
      
      • ``` Slave.ino ```

   </td></tr></table><br>
   
2. Fill in the ``` Additional Board Manager URLs ``` in Arduino IDE

   <table><tr><td width="810">
      
      Click ``` File ``` -> ``` Preferences ``` -> enter the ``` Boards Manager Url ``` by copying the following link :
   
      ```
      http://arduino.esp8266.com/stable/package_esp8266com_index.json
      ```

   </td></tr></table><br>
   
3. ``` Board Setup ``` in Arduino IDE

   <table>
      <tr><th>
         
      i
         
      </th><th width="780">
            
      How to setup the ``` Arduino Uno ``` board
   
      </th></tr>
      <tr><td colspan="2">

      Selecting a board by clicking: ``` Tools ``` -> ``` Board ``` -> ``` Arduino AVR Boards ``` -> ``` Arduino Uno ```
              
      </td></tr>
   </table><br><table>
      <tr><th>
         
      ii
         
      </th><th width="775">

      How to setup the ``` ESP-01 ``` board
            
      </th></tr>
      <tr><td colspan="2">

      • Click ``` Tools ``` section -> ``` Board ``` -> ``` Boards Manager ``` -> Install ``` esp8266 ```.

      • Then selecting a board by clicking: ``` Tools ``` -> ``` Board ``` -> ``` ESP8266 Boards ``` -> ``` Generic ESP8266 Module ```.
            
      </td></tr>
   </table><br>
   
4. ``` Change the Board Speed ``` in Arduino IDE

   <table>
      <tr><th>
         
      i
         
      </th><th width="780">
            
      How to change the speed of ``` Arduino Uno ``` board
   
      </th></tr>
      <tr><td colspan="2">

      Click ``` Tools ``` -> ``` Upload Speed ``` -> ``` 9600 ```
              
      </td></tr>
   </table><br><table>
      <tr><th>
         
      ii
         
      </th><th width="775">

      How to change the speed of ``` ESP-01 ``` board
            
      </th></tr>
      <tr><td colspan="2">

      Click ``` Tools ``` -> ``` Upload Speed ``` -> ``` 9600 ```
            
      </td></tr>
   </table><br>
   
5. ``` Install Library ``` in Arduino IDE

   <table><tr><td width="810">
         
      Download all the library zip files. Then paste it in the: ``` C:\Users\Computer_Username\Documents\Arduino\libraries ```

   </td></tr></table><br>

6. ``` Port Setup ``` in Arduino IDE

   <table><tr><td width="810">
         
      Click ``` Port ``` -> Choose according to your device port ``` (you can see in device manager) ```

   </td></tr></table><br>

7. Change the ``` WiFi Name ```, ``` WiFi Password ```, and so on according to what you are currently using.<br><br>

8. Before uploading the program please click: ``` Verify ```.<br><br>

9. If there is no error in the program code, the next step is to use the ``` ESP-01 ``` programming tool according to the procedure. Then click: ``` Upload ```. While ``` Arduino Uno ``` can be done directly without using programming tools.<br><br>

10. If there is still a problem when uploading the program, then try checking the ``` driver ``` / ``` port ``` / ``` programmer tool ``` / ``` others ``` section.

<br><br>

## CH340-ESP01 USB Setup
<img width="840" src="Assets/Documentation/Setup/ESP01.jpg" alt="esp01-setup"><br><br><br>

1. ``` Programming Mode ``` :
      
   • Attach the ``` ESP-01 ``` to the ``` CH340-ESP01 USB ```.

   • Press and hold the button on the ``` CH340-ESP01 USB ```, and plug it into computer/laptop.
   
   • Release the button when the device is recognized by the computer/laptop.
   
   • Please ``` upload ``` the program.<br><br><br>
   
2. ``` Operating Mode ``` :
   
   • Release the ``` CH340-ESP01 USB ``` from the computer/laptop.
   
   • The program code that has been embedded in this ``` ESP-01 board ``` is ready for operation (no more programming activities).

   • Release the ``` ESP-01 ``` from the ``` CH340-ESP01 USB ```. Do the wiring as shown in the pictorial diagram.

<br><br>

<h3><img src="https://github.com/user-attachments/assets/932b96eb-cbc7-42f1-8938-43cb431889a5" width="16" height="16"> Notes :</h3>
<blockquote>
   <ul>
   <li>
   
   To upload the program, besides using the ``` CH340-ESP01 USB ```, you can also use other programming tools such as: ``` CP2102 USB ```, ``` CH340 USB ```, ``` FTDI USB ```, or with ``` PL2303 USB ```.
   
   </li>
   <li>
   
   Based on experience, I admit that using the ``` CH340-ESP01 USB ``` is much better than other programming tools because it does not require a cable to be connected to a computer/laptop.
   
   </li>
   </ul>
</blockquote>

<br><br>

## Ubidots Setup
1. Getting started with Ubidots :

   <table><tr><td width="810">
   
      • Please <a href="https://industrial.ubidots.com/accounts/signin/">Log in</a> to access the ``` Ubidots ``` service.
      
      • If you don't have a ``` Ubidots ``` account yet, please create one.

   </td></tr></table><br>

2. Creating dashboards : 

   <table><tr><td width="810">
   
      • In the ``` Data ``` section -> select ``` Dashboards ``` menu.
   
      • Delete the Ubidots built-in demo dashboard before creating a new dashboard.
   
      • Click ``` Add new Dashboard ```.
   
      • ``` Name ```, ``` Tags ```, ``` Default time range ``` -> customize it to your needs.

      • ``` Dynamic Dashboard ``` -> change it to ``` Dynamic (Single Device) ```.

      • ``` Default Device ``` -> select the device you want to display.

      • Leave the other settings alone -> then click ``` SAVE ```.

   </td></tr></table><br>

3. Creating widget : 

   <table><tr><td width="810">
   
      • Make sure you are in the ``` Dashboards ``` menu.
   
      • Click ``` + Add new widget ```.
   
      • Please choose according to your needs. In this project, the author uses ``` Line chart ``` for data visualization.
   
      • Please set the variables that you want to use on the widget by clicking ``` + ADD VARIABLE ```, then click ``` ✅ Checklist ``` to save.
   
      • If you want to change the content of the widget, please click the ``` pencil ``` symbol -> if so, then click ``` ✅ Checklist ``` to save.

   </td></tr></table><br>

4. Firmware configuration : 

   <table><tr><td width="810">
   
      • Click the ``` User ``` section in the bottom left corner -> then select ``` API Credentials ```.
   
      • Copy the ``` Default token ``` -> paste it into the firmware code. An example is as follows:

      <table><tr><td width="780">
   
      ```ino
      const String token = "BBUS-aRZvtYRMM7IWbrKFcICR30YYP7dh5Q"; // define ubidots token
      ```

      </td></tr></table>

   </td></tr></table>

<br><br>

## Get Started
1. Download and extract this repository.<br><br>
   
2. Make sure you have the necessary electronic components.<br><br>
   
3. Make sure your components are designed according to the diagram.<br><br>
   
4. Configure your device according to the settings above.<br><br>

5. Please enjoy [Done].

<br><br>

## Highlights
<table>
<tr>
<th width="420">Hardware</th>
<th width="420">Serial Monitor & IoT Platform: Ubidots</th>
</tr>
<tr>
<td><img src="Assets/Documentation/Experiment/Device.jpg" alt="hardware"></td>
<td><img src="Assets/Documentation/Experiment/Serial Monitor Ubidots.jpg" alt="serialmonitor-iotplatform"></td>
</tr>
</table>

<br><br>

## Appreciation
If this work is useful to you, then support this work as a form of appreciation to the author by clicking the ``` ⭐Star ``` button at the top of the repository.

<br><br>

## Disclaimer
This application is my own work and is not the result of plagiarism from other people's research or work, except those related to third party services which include: libraries, frameworks, and so on.

<br><br>

## LICENSE
MIT License - Copyright © 2024 - Devan C. M. Wijaya, S.Kom

Permission is hereby granted without charge to any person obtaining a copy of this software and the software-related documentation files to deal in them without restriction, including without limitation the right to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons receiving the Software to be furnished therewith on the following terms:

The above copyright notice and this permission notice must accompany all copies or substantial portions of the Software.

IN ANY EVENT, THE AUTHOR OR COPYRIGHT HOLDER HEREIN RETAINS FULL OWNERSHIP RIGHTS. THE SOFTWARE IS PROVIDED AS IS, WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESS OR IMPLIED, THEREFORE IF ANY DAMAGE, LOSS, OR OTHERWISE ARISES FROM THE USE OR OTHER DEALINGS IN THE SOFTWARE, THE AUTHOR OR COPYRIGHT HOLDER SHALL NOT BE LIABLE, AS THE USE OF THE SOFTWARE IS NOT COMPELLED AT ALL, SO THE RISK IS YOUR OWN.
