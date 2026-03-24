# URDF Optimization Pipeline

A standardized pipeline for converting **raw CAD exports** into
**ROS-ready robot description packages**.

This repository demonstrates the workflow from **industrial CAD models →
optimized meshes → clean URDF packages**, including:

- mesh decimation
- normal repair
- collision geometry generation
- URDF restructuring
- ROS package preparation

The resulting robot models are lightweight and ready for use in robotics
tools such as:

- RViz
- Gazebo
- MoveIt
- IsaacSim

---

## Robots Included

| Robot      | Manufacturer | DOF | Source CAD                         |
|------------|--------------|-----|------------------------------------|
| AR1440     | Yaskawa      | 6   | `GP12_AR1440.STEP`                 |
| HC10DTP    | Yaskawa      | 6   | `HC10DTP-B00_range.stp`            |
| IRB-5720   | ABB          | 6   | `IRB5720_180kg-260_OC_02_ASM.step` |
| KUKA IIWA  | KUKA         | 7   | sourced from official package      |

---

## Repository Structure

```
urdf_optimization/
├── AR1440/
│   ├── original_cad_file/       # Manufacturer STEP CAD model
│   ├── unoptimized_urdf/        # Raw CAD export with heavy meshes
│   └── optimized_urdf/
│       └── ar1440_description/  # ROS robot description package
│           ├── meshes/
│           │   ├── collision/   # simplified collision meshes
│           │   └── visual/      # optimized visual meshes
│           ├── urdf/            # robot URDF files
│           ├── launch/          # display.launch.py
│           └── config/          # RViz configuration
│
├── HC10DTP/                     # Same structure
├── IRB-5720/                    # Same structure
├── KUKA-IIWA/                   # 7-DOF robot
└── README.md
```

---

## Optimization Pipeline

The following steps were applied to convert CAD models into efficient
robot description packages.

```
STEP CAD
   ↓
Mesh Export (DAE)
   ↓
Mesh Cleaning
   - normal repair
   - duplicate removal
   - scaling corrections
   ↓
Mesh Decimation
   - reduce polygon count
   ↓
Collision Geometry Generation
   ↓
URDF Cleanup
   - consistent link naming
   - separated visual/collision meshes
   ↓
ROS Description Package
```

---

## Mesh Organization

Each robot package follows the standard ROS robot description layout:

```
meshes/
 ├── visual/       # high quality meshes for visualization
 └── collision/    # simplified meshes for physics
```

| Mesh Type | Purpose  | Format |
|-----------|----------|--------|
| Visual    | Rendering | `.dae` |
| Collision | Physics   | `.stl` |

Collision meshes are simplified to improve simulation performance.

---

## ROS Usage

Build the workspace:

```bash
colcon build
source install/setup.bash
```

Launch a robot model in RViz:

```bash
ros2 launch ar1440_description display.launch.py
ros2 launch hc10_description display.launch.py
ros2 launch kuka_iiwa_description display.launch.py
ros2 launch irb_description display.launch.py
```


The launch file starts:

- robot_state_publisher
- joint_state_publisher_gui
- RViz

This allows interactive visualization and joint manipulation.

---

## Purpose

The project focuses on optimizing raw CAD-based robot models into **efficient ROS-compatible URDF packages** by improving mesh structure, reducing polygon count, and generating lightweight collision geometries.

It was also created to **showcase my skills in robot model optimization**, including:

- CAD-to-URDF conversion
- mesh decimation and cleaning
- collision mesh generation
- ROS robot description package design
- simulation-ready model preparation

The optimized models can be used for:

- robot visualization
- motion planning
- simulation
- robotics research pipelines

---
## 📸 Gallery

<div align="center">

| AR1440 | HC10DTP |
|:-:|:-:|
| ![ar1440](https://github.com/user-attachments/assets/aef01611-3f4d-450a-b539-3f6b1ba52c6d) | ![hc10dtp](https://github.com/user-attachments/assets/dd4af00a-3e8d-4e7c-a134-7c5d580e141b) |

| IRB-5720 | KUKA IIWA|
|:-:|:-:|
| ![irb1440](https://github.com/user-attachments/assets/f7070e00-396c-4c26-96d4-45eea8033aa4) | ![iiwa](https://github.com/user-attachments/assets/56a8ea1b-e843-4ad6-9a2e-66fd26833575) |


</div>

---

## License

CAD models belong to their respective manufacturers.

This repository contains **processed meshes and URDF structures for
educational and research use only**.
