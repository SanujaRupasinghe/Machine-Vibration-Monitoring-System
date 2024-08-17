<div align="left">
  <img src="logo.PNG" alt="Project Logo" width="100" style="margin-right: 20px;">
</div>

# "VibroGuard": A Hardware-Software Co-Solution for Monitoring and Analyzing Vibrations of Industrial Machines 

## By <a href="https://github.com/linukaratnayake">Linuka Ratnayake</a>, <a href="https://github.com/SanujaRupasinghe">Sanuja Rupasinghe</a>

### Overview

#### Use Case

Many machines used in the industry tend to vibrate in their natural operating conditions. However, these vibrations can be analyzed to get valuable insights about the machine, such as detecting anomalous behavior or an indication for a near-future repair.

#### Project Scope

This project is done as a partial fulfillment for EN2160: Electronic Design Realization module in the Semester 4 curriculum in the Department of Electronic and Telecommunication Engineering at University of Moratuwa, Sri Lanka.

Project **"VibroGuard"** was aimed to design and develop an industry level solution. Accordingly, a hardware-software co-solution is developed including PCB, Enclosure, Software, and Firmware.

https://github.com/user-attachments/assets/75e11f41-68b1-4032-a1a3-b93472fd98e2

### PCB Design

Product hardware consisted of two modules. Each of them contained a separate 2-layer PCB designed using **Altium Designer**.

| **Main Module** | **Sensor Module** |
|:--:|:--:|
| ![Main Module Soldered](PCB%20Design/Images/Microcontroller_Soldered_Front.jpeg) | <img src="PCB%20Design/Images/Sensor_Soldered_Front.jpeg" style="width: 90%;"> |
| ![Main Module Top](PCB%20Design/Images/Microcontroller_Top.png) | <img src="PCB%20Design/Images/Sensor_Top.png" style="width: 70%;"> |
| ![Main Module Bottom](PCB%20Design/Images/Microcontroller_Bottom.png) | <img src="PCB%20Design/Images/Sensor_Bottom.png" style="width: 70%;"> |


PCB design files and schematics can be found <a href="PCB%20Design">here</a>.



### Firmware Design

ATmega328P-AU microcontroller is used along with FT232RL Serial UART IC in the Main Module. The microcontroller in programmed in **C++**, using register level programming such as IO port manipulation, UART and I2C communication, sampling accelerometer reading with given sampling frequency, etc.

The code can be found <a href="Firmware%20Development/Microcontroller_Code/">here</a>.

### Enclosure Design

Similar to PCB design, enclosures were also designed for the two separate modules in **SOLIDWORKS** and 3D printed. In the process, moldability of the designs were also considered.

| **Main Module** | **Sensor Module** |
|:--:|:--:|
| <img src="Enclosure%20Design/Images/Main_Controller_Enclosure.PNG" style = "width: 94%;"> | ![Sensor Module Enclosure](Enclosure%20Design/Images/Sensor_Enclosure.PNG) |

Enclosure design files can be found <a href="Enclosure%20Design">here</a>.

### Software Design
#### Data Visualization

Once the acceleration data is sampled and sent by the microcontroller via the UART interface, it is acquired by the computer, and displayed on screen in graphical format. **Matplotlib** is used for data visualization.

Data visualization can be performed in two modes.

<ol> 
<li> Just visualize incoming data of vibrations. </li>
<li> Visualize with detected anomalies (anomalies in red). </li>
</ol>

| **Just Visualizing** | **Visualizing with Anomalies** |
|:--:|:--:|
| ![Just Visualize](Software%20Development/Intial%20Test%20Codes/Visualize%20Data/Images/Just_Visualize.png) | ![Visualize Anomalies](Software%20Development/Intial%20Test%20Codes/Visualize%20Data/Images/Visualize_Anomalies.png) |

For code in initial stages of data visualization, see <a href="Software%20Development/Intial%20Test%20Codes/Visualize%20Data/">here</a>.

#### Machine Learning Models

Anomaly detection is done by utilizing autoencoders, by utilizing **TensorFlow**. Three copies of the same model architecture are used for the x, y, and z axes of the accelerometer data streams.

User is given the flexibility to train their own models or load saved models depending on the situation.
e.g.: If the device is connected to a new vibrating machine, models should be re-trained accordingly.

For code in initial stages of machine learning model development, see <a href="Software%20Development/Intial%20Test%20Codes/Anomaly%20Detection/">here</a>.

#### Graphical User Interface

A Graphical User Interface (GUI) application was developed using **Tkinter** framework in Python. With the GUI application, the user can navigate through the following options.

<ul>
<li> Set baud rate and port (COM port in Windows) where the device is connected. </li>
<li> Collect a dataset of,
<ol> <li> specified number of samples </li>
or <li>for a specified amount of time, </li></ol>and save it for future use. </li>
<li> Train machine learning models by,
<ol><li> Collect data and train at the same time </li>
<li> Train using data collected before </li>
<li> Load saved models </li> </ol>
<li> Visualize data either,
<ol> <li> without anomaly detection (just visualize incoming data) </li>
or
<li> with anomaly detection </li> </ol>
</ul>

| ![Select COM](Software%20Development/Final%20GUI%20Application%20-%20Tkinter/Images/GUI_Select_COM.png) | ![Collect Data](Software%20Development/Final%20GUI%20Application%20-%20Tkinter/Images/GUI_Collect_Data.png) |
|:--:|:--:|
| ![Train ML Model](Software%20Development/Final%20GUI%20Application%20-%20Tkinter/Images/GUI_Train_ML_Model.png) | ![Visualize Data](Software%20Development/Final%20GUI%20Application%20-%20Tkinter/Images/GUI_Visualize_Data.png) |


Code related to GUI application development and integration of both data visualization and machine learning parts can be found <a href="Software%20Development/Final%20GUI%20Application%20-%20Tkinter/">here</a>.

### System Integration

The following images show some steps of system integration including wiring, assembling, and working of powered-up module.

| ![System Integration Side](Project%20Documents/System%20Integration%20Images/SysInt_All.jpg) | <img src="Project%20Documents/System%20Integration%20Images/SysInt_Wired.jpg" style=" width: 94%;"> |
|:--:|:--:|
| ![System Integration Powered](Project%20Documents/System%20Integration%20Images/SysInt_Device.jpg) | <img src="Project%20Documents/System%20Integration%20Images/SysInt_Wiring.jpg" style=" width: 98%;"> |

### Documents Related to the Project

Detailed documentation of the project can be found using the following links. Feel free to refer them to get a thorough understanding of the project.

<ol>
<li> <a href="Project%20Documents/1_Design_Methodology_Document.pdf">Design Methodology Document</a></li>
<li> <a href="Project%20Documents/2_Comprehensive_Design_Document.pdf">Comprehensive Design Document</a></li>
<li> <a href="Project%20Documents/3_Document_of_Photographs.pdf">Document of Photographs</a></li>
</ol>
