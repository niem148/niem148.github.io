---
title: Raspberry Pi 5 Portable Machine with UPS and Batteries
date: 2025-11-13 09:42:05 +0000
categories: [raspberrypi, hardware]
tags: [pi5, laptop build, UPS, cooling, display, battery, fusion, 3dprinting, itskills, ups, portablecomputing]     # TAG names should always be lowercase
media_subpath: /assets/media/pi5_laptop/
image: preview.jpg
---

This project showcases my ability to design and build a portable Raspberry (Pi5) machine capable of running entirely off-grid, powered by batteries and an uninterruptible power supply (UPS). The machine is designed to operate without mains power, making it ideal for on-the-go use cases, including AI, media serving, and network-wide ad blocking (Pi-hole). The entire design is self-contained in a custom 3D printed case.

![Pi5 Portable Setup](cooling.jpg)
*The fully assembled Raspberry Pi 5 portable machine.*

## Key Features

- **Portable Power**: Operates entirely off battery power with UPS integration.
- **Custom 3D Printed Case**: Designed and printed in PETG for durability and a sleek finish.
- **Cooling System**: Incorporates active cooling to maintain performance.
- **Modular Design**: Easily upgradeable with access to all ports and expansion capabilities.

## Part List

Here are the key components used in the build:

- **PETG Black Filament** – For the 3D printed case
- **Slim Bluetooth Keyboard** – Compact and wireless
- **GeeekPi 10.1" Touch Screen** – For easy interaction
- **Geekworm UPS X1203** – Uninterruptible power supply
- **Geekwork 18650 Parallel Battery Pack (x2)** – Provides backup power
- **Geekworm Metal Power Switch** – Reliable power control
- **18650 Batteries (x4)** – High-capacity batteries for extended use
- **Type-C Terminal** – For power input
- **JST XH2.54 Connectors** – For wiring and connectors
- **U-Shaped HDMI Mini to HDMI** – For video output
- **USB C to C (x2)** – For data and power transfer
- **USB A to C short cable (Male/Female)** – For additional connectivity
- **DC Extension Lead (short)** – For power management
- **L-Shaped Micro HDMI to HDMI** – For space efficiency

## 3D Modeling in Fusion 360

### Design Process

The case design was created in **Autodesk Fusion 360**. Here’s a step-by-step breakdown of how I approached the modeling:

1. **Measuring the LCD**: Accurate measurements of the GeeekPi 10.1" touch screen were taken to ensure a perfect fit.
2. **Sketching the Design**: I started by sketching a basic layout, incorporating all necessary ports and connectors, including HDMI, USB, and power.
3. **Adding Screw Mounts**: Designed screw mounts to securely fasten the components inside the case.
4. **Snap Fit Vents**: I incorporated snap-fit vents with a hexagonal pattern to enhance airflow and cooling, while maintaining structural integrity.
5. **Flush Kickstand**: A flush kickstand was designed with magnets to keep the case in place and provide an ergonomic viewing angle.

![Fusion 360 Design](cooling.jpg)
*The 3D model in Fusion 360.*

### 3D Printing

The case was 3D printed on a **Bambu A1 printer** using **PETG black filament**. PETG was chosen for its strength and durability, ensuring the case would withstand daily use and provide protection for the internal components.

## Troubleshooting & Iterations

Building this project was not without its challenges. Here’s a list of some key troubleshooting steps:

- **Adjusting Tolerances**: I spent a significant amount of time iterating on the design, adjusting tolerances to ensure a perfect fit for the screen, screws, and vents.
- **Power Issues**: I faced a power issue where the 10-inch LCD would occasionally shut off. This was resolved by utilizing the 5V output on the UPS to reliably power the screen via USB.
- **Connector Modification**: I had to strip down the plastic U-shaped USB and HDMI connectors to bare metal to ensure they fit properly into the case and didn't protrude.
- **Cable Management**: The internal cable management was optimized using loops and zip ties to keep everything neat and organized.
- **Safety Enhancements**: To ensure safety, I used high-temperature hot tape on areas prone to heat buildup, and I added an **Arctic Cooler** to the Pi5 for better cooling during heavy use.

![3D Printed Case](cooling.jpg)
*The 3D printed case, showing the internal layout and cable management.*

## Software & Use Case

### Flashing the Raspberry Pi 5

I used the **Raspberry Pi Imager** to flash the latest **Pi OS** onto the SD card. This enabled a smooth and stable experience for running the device headlessly or with the attached screen.

### Future Plans

The goal is to turn this Pi5 into a multi-functional device:

1. **Pi-hole**: A local DNS server to block ads across the entire network.
2. **AI Projects**: Utilizing the power of the Pi5 for machine learning and AI projects.
3. **Media Server**: Turning it into a local media server for streaming content.

### Next Steps

This is just the beginning of the project. In future posts, I will detail the installation and setup of Pi-hole, AI frameworks, and media server software. Stay tuned!

## AI Assistance
Throughout the project I leveraged Copilot and GPT tools to accelerate problem‑solving and documentation. These tools served as valuable aids, allowing me to iterate quickly and overcome challenges, while still relying on my own technical expertise in IT and 3D design.

They were fundamental in:
- Brainstorming design approaches in Fusion 360
- Troubleshooting power and connector issues
- Drafting clear technical documentation for repeatability

By combining AI assistance with my own IT and 3D design expertise, I delivered a polished, working solution.

## Conclusion

This Raspberry Pi 5 portable machine is a perfect example of how hardware design, 3D modeling, and software skills can be combined to create a powerful, functional, and portable computing solution. The project demonstrates my proficiency in several key areas, including hardware integration, design, troubleshooting, and software implementation. I’m excited to continue working on this project and exploring new use cases for this versatile Raspberry Pi setup.

![Pi5 in Action](cooling.jpg)
*The Raspberry Pi 5 running a media server application.*

---

Feel free to connect with me to discuss this project further or if you’re interested in collaborating on similar endeavors.
