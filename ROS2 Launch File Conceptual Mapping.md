```mermaid
flowchart TD

    subgraph ROS2_Sensors["ROS2 Sensor Nodes"]
        CAM["camera_node"]
        LIDAR["lidar_node"]
        IMU["imu_node"]
        TACT["tactile_node"]
    end

    subgraph ROS2_Perception["ROS2 Perception Node"]
        PER["perception_node"]
    end

    subgraph DAIS10_Nodes["DAIS‑10 Semantic Nodes"]
        SIS10["sis10_node"]
        SIF10["sif10_node"]
        MCM10["mcm10_node"]
        TIER10["tier10_node"]
        SICM10["sicm10_node"]
        DIFS10["difs10_node"]
        QFIM10["qfim10_node"]
        AMD10["amd10_node"]
    end

    subgraph ROS2_Core["ROS2 Core Nodes"]
        FUSION["fusion_node"]
        PLANNER["planner_node"]
        CONTROL["control_node"]
        DIAG["diagnostics_node"]
    end

    CAM --> PER
    LIDAR --> PER
    IMU --> PER
    TACT --> PER

    PER --> SIS10
    SIS10 --> SIF10
    SIF10 --> MCM10
    MCM10 --> TIER10
    TIER10 --> SICM10
    SICM10 --> DIFS10
    DIFS10 --> QFIM10

    QFIM10 --> FUSION
    FUSION --> PLANNER
    PLANNER --> CONTROL

    CONTROL --> AMD10
    AMD10 --> DIAG
````
