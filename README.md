# Azure Truck IoT


![Image](https://github.com/AzureTruck/IoT/blob/master/Assets/AzureTruckIoT1.jpg?raw=true)


## Project description

Azure Truck project was created to demonstrate how Microsoft technologies can be used together inside the car created by polish Microsoft Most Valuable Professionals. This part of the whole project describes Internet of Things (IoT) part which was created especially for Azure Truck.


## Solution

<p align="center">
  <img src="https://github.com/AzureTruck/IoT/blob/master/Assets/AzureTruckIoT6.png?raw=true" alt="Solution diagram"/>
</p>

IoT solution for Azure Truck consists of three Raspberry Pi devices connected with the Microsoft Azure Cloud. Each board has some sensors connected:

#### First board has below components:

- HDMI Camera 

- LCD screen 

- Motion detector 

#### Second board has below components:

- RGB color LED 

- Motion detector 

- Temperature and pressure sensors

- Color detector

#### Third board has below components:

- Temperature sensors

All three devices are connected to the Azure cloud services but third one is configured as "Edge" device.


## Microsoft Azure cloud services for IoT

As you can see on the architecture diagram each device is connected with Azure cloud. Below I described each Azure service used in Azure Truck IoT solution.

#### Azure IoT Hub

The Azure IoT Hub provides reliable and secure communication between IoT devices. It also establishes bi-directional communication between each device and the Azure cloud.

#### Azure Storage

Azure Storage was created to store data collected from the sensors (like temperature or pressure). This type of data is stored in the Azure Table Storage. Azure Blob Storage was created to keep images send from the IoT device with motion sensor and a camera.

#### Azure Function for face detection

First Azure Function App was created to use Azure Cognitive Services Face API to detect person from the image uploaded to the Azure Blob Storage. Once there is a new photo uploaded to the Storage, Function App is triggered. Face API is called and result about face detection is retuned through Azure IoT Hub to the IoT device with camera and LCD screen.

#### Azure Function for temperature, pressure, altitude and color data collection

Second Azure Function App was created to collect data from the device where pressure, temperature, altitude and color sensors are connected. Once there is new information sent from the device, Function App is invoked and data is stored in the Azure Table Storage. This is also the main data source for Power BI dashboards.

#### Azure IoT Edge

As mentioned before one of the devices was used as an "Edge" device. In this case we used Azure IoT Edge. Azure IoT Edge enables moving cloud analytics and custom business logic to IoT devices. The device can process logic directly without pushing data to the cloud.
Azure IoT Edge consists of three main components:

- Azure IoT Edge runtime

The runtime enables custom logic and cloud logic on IoT Edge devices. It is located on the IoT Edge device, and executes management and communication operations.

- Azure IoT Edge module (or modules)

IoT Edge modules are units that consist of custom logic (for instance to analyze temperature) or cloud logic (like Azure Functions, Azure Stream Analytics and Azure Machine Learning). In our case there was temperature module writted in Python to detect temperature for the sensor.

- IoT Hub

The Azure IoT Edge runtime connects to Azure IoT Hub to facilitate communication between the Edge device and the cloud.

- Azure Container Registry

Modules are kept as a Docker images in the Azure Container Registry. Azure IoT Edge Runtime can pull images from here and run modules as Docker container.

<p align="center">
  <img src="https://github.com/AzureTruck/IoT/blob/master/Assets/AzureTruckIoT5.png?raw=true" alt="Solution diagram"/>
</p>


## Devices specification

There was three Raspberry Pi2 devices used in the Azure Truck project. Two of them running Windows 10 IoT Core system and on of them ("Edge device") is running Raspian9. For the first two devices there is dedicated Universal Windows Application (UWP) created with IoT extension to provide communication between the app and the device and sensors. "Edge" device with IoT Edge runtime has module written in Python.

Below there is a list of IoT sensors used in this project together with connection schemas.

#### Face detection devices

- HDMI USB Camera
- Motion sensor
- LCD screen

#### Sensors device (temperature, pressure, altitude and color)

- Temperature and pressure sensor
- RGB color detection sensor
- RGB diode


## Project source code

- Azure Truck IoT UWP application source code can be found in our official Github repository [here](https://github.com/AzureTruck/IoT/tree/master/AzureTruckIoT)

- Python module source code for the "Edge" device can be found in in our official Github repository [here](https://github.com/AzureTruck/IoT/tree/master/TemperatureEdgeSolution)
