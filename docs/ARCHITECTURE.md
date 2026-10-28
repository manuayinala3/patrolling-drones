# Architecture Overview

## System Architecture

The AI Patrolling Drone system is partitioned into two independent, loosely coupled subsystems:
1. **CORE Pipeline (Person A)**: Hardware-agnostic computer vision, tracking, zone alerting, persistence, and web dashboard.
2. **Track S Simulation (Person B)**: PX4 SITL + Gazebo simulation, autonomous flight missions, and camera bridge.

### Seam / Interface Contract

The CORE pipeline connects to the simulation through an HTTP camera bridge hosted by Person B:
- Endpoint: `http://127.0.0.1:8081/`
  - `GET /frame.jpg`: Current camera image (JPEG bytes).
  - `GET /frame_meta.json`: Current frame metadata (`frame_number`, `t_wall`, `t_sim`, `source_frame_idx`, `width`, `height`).

Person A implements atomic frame fetching with validation and automatic reconnection backoff.

---

*(Track S architecture and simulation documentation will be contributed by Person B)*
