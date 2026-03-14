# Yaskawa AR1440 URDF Optimization

This package contains an **optimized ROS robot description** for the
**Yaskawa AR1440 industrial manipulator**.

The robot model was generated from the original **manufacturer CAD
model** and processed through a mesh optimization pipeline to produce
**lightweight meshes suitable for robotics simulation and motion
planning**.

---

# Robot Overview


| Property | Value |
|----------|------|
| Robot | Yaskawa AR1440 |
| Degrees of Freedom | 6 |
| CAD Source | `GP12_AR1440.STEP` |
| CAD File Size | 37 MB |
| ROS Package | `ar1440_description` |

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
| Base | `Base_link_1.dae` | 7.8 MB |
| Link 1 | `link_1_1.dae` | 5.1 MB |
| Link 2 | `link_2_1.dae` | 3.0 MB |
| Link 3 | `link_3_1.dae` | 5.7 MB |
| Link 4 | `link_4_1.dae` | 3.7 MB |
| Link 5 | `link_5_1.dae` | 7.7 MB |
| Link 6 | `link_6_1.dae` | 192 KB |

Total mesh size ≈ **33 MB**

---

## Optimized Visual Meshes


| Link | File | Size |
|------|------|------|
| Base | `base_link_visual.dae` | 164 KB |
| Link 1 | `link_1_visual.dae` | 228 KB |
| Link 2 | `link_2_visual.dae` | 204 KB |
| Link 3 | `link_3_visual.dae` | 376 KB |
| Link 4 | `link_4_visual.dae` | 232 KB |
| Link 5 | `link_5_visual.dae` | 420 KB |
| Link 6 | `link_6_visual.dae` | 164 KB |

Total ≈ **1.8 MB**

---

## Collision Meshes


| Link | File | Size |
|------|------|------|
| Base | `base_link_collision.stl` | 8 KB |
| Link 1 | `link_1_collision.stl` | 8 KB |
| Link 2 | `link_2_collision.stl` | 8 KB |
| Link 3 | `link_3_collision.stl` | 12 KB |
| Link 4 | `link_4_collision.stl` | 16 KB |
| Link 5 | `link_5_collision.stl` | 12 KB |
| Link 6 | `link_6_collision.stl` | 12 KB |

Total ≈ **76 KB**

---
## Optimization Metrics


|Mesh Type                       |Unoptimized  | Optimized   | Reduction
|------------------------------- |------------- |------------ |-----------|
|Visual Mesh Triangles           |508,360       |23,946      | \~95.3%|
|Collision Mesh Triangles      |508,360       |1,270       | \~99.75%|
|**Total Optimized Triangles**   |508,360       |**25,216** |  \~95%|


- The mesh optimization reduced **visual mesh complexity by \~95.3%** and **collision mesh complexity by \~99.75%**, significantly   improving performance for robotics simulation and motion planning.

# Optimization Summary

| Stage | Size |
|------|------|
| Original CAD | 37 MB |
| Raw Mesh Export | ~33 MB |
| Final Robot Model (Visual + Collision) | **~1.9 MB** |
| **Reduction** | **~94% smaller** |


This results in **over 94% reduction in mesh size compared to the raw Mesh export**, making the robot model suitable for:
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

The CAD model belongs to **Yaskawa Electric Corporation**.

This repository only contains **processed meshes and URDF structures for research and educational purposes**.
