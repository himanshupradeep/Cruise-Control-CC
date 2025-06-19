# Cruise Control System (CANoe Simulation)

## Description  
A CAN-based ECU simulation for Cruise Control with Engine, Brakes, and HMI ECUs. Includes 4 phases: simulation, DBC setup, interactive panel design, and CAPL scripting for real-time behavior. Implements real-world Cruise Control logic including speed thresholds, switch control, and safety overrides to replicate authentic vehicle behaviour. 

![image](https://github.com/user-attachments/assets/d60a7c3f-b94c-4ec6-8b75-e9991a957a7b)

Image Source : https://uchanics.ca/cruise-control-warning-light-service-and-guide-what-is-it-and-what-to-do/

## Project Overview  
The Cruise Control system is designed to maintain a constant vehicle speed without continuous accelerator input. Once the vehicle speed exceeds **30 km/h**, the user can activate CC using the **SET** switch. Speed can be adjusted in **1 km/h increments** using **CC+** or **CC–**. The system deactivates automatically when the **Cancel** switch is pressed or if the **brake pedal** is applied. The Cruise Control is limited to a maximum of **120 km/h** and does **not allow activation from standstill**. There is also **no low-speed following functionality** in this configuration.

![image](https://github.com/user-attachments/assets/c7f441ef-86ef-486a-bcfd-85ca705183dc)

Image Source : https://www.researchgate.net/figure/Block-diagram-of-cruise-control-system_fig5_354198908

## Cruise Control Switch Functions  

![image](https://github.com/user-attachments/assets/75665d95-e774-4f8b-b28f-877afb327e5a)

Image Source : https://vehiclefreak.com/is-cruise-control-bad-for-your-car-when-to-use-it/


| Switch        | Function                                                                 |
|---------------|--------------------------------------------------------------------------|
| **SET**       | Activates Cruise Control at the current vehicle speed (≥ 30 km/h).       |
| **CC+**       | Increases the set cruise speed by 1 km/h.                                |
| **CC–**       | Decreases the set cruise speed by 1 km/h.                                |
| **CANCEL**    | Deactivates Cruise Control without erasing the last set speed.           |
| **BRAKE**     | Immediately deactivates Cruise Control and overrides throttle control.   |

## System Behavior Summary  

![ScreenRecording2025-06-19144257-ezgif com-video-to-gif-converter](https://github.com/user-attachments/assets/952a280e-77a7-4d29-9758-e439115d3428)


- **Activation Threshold**: Cruise Control activates only above **30 km/h**.  
- **Speed Range**: Works between **30 km/h and 120 km/h**.  
- **Set Speed Memory**: The last set speed is remembered unless system is reset.  
- **Safety First**: Deactivated by brake or cancel input to ensure driver override.  
- **Simplified Model**: No acceleration from 0 km/h or follow-at-low-speed functionality.

## Project Phases  

### 1. Simulation  
![Screenshot 2025-06-19 144400](https://github.com/user-attachments/assets/1246cd08-54b6-4ba2-8bba-6befd16256e4)
![Screenshot 2025-06-19 144409](https://github.com/user-attachments/assets/b4ca0c96-d3d6-4b0d-848a-9c8977413c24)


- Create network nodes for **Engine**, **CC**, **Brake**, and **HMI ECUs**.  
- Load the necessary **DBC file** to link message signals to network interactions.  
- Set up system timing and connection routing to emulate a live CAN environment.  

### 2. Database Creation  
![Screenshot 2025-06-19 145251](https://github.com/user-attachments/assets/00d80fd8-e2c8-44aa-a629-126bad192b1a)


- Construct a new **DBC** including:  
  - Network nodes and message frames  
  - Signal definitions (direction, value range, byte positioning)  
  - Environment variables for driver interactions  
- Define clear rules for transmission and reception of each message across ECUs.  

### 3. Panel Creation  
![Screenshot 2025-06-19 145334](https://github.com/user-attachments/assets/1bf76cf2-9f6f-4b1e-9cfd-b22e2cb4bb9c)

![Screenshot 2025-06-19 145406](https://github.com/user-attachments/assets/6fe98906-0ecd-4718-a7be-9f1bed4ceb3b)


- Build a **GUI panel** that allows the user to:  
  - Simulate pressing switches like **SET**, **CC+**, **CC–**, **Cancel**, and **Brake**  
  - Visualize current speed, set speed, CC state, and switch actions  
  - Monitor system response live during simulation  

### 4. CAPL Scripting  
![Screenshot 2025-06-19 145443](https://github.com/user-attachments/assets/a70041ba-c846-420e-b5b8-5446c46a3fde)

- Use **CAPL (CANoe Programming Language)** to:  
  - Define environment and global variables for system behavior  
  - Map user inputs to specific logic blocks based on CC rules  
  - Simulate physical responses (e.g., throttle hold, CC state transitions)  
  - Broadcast computed signals onto the **CAN data bus**

## How to Run  
1. Launch **Vector CANoe** with required license/module support.  
2. Open the project files and DBC.  
3. Start simulation and test CC functionality through the panel.  
4. Validate system behavior in response to speed, inputs, and safety conditions.


## License  
This project is open for educational use and learning purposes. Feel free to fork, modify, or contribute!
