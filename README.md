# SamadhiSense: Real-Time Automotive Awareness System

## Overview

**SamadhiSense** is a conceptual project designed to demonstrate a crucial aspect of modern Advanced Driver-Assistance Systems (ADAS): the real-time acquisition, processing, and high-performance computing (HPC) analysis of critical vehicle data. Inspired by the Buddhist concept of *Samadhi*—a state of focused and clear concentration—this system aims to achieve heightened environmental awareness for an ADAS, enabling precise and timely guidance.

This project simulates the journey of vital sensor data, specifically **wheel speed** and **light intensity**, from their origin through a **CAN bus**, a **CAN-to-Ethernet gateway**, and finally to a powerful **High-Performance Computing (HPC)** unit. The HPC then leverages this focused feedback to inform and guide the ADAS.

## Project Goal

The primary goal of SamadhiSense is to illustrate the robust real-time capabilities of FreeRTOS in handling concurrent tasks, inter-process communication, and external hardware interfaces within an automotive context. It highlights how low-latency data flow from vehicle sensors can power sophisticated ADAS decision-making on a remote, powerful computing platform.

## Key Components & Technologies

* **Simulated Wheel Speed Sensor:** Provides real-time data on vehicle velocity.
* **Simulated Light Sensor:** Offers input on ambient light conditions.
* **CAN Bus (Simulated):** The primary in-vehicle network for transmitting sensor data.
* **CAN-to-Ethernet Gateway (FreeRTOS-powered):**
    * Acts as the bridge between the vehicle's internal CAN network and the external Ethernet network.
    * Leverages **FreeRTOS** for concurrent handling of CAN message reception, data encapsulation, and Ethernet transmission.
    * Ensures reliable and low-latency data forwarding.
* **Ethernet Network:** Carries sensor data from the gateway to the HPC.
* **High-Performance Computing (HPC) Unit (Simulated/Conceptual):**
    * Represents a powerful external processor (e.g., a server or dedicated compute cluster).
    * Receives sensor data from the Ethernet gateway.
    * Performs complex algorithms and decision-making for the ADAS, utilizing the real-time feedback.
* **ADAS System (Conceptual Guidance):** The ultimate beneficiary of the HPC's insights, using the processed data to guide vehicle behavior (e.g., adaptive lighting adjustments, traction control interventions, or enhanced situational awareness for higher-level autonomous functions).

## FreeRTOS Utilization

FreeRTOS is central to the **CAN-to-Ethernet Gateway** component, demonstrating its strength in:

* **Task Management:** Separate tasks for CAN reception, data processing, and Ethernet transmission ensure smooth, concurrent operation.
* **Inter-Task Communication:** Queues and semaphores will be used to safely pass sensor data and control signals between tasks.
* **Real-time Performance:** Prioritization of critical data forwarding tasks to minimize latency, crucial for ADAS responsiveness.
* **Network Stack Integration:** Managing the Ethernet interface and communication protocols within a constrained embedded environment.

## How it Works (Conceptual Flow)

1.  **Sensor Data Generation:** Simulated wheel speed and light sensor data are generated on a microcontroller representing an ECU.
2.  **CAN Bus Transmission:** This data is formatted into CAN messages and "transmitted" onto a simulated CAN bus.
3.  **Gateway Reception:** The FreeRTOS-powered CAN-to-Ethernet gateway receives these CAN messages.
4.  **Data Processing & Encapsulation:** Within the gateway, FreeRTOS tasks process the raw CAN data, potentially performing initial filtering or aggregation, and then encapsulate it into Ethernet packets.
5.  **Ethernet Transmission:** The gateway transmits these packets over Ethernet to the HPC.
6.  **HPC Analysis & ADAS Guidance:** The HPC receives the data, performs high-level analysis (e.g., determining optimal lighting based on light sensor input, or predicting traction needs from wheel speed data), and then "guides" the ADAS with informed decisions.

## Potential Enhancements & Future Work

* Implement **actual CAN bus communication** with real transceivers.
* Integrate **real sensors** instead of simulations.
* Develop a **basic ADAS response module** on the HPC side (e.g., a Python script that interprets data and prints "ADAS action" suggestions).
* Add **security features** to the Ethernet communication.
* Explore **over-the-air (OTA) updates** for the FreeRTOS gateway firmware.
* Incorporate **additional sensor types** (e.g., simulated radar, camera data) for more complex ADAS scenarios.






