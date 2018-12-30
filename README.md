# Azure Truck IoT


![Image](https://github.com/AzureTruck/IoT/blob/master/Assets/AzureTruckIoT1.jpg?raw=true)

## Project description

Azure Truck project was created to demonstrate how Microsoft technologies can be used together inside the car created by polish Microsoft Most Valuable Professionals. This part of the whole project describes Internet of Things (IoT) part which was created especially for Azure Truck.

## Solution

<p align="center">
  <img src="https://github.com/AzureTruck/IoT/blob/master/Assets/AzureTruckIoT4.png?raw=true" alt="Solution diagram"/>
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

## Microsoft Azure services for IoT

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

Aaa

- Azure IoT Edge module (or modules)

Aaa

- IoT Hub

Aaa

- Azure Container Registry

Aaa
