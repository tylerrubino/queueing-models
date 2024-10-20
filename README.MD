# Queueing Models Simulations (OOP Design with Visualizations)

This repository contains the simulation of the **M/M/1** queueing model, implemented using **Object-Oriented Programming (OOP)** principles in Java. The project includes visualizations for queue metrics using both **JFreeChart** in Java and **Matplotlib** in Python. Future models like **M/M/K**, **G/G/1**, and **G/G/K** are currently under development.

## Table of Contents

-[Introduction](#introduction) -[Object-Oriented Design](#object-oriented-design) -[Class Structure](#class-structure) -[M/M/1 Queue Model](#mm1-queue-model) -[Visualization Options](#visualizations-options) -[Method 1: JFreeChart (Java)](#method-1-jfreechart-java) -[Method 2: CSV Export and Matplotlib (Python)](#method-2-csv-export-and-matplotlib-python) -[How to Run the Simulation](#how-to-run-the-simulation) -[Running with User Input](#running-with-user-input) -[Project Structure](#project-structure) -[Future Enhancements and Models Under Development](#future-enhancements-and-models-under-development) -[License](#license)

## Introduction

Queueing theory models how tasks (or customers) move through a system with **arrival rates**, **Service rates**, and a limited number of servers. These models are crucial for understanding and optimizing performance in various industries, such as telecommunications, cloud computing, and manufacturing.

This repository focuses on the **M/M/1**, **M/M/K**, **G/G/1**, and **G/G/K** queueing models and uses **Object-Oriented Programming (OOP)** to promote modularity, flexibility, and scalability. The project currently only implements the **M/M/1** model and supports two visualization methods: in-app **JFreeChart** for real-time Java visualizations and **CSV export** for external plotting with **Python/Matplotlib**.

## Object-Oriented Design

### Class Structure

1. **Tasks**: Represents a job or customer in the queue. Each task has attrivutes such as arrival time.
2. **TaskQueue**: Represents a First-In-First-Out (FIFO) queue of tasks.
3. **Server**: Simulates a server that processes tasks.
4. **QueueModel** (Abstract Class): A base class that provides common functionality (e.g., arrival and service events) across different queueing models.
5. **MM1Queue**: Implements the **M/M/1** queueing model by inherting from `QueueModel`.
6. **Visualization**: A class responsible for creating visualizations using **JFreeChart**.
7. **MetricsExporter**: A utility class that exports simulation data to **CSV** for external processing.

This design allows for easy extension and modification, as future queue models can be added by simply creating new classes that extend `QueueModel`.

## M/M/1 Queue Model

### Description:

- The **M/M/1** queueing model represents a single-server system where:
  - **M**: Arrivals follow a Poisson process (constant arrival rate, λ).
  - **M**: Service times follow an exponential distribution (constant service rate, μ).
  - **1**: There is a single server handling tasks.

### Key Metrics:

- **Queue Length**: The number of tasks waiting to be processed over time.
- **Average Waiting Time**: The average time tasks spend waiting and being processed.
- **Server Utilization**: The fraction of time the server is busy.

The simulation collects these metrics and allows users to visualize the data using **JFreeChart** (Java) or export it to **CSV** for external analysis with **Python/Matplotlib**

## Visualization Optons

This project offers two methods for visualizing queue metrics:

### Method 1: JFreeChart (Java)

**JFreeChart** is a Java library that allows in-app visualizations of metrics such as queue length over time. This method is integrated directly into the simulation and provides an interactive way to view results within the Java application.

#### Steps to Use JFreeChart Visualization:

1. During the simulation, queue metrics such as **queue length** and **waiting time** are recorded.
2. The data is passed to the **Visualization** class, which uses JFreeChart to create a real-time plot.
3. The chart is displayed in a Swing window after the simulation completes.

#### Example Chart:

- Queue Length Over Time
- Waiting Time Distribution

### Method 2: CSV Export and Matplotlib (Python)

In addition to in-app visualizations, you can export the simulation data (e.g., queue length, waiting time) to a **CSV** file. Once exported, you can use **Python** and **Matplotlib** to generated detailed plots externally.

#### Steps to Use CSV Export and Python Visualization:

1. Run the simulation and collect metrics like queue length and wait time.
2. The data is exported to a **CSV** file using the `MetricsExporter` Class.
3. Use the provided **Python** script to generate plots from the CSV file.

#### Python Script Example:

```python
import pandas as pd
import matplotlib.pyplot as plt

# Load the CSV data
data = pd.read_csv("mm1_simulation.csv")

# Plot Queue Length over Time
plt.plot(data['Time'], data['QueueLength'])
plt.xlabel('Time')
plt.ylabel('Queue Length')
plt.title('Queue Length over Time')
plt.show()
```

## How to Run the Simulation

The current implementation supports the **M/M/1** queueing model. Future versions will include additional models (e.g., M/M/K, G/G/1, G/G/K).

### Running with User Input

1. **Compile the Simulation Class**:

```bash
javac src/Simulation.java
```

2. **Run the Simulation Program**:

```bash
java src/Simulation
```

3. **Follow the Prompts**:

- Enter the arrival rate (λ), service rate (μ), and total simulation time when prompted.
- Choose whether you want to:
  - 1. for **JFreeChart** visualization (Java), or
  - 2. for **CSV export** for Python/Matplotlib visualization.

4. **View the Results**:

- The program will either display the **JFreeChart visualization** or export the data to a **CSV file** based on the user's selection.

## Project Structure

```bash
queueing-models/
├── src/
│   ├── core/
│   │   ├── Task.java             # Class representing a task
│   │   ├── TaskQueue.java        # FIFO queue for tasks
│   │   ├── Server.java           # Server class for processing tasks
│   ├── models/
│   │   ├── QueueModel.java       # Base class for all queueing models
│   │   ├── MM1Queue.java         # M/M/1 queue simulation class
│   └── utils/
│       ├── Visualization.java    # Class for plotting with JFreeChart
│       ├── MetricsExporter.java  # Utility for exporting data to CSV
│   └── Simulation.java           # Entry point for running simulations
└── README.md
```

### Explanation

- **core/**: Contains the common classes such as **Task, TaskQueue** and **Server**, which are reused across different queueing models.
- **models/**: Contains the **M/M/1** queue model. Future models (M/M/K, G/G/1, G/G/K) will be added here as they are developed.
- **utils/**: Contains utility classes for visualizing metrics and exporting data.

## Future Enhancements and Models Under Development

While the **M/M/1** model is fully implemented, the following models are under development:

- **M/M/K**: Multi-server system with Poisson arrivals and exponential service times.
- **G/G/1**: General arrival and service time distributions with a single server.
- **G/G/K**: General arrival and service time distributions with multiple servers.

Planned enhancements include:

- **Real-Time Visualization**: Implement real-time plotting during the simulation to show how metrics change dynamically.
- **Additional Metrics**: Track and visualize server utilization and task throughput in future versions.

## License

License coming soon.

## Contributions

Contributions, issues, and feature requests are welcome! Feel free to fork the project and submit pull requests to enhance the simulations or add new models.
