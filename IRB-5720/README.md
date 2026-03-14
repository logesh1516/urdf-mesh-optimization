# ABB IRB-5720 URDF Optimization

This package contains an **optimized ROS robot description** for the
**ABB IRB-5720 industrial manipulator**.

The robot model was generated from the original **manufacturer CAD
model** and processed through a mesh optimization pipeline to produce
**lightweight meshes suitable for robotics simulation and motion
planning**.

---

# Robot Overview


| Property | Value |
|----------|------|
| Robot | ABB IRB-5720 |
| Degrees of Freedom | 6 |
| CAD Source | `IRB5720_180kg-260_OC_02_ASM.step` |
| CAD File Size | 27 MB |
| ROS Package | `irb_description` |

---

# Mesh Optimization Results

The raw CAD meshes were extremely heavy and unsuitable for simulation.

They were optimized through:

- mesh cleanup
- polygon decimation
- visual/collision separation
- URDF restructuring

---

# Mesh Size Comparison

## Unoptimized Meshes (CAD Export)


| Link | File | Size |
|------|------|------|
| Base | `Base_link_1.dae` | 1.2 MB |
| Link 1 | `link_1_1.dae` | 2.1 MB |
| Link 2 | `link_2_1.dae` | 2.2 MB |
| Link 3 | `link_3_1.dae` | 1.3 MB |
| Link 4 | `link_4_1.dae` | 1.2 MB |
| Link 5 | `link_5_1.dae` | 2.0 MB |
| Link 6 | `link_6_1.dae` | 1.1 MB |

Total mesh size ≈ **11.1 MB**

---

## Optimized Visual Meshes


| Link | File | Size |
|------|------|------|
| Base | `base_link_visual.dae` | 260 KB |
| Link 1 | `link_1_visual.dae` | 584 KB |
| Link 2 | `link_2_visual.dae` | 196 KB |
| Link 3 | `link_3_visual.dae` | 520 KB |
| Link 4 | `link_4_visual.dae` | 216 KB |
| Link 5 | `link_5_visual.dae` | 156 KB |
| Link 6 | `link_6_visual.dae` | 84 KB |

Total ≈ **1.97 MB**

---

## Collision Meshes


| Link | File | Size |
|------|------|------|
| Base | `base_link_collision.stl` | 8 KB |
| Link 1 | `link_1_collision.stl` | 8 KB |
| Link 2 | `link_2_collision.stl` | 12 KB |
| Link 3 | `link_3_collision.stl` | 8 KB |
| Link 4 | `link_4_collision.stl` | 8 KB |
| Link 5 | `link_5_collision.stl` | 12 KB |
| Link 6 | `link_6_collision.stl` | 12 KB |

Total ≈ **68 KB**

---
## Optimization Metrics


|Mesh Type                       |Unoptimized  | Optimized   | Reduction
|------------------------------- |------------- |------------ |-----------|
|Visual Mesh Triangles           |170,078       |25,810      | \~84.82%|
|Collision Mesh Triangles      |170,078       |1,152       | \~99.32%|
|**Total Optimized Triangles**   |170,078       |**26,962** |  \~84.13%|


- The mesh optimization reduced **visual mesh complexity by \~84.82%** and **collision mesh complexity by \~99.32%**, significantly improving performance for robotics simulation and motion planning

# Optimization Summary

| Stage | Size |
|------|------|
| Original CAD | 27 MB |
| Raw Mesh Export | ~11.1 MB |
| Final Robot Model (Visual + Collision) | **~2.04 MB** |
| **Reduction** | **~81.6% smaller** |


This results in **over 81.6% reduction in mesh size compared to the raw Mesh export**, making the robot model suitable for:
- real-time visualization
- motion planning
- simulation

---

# Applications

The optimized robot model can be used for:

- robot visualization
- motion planning
- MoveIt integration
- Gazebo simulation
- Isaac Sim simulation
- robotics research

---

# Notes

The CAD model belongs to **ABB Robotics**.

This repository only contains **processed meshes and URDF structures for research and educational purposes**.
