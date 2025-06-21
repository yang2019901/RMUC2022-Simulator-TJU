# RMUC2022-Simulator-TJU

[![license](https://img.shields.io/badge/license-Mozilla-green)](./LICENSE)

## Introduction

This project is an open-source simulator for the **RMUC2022**, developed in Unity by Yang Ming, a former member of the Algorithm Group in **北洋机甲** team, from July 2022 to June 2023.

**Inspired by:**
*   DJI Referee System Client
*   South China Tiger Simulator 2021

## Features

*   **Supports Single and Multiplayer Modes:** Test locally or play online via LAN or IPv6.
*   **High-Fidelity 3D Models:** Includes high-precision 3D models of all robots from the 2022 season.
*   **Realistic Physics Simulation:** Simulates robot movement, collisions, shooting, and other physical effects.
*   **Consistent UI style:** The UI is designed with reference to the DJI Referee System Client.

## Table of Contents

- [RMUC2022-Simulator-TJU](#rmuc2022-simulator-tju)
  - [Introduction](#introduction)
  - [Features](#features)
  - [Table of Contents](#table-of-contents)
  - [Installation Guide](#installation-guide)
  - [Usage](#usage)
    - [Network Requirements](#network-requirements)
    - [System Requirements](#system-requirements)
    - [Key Bindings](#key-bindings)
  - [Demo](#demo)
    - [User Login Interface](#user-login-interface)
    - [Game Mode Selection](#game-mode-selection)
    - [Robot Selection](#robot-selection)
    - [Battlefield](#battlefield)
  - [Contributing](#contributing)
  - [Code of Conduct](#code-of-conduct)
  - [Versioning](#versioning)
  - [Acknowledgments](#acknowledgments)
  - [Feedback](#feedback)
  - [License](#license)

## Installation Guide

### For General Users

You can download the pre-built executable (`RMUC2022-Simulator-Release.zip`) directly from the **Releases** page of this repository and run it.

### For Developers

1.  **Development Environment:** Unity Editor 2021.3.8f1c1
2.  **Open the Project:** Use Unity Hub "Open" -> Select the parent folder of `Assets/`.
3.  **Compilation:** The first time you open the project, it needs to be compiled, which may take from a few minutes to tens of minutes.
4.  **Scene Files:** There are two scene files for the simulator: `Lobby.unity` for selecting the game mode and `BattleField.unity` for the actual combat. They are located in the `Assets/Scenes/` directory. Double-click to open them in the Unity Editor.
5.  **Build Settings:** `Ctrl+Shift+B` to change build settings (e.g., target platform); `Ctrl+B` to build the project.
6.  **Environment Issues:** Due to differences in development environments, errors are normal. You can search on Google, contact the author, or create an Issue.

## Usage

The simulator supports both single-player and multiplayer modes. In multiplayer, the room creator's computer acts as the server (Server PC), and other players (Client PCs) can join via LAN or IPv6. (If not on the same LAN and without an IPv6 address, you can use methods like NAT traversal).

### Network Requirements

The network bandwidth for both Server PC and Client PCs is recommended to be no less than 1Mb/s. The theoretical network usage is about 10Kb/s to 20Kb/s. Network latency should be as low as possible to ensure consistent robot behavior between the Client and Server PCs. (All simulator data is processed on the Server PC, and all data is based on the results of the Server PC's calculations).

### System Requirements

Currently, the simulator does not use LOD, and the scenes have a high number of triangles, requiring a reasonably powerful CPU and graphics card. An i5-9th gen + GTX 1650 laptop can maintain a stable 90 FPS.

**Log Files:** Logs are cached in the path `.\rmuc_simu_preview_Data\YOUR_LOGS`. Deleting them does not affect the program's operation.

### Key Bindings

After entering the BattleField scene, the key bindings for each robot are as follows:

**Note 1:** Press the **`** key to open the settings menu, select **Quit** to exit the current match and return to the Lobby.

**Note 2:** For the Engineer robot, operations in parentheses are for the claw mode, e.g., **R** key => Extend/retract rescue card; **Left Shift + R** key => Enable/disable claw suction.

| Key | Infantry | Hero | Engineer | Drone |
| :---: | :---: | :---: | :---: | :---: |
| **Esc** | Lock/Unlock Mouse | Lock/Unlock Mouse | Lock/Unlock Mouse | Lock/Unlock Mouse |
| **`** | Open Settings | Open Settings | Open Settings | Open Settings |
| **O** | Open Ammo Refill | Open Ammo Refill | Open Ammo Refill | Open Ammo Refill |
| **W/A/S/D** | Move Forward/Left/Back/Right | Move Forward/Left/Back/Right | Move Forward/Left/Back/Right (Claw Pan) | Move Forward/Left/Back/Right |
| **R** | \ | \ | Extend/Retract Rescue Card (Toggle Claw Suction) | Call Air Support (requires >300 team coins) |
| **C** | Toggle Capacitor | Toggle Capacitor | N/A (Claw Flip Out 90°) | \ |
| **Z** | \ | \ | N/A (Claw Flip In 90°) | \ |
| **X** | Brake | Brake | Brake | \ |
| **E/Q** | \ | \ | Turn Right/Left | Ascend/Descend |
| **Left Shift** | Chassis Spin | Chassis Spin | Hold for Claw Mode | \ |
| **Left Mouse** | Fire Projectile | Fire Projectile | \ | Fire Projectile |
| **Right Mouse** | Armor Aim-Assist (Power Rune Aim-Assist if R is held) | Armor Aim-Assist (Power Rune Aim-Assist if R is held) | \ | Armor Aim-Assist (Power Rune Aim-Assist if R is held) |
| **Mouse Move** | Adjust View | Adjust View | Adjust View | Adjust View |

## Demo

### User Login Interface

Users enter their nickname (Player Name) here. It is recommended to use no more than six half-width characters to ensure it displays correctly. By default, the computer name will be used as the nickname on each launch.

<img src="README.assets\log_in.png" alt="log_in" style="zoom: 67%;" />

### Game Mode Selection

-   **Single Player:** Play offline locally.
-   **Multi Player:** Create or join a multiplayer room.
-   **Back:** Return to the login screen.

<img src="README.assets\select_mode.png" alt="select_mode" style="zoom:67%;" />

### Robot Selection

-   **Start Game:** This button is only visible to the host. Clicking it switches to the `BattleField` scene and starts the game.
-   **Select Robot:** Click the buttons on either side of the robot to select it (Red team on the left, Blue team on the right).
-   **Ready Status:** After a non-host player selects a robot, the button changes to `Cancel Ready` to indicate their ready status to the host. This is only an indicator and does not prevent the host from starting the game.

<img src="README.assets\select_robot.png" alt="select_robot" style="zoom:67%;" />

### Battlefield

The UI simulates the real RoboMaster competition interface, with additional capacitor and experience bars in the lower-left corner for more status information.

<img src="README.assets\in_game1.png" alt="in_game1" style="zoom: 33%;" />

The project uses `WheelCollider` to simulate the physical properties of wheels, realistically reproducing dynamic effects such as rollovers on complex terrain (like slopes).

<img src="README.assets\in_game2.png" alt="in_game2" style="zoom: 33%;" />

## Contributing

We greatly welcome community contributions! Please follow these steps:

1.  Fork the Project.
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`).
3.  Commit your Changes (`git commit -m 'Add some AmazingFeature'`).
4.  Push to the Branch (`git push origin feature/AmazingFeature`).
5.  Open a Pull Request.

## Code of Conduct

To foster an open and welcoming environment, we as contributors and maintainers pledge to make participation in our project and our community a harassment-free experience for everyone, regardless of age, body size, disability, ethnicity, gender identity and expression, level of experience, nationality, personal appearance, race, religion, or sexual identity and orientation.

## Versioning

v1.0.0

## Acknowledgments

*   Thanks to **DJI** for creating the RoboMaster series of competitions. Its competition mechanism is novel and challenging, and the competition venue is beautiful and full of technology. The UI and CG of the simulator's competition venue are made with reference to its style. Without the ingenious design of the DJI competition mechanism, the simulator would not have been possible.
*   Thanks to the **华南虎** team for releasing their simulator in 2021. It was the first super confrontation simulator I came into contact with, and it also gave me the idea of developing a simulator from scratch. Without their pioneering ideas, I would not have had the desire and action to build a simulator.
*   Thanks to every member of the **北洋机甲** team. They selflessly provided high-precision 3D models of all robots for the 2022 season, which made an important contribution to improving the visual fidelity and physical realism of the simulator.
*   Special thanks to my roommates **Zhang Chenrui** and **Cao Hongyu**. They actively participated in the testing of the simulator's network connection, multiplayer confrontation, etc. during the development and pre-release process, and provided a lot of valuable opinions on control logic simulation, triangle optimization, etc., which directly promoted the iterative optimization of the simulator.

## Feedback

If you have any questions, comments, or suggestions, including but not limited to mechanism bugs, model clipping, counter-intuitive controls, UI beautification, etc., please feel free to contact the author.
*   **QQ:** 1308592371
*   **Email:** mingyang2601@outlook.com

Enjoy it!

## License

This project is licensed under the Mozilla Public License 2.0.
