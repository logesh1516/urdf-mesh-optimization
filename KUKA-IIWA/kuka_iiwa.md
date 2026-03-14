# KUKA-IIWA URDF Optimization

This package contains an **optimized ROS robot description** for the
**KUKA-IIWA industrial manipulator**.

The robot model was generated from the original **manufacturer CAD
model** and processed through a mesh optimization pipeline to produce
**lightweight meshes suitable for robotics simulation and motion
planning**.

This is optimization is done to challenge myself in optimizing the already optimized meshes.

---

# Robot Overview


| Property | Value |
|----------|------|
| Robot | KUKA-IIWA |
| Degrees of Freedom | 7 |
| CAD Source | `genesis assets` |
| ROS Package | `kuka_iiwa_description` |

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
| Base | `base_link.dae` | 4.6 MB |
| Link 0 | `link_0.obj` | 184 KB |
| Link 1 | `link_1.obj` | 168 KB |
| Link 2 | `link_2.obj` | 88 KB |
| Link 3 | `link_3.obj` | 116 KB |
| Link 4 | `link_4.obj` | 92 KB |
| Link 5 | `link_5.obj` | 76 KB |
| Link 6 | `link_6.obj` | 68 KB |
| Link 7 | `link_7.obj` | 92 KB |

Total mesh size ≈ **5.46 MB**

---

## Optimized Visual Meshes


| Link | File | Size |
|------|------|------|
| Base | `base_link_visual.dae` | 136 KB |
| Link 1 | `link_1_visual.dae` | 104 KB |
| Link 2 | `link_2_visual.dae` | 60 KB |
| Link 3 | `link_3_visual.dae` | 76 KB |
| Link 4 | `link_4_visual.dae` | 64 KB |
| Link 5 | `link_5_visual.dae` | 56 KB |
| Link 6 | `link_6_visual.dae` | 48 KB |
| Link 7 | `link_7_visual.dae` | 80 KB |

Total ≈ **0.61 MB**

---

## Collision Meshes


| Link | File | Size |
|------|------|------|
| Base | `base_link_collision.stl` | 12 KB |
| Link 1 | `link_1_collision.stl` | 8 KB |
| Link 2 | `link_2_collision.stl` | 4 KB |
| Link 3 | `link_3_collision.stl` | 8 KB |
| Link 4 | `link_4_collision.stl` | 4 KB |
| Link 5 | `link_5_collision.stl` | 4 KB |
| Link 6 | `link_6_collision.stl` | 4 KB |
| Link 7 | `link_7_collision.stl` | 8 KB |

Total ≈ **52 KB**

---
## Optimization Metrics


|Mesh Type                       |Unoptimized   | Optimized   | Reduction
|------------------------------- |------------- |------------ |-----------|
|Visual Mesh Triangles           |14,758        |9,162        | \~37.9%|
|Collision Mesh Triangles        |14,758        |826          | \~94.4%|
|**Total Optimized Triangles**   |14,758        |**9,988**    | \~32.3%|


- The mesh optimization reduced **visual mesh complexity by \~37.9%** and **collision mesh complexity by \~94.4%**, significantly improving performance for robotics simulation and motion planning

# Optimization Summary

| Stage | Size |
|------|------|
| genesis asset size(kuka_iiwa) | ~5.46 MB |
| Final Robot Model (Visual + Collision) | **~0.66 MB** |
| **Reduction** | **~87.9% smaller** |


This results in **over 87.9% reduction in mesh size compared to the already optimized meshes**, making the robot model suitable for:
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

The URDF model belongs to **genesis assets**.

This repository only contains **processed meshes and URDF structures for research and educational purposes**.
