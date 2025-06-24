# FPGA-Based-Smart-Car-Security-System
![Project Status](https://img.shields.io/badge/status-Completed-brightgreen.svg)
![Platform](https://img.shields.io/badge/platform-FPGA-blue.svg)
![Tool-Vivado](https://img.shields.io/badge/tool-Vivado-ff69b4.svg)
![Tool-Quartus](https://img.shields.io/badge/tool-Quartus-9cf.svg)
![Simulator](https://img.shields.io/badge/simulation-ModelSim-yellow.svg)
![Language-Verilog](https://img.shields.io/badge/language-Verilog-blue.svg)
![Language-SystemVerilog](https://img.shields.io/badge/language-SystemVerilog-purple.svg)

---
A concealed and reprogrammable smart anti-theft system designed using Verilog HDL and system verilog for high-end vehicles such as Porsche. This project enhances security by detecting unauthorized access, activating an audible alarm, and securely disabling the fuel pump unless the correct hidden owner-authenticated sequence is performed. 

![Overview](https://github.com/user-attachments/assets/816f66b0-ebda-4f4c-8c5c-d8bd88b1f953)

## Overview
![Requirements](https://github.com/user-attachments/assets/05d98c02-13f2-4dd2-b8a9-c99020dce5f6)

---
## How the System Works 
Think of the system like a guard dog that:
o	Sleeps quietly until you leave the house.
o	Starts watching when the house is empty. 
o	If someone opens the door, it gives them a few seconds — if they don’t prove they belong, it starts barking (alarm).
o	And secretly, it locks the fuel line so even if the thief stops the barking, the car won’t move.

---

## Major Features

![Features](https://github.com/user-attachments/assets/08a4c65b-4b0b-421e-913d-a95b4a74900d)

---
## System Diagram

![System Diagram](https://github.com/user-attachments/assets/a9d8ab87-3d3f-4e11-93dd-da52cccc5eb8)

---

## Block Diagram

![Block Diagram](https://github.com/user-attachments/assets/a5fed45a-767d-456a-9b54-c06c48a949d0)

---

## FSM Diagram

![FSM 1](https://github.com/user-attachments/assets/9ef9ec2d-25ab-4e28-b11f-5a8acdf068b6)
![FSM 2](https://github.com/user-attachments/assets/531ca61f-ab6d-437d-88b2-84e6d049efc8)

---

## ⏱️ Timing Parameters

![Timing Parameters](https://github.com/user-attachments/assets/0e84c2cc-1158-4d03-9f83-7284642f4f3a)

These values are stored in memory and can be reprogrammed at runtime.

---

## Tools and Technologies

- **HDL**: Verilog / SystemVerilog
- **Simulation Tool**: ModelSim-Altera Edition
- **Synthesis Tool**: Quartus / Vivado
- **Waveform Viewer**: GTKWave
- **Editor**: Visual Studio Code (VS Code)
- **Version Control**: Git
- **Target FPGA Board**: DE1-SoC (Intel/Altera)

---

## Modules Hierarchy
![Module Names](https://github.com/user-attachments/assets/f0a6fe07-a957-4747-ae7e-2660534f0b48)

---
## RTL Design and Simulation of Testbenches
## Car Anti Theft Alarm System (main module)
![main module](https://github.com/user-attachments/assets/572e3cee-2d6d-436a-81fa-87395789121d)
![Testbench](https://github.com/user-attachments/assets/5673f2d5-7a24-4f29-8798-341f29c60993)

## Anti-Theft FSM
![Anti Theft FSM](https://github.com/user-attachments/assets/ad84820e-78d6-4333-9d7e-b265d9e8b42f)

## Fuel Pump Logic
![Fuel Pump Logic](https://github.com/user-attachments/assets/e9a33914-d97a-4afa-af29-a2e2ce4c9df5)
![Testbench](https://github.com/user-attachments/assets/8e62e9b8-6065-4e26-97d0-4425e8d684e5)

## Siren Generator
![Siren Generator](https://github.com/user-attachments/assets/96d5bcd0-8522-45dd-b072-28dd37005abe)
![Testbench](https://github.com/user-attachments/assets/4bcd9ea0-23d9-469d-b700-6a9bc49e283f)

## Time Parameters
![Time Parameters](https://github.com/user-attachments/assets/7e2aeee6-a185-42db-9071-230e1ce97a2f)
![Testbench](https://github.com/user-attachments/assets/b781a824-084c-4ec6-8298-b4f9f626a801)

## Timer 1Hz
![Timer 1Hz](https://github.com/user-attachments/assets/12f0d55f-ceb1-42c5-85dc-ba6bf004566f)

## Time Parameters With Reprogrammability
![Time Parameters With Reprogrammability](https://github.com/user-attachments/assets/7161ec07-8c3a-4cac-b28f-db104ef76070)
![Testbench](https://github.com/user-attachments/assets/81136a20-9d49-41a1-9019-a54c0950011d)

## Debouncer
![Debouncer](https://github.com/user-attachments/assets/56f276f6-c0e2-46bb-a01e-d7ff7a6961fe)

## Simulation Checklist

- [x] **FSM Behavior**: Verified transitions between all states (Armed, Triggered, Alarm, Disarmed)
- [x] **Timer Accuracy**: All time intervals matched expected durations
- [x] **Siren Modulation**: Alternating 440Hz and 880Hz tones confirmed
- [x] **Fuel Pump Lock**: Disarm sequence required to restore pump power
- [x] **LED Indicator**: Correct status signal behavior (blinking, solid, off)
- [x] **Debouncer**: Inputs free from glitches or spurious toggles
- [x] **Time Reprogrammability**: Parameters updated and reflected immediately
- [x] **Testbenches**: Each module tested independently in ModelSim Altera

---

## Results

Below are key results verified from simulations and waveform analyses:

- ✅ **Auto-Arming Delay**: System enters Armed state exactly **6 seconds** after ignition off and all doors closed.
- ✅ **Driver Door Trigger**: Countdown of **8 seconds** starts upon driver door open. LED solid during countdown.
- ✅ **Siren Behavior**: Siren asserts if countdown expires, alternating tones confirmed via waveform.
- ✅ **Fuel Pump Safety**: Fuel pump remains OFF until **brake + hidden switch** are pressed under ignition.
- ✅ **Parameter Update**: New values loaded during reprogramming reflected instantly in next FSM cycle.
- ✅ **No Metastability**: Debouncer module ensures all transitions are clean and glitch-free.
- ✅ **FSM Coverage**: All FSM transitions including resets, armed/triggered/alarm/disarm verified.

---

## Real-Life Scenarios
![Case 1](https://github.com/user-attachments/assets/974ac255-71a4-43d1-975b-abe2bd6e4d3c)
![Case 2](https://github.com/user-attachments/assets/d025e84e-cb7a-4a01-9ab6-e5faf6b616ce)

## Future Work
![Future Work](https://github.com/user-attachments/assets/cc221805-1d87-4963-913d-44125f2e213c)

## License

This project is licensed under the MIT License.

---

## Regards
![Regards](https://github.com/user-attachments/assets/92608e0c-3c93-41c8-af62-2d24b6ebf4ca)
