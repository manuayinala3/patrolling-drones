# AI Patrolling Drone (Core + Track S Simulation)

An autonomous AI patrolling drone pipeline featuring real-time detection, object tracking, restricted zone intrusion alerting, run recording, and an analytics dashboard.

## System Components
- **Core Pipeline (Person A)**: Hardware-agnostic computer vision detection (YOLO), ByteTrack object tracking, spatial zone alerting, SQLite telemetry storage, and video dashboard.
- **Track S Simulation (Person B)**: PX4 SITL + Gazebo simulation environment and local HTTP camera bridge.

## Project Structure
```
drone-patrol/
├── apps/               # Entrypoint scripts (run_pipeline, dashboard, verify_run, etc.)
├── config/             # Configuration YAML files (default.yaml, sim.yaml)
├── data/
│   ├── runs/           # Generated run outputs (git-ignored)
│   └── samples/        # Test videos
├── docs/               # Architecture and documentation
├── sim/                # Person B: Gazebo worlds, PX4 mission, camera bridge
├── src/
│   └── patrol/         # Core computer vision and alerting modules
└── tests/              # Unit & integration test suites
```

## Quick Start (Core Pipeline)
1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
2. Run pipeline on a sample video:
   ```bash
   python apps/run_pipeline.py --config config/default.yaml
   ```
3. Launch dashboard:
   ```bash
   python apps/dashboard.py
   ```
