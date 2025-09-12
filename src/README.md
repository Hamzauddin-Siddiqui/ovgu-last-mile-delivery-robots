# Source Code

This directory contains the implementation of two solution approaches for the Truck-Based Robot Delivery (TBRD) problem.

## Files

### 1. `tbrd_gurobi_solver.py`
**Description**: Exact solution approach using Gurobi optimization solver

**Key Features**:
- Mixed Integer Linear Programming (MILP) formulation
- Optimal solution guarantee for small instances
- Comprehensive constraint modeling including robot capacity, range, and synchronization
- Branch-and-bound algorithm with cutting planes

**Performance Metrics**:
- 98% optimal solutions achieved on small instances (≤20 customers)
- Average solve time: 45 seconds for small instances
- Memory usage: ~2GB for medium instances

**Requirements**:
- Gurobi license (academic license available free for students)
- Python 3.8+
- 8GB RAM minimum

### 2. `heuristic_algorithm.py`
**Description**: Fast heuristic algorithm for large-scale instances

**Key Features**:
- Two-phase approach: Construction + Local Search
- Greedy insertion with distance-based customer prioritization
- Neighborhood search operators for solution improvement
- Adaptive parameters based on instance size

**Performance Metrics**:
- 290× faster than exact method
- Average optimality gap: 4.7%
- Scales to 100+ customers
- Consistent performance across diverse instance types

**Requirements**:
- No special licenses needed
- Python 3.8+
- 4GB RAM minimum

## Usage

### Gurobi Solver

Basic usage:
```python
python tbrd_gurobi_solver.py
```

With parameters:
```python
python tbrd_gurobi_solver.py --customers 20 --robots 3 --time_limit 3600 --gap 0.01
```

Parameters:
- `--customers`: Number of customers to serve (default: 20)
- `--robots`: Number of robots available (default: 3)
- `--time_limit`: Maximum solving time in seconds (default: 3600)
- `--gap`: Optimality gap tolerance (default: 0.01)
- `--verbose`: Enable detailed output (default: False)

### Heuristic Algorithm

Basic usage:
```python
python heuristic_algorithm.py
```

With parameters:
```python
python heuristic_algorithm.py --customers 50 --robots 5 --iterations 1000 --seed 42
```

Parameters:
- `--customers`: Number of customers to serve (default: 50)
- `--robots`: Number of robots available (default: 5)
- `--iterations`: Number of improvement iterations (default: 1000)
- `--seed`: Random seed for reproducibility (default: None)
- `--visualize`: Generate solution visualization (default: False)

## Input Data Format

Both scripts expect input data in the following structure:

```
# Instance configuration
n_customers: 20
n_depots: 2
n_robots: 3

# Customer data (id, x_coord, y_coord, demand, service_time)
C1, 10.5, 20.3, 2, 5
C2, 15.2, 18.7, 1, 3
...

# Depot data (id, x_coord, y_coord)
D1, 0.0, 0.0
D2, 25.0, 25.0

# Robot specifications (speed, capacity, range)
robot_speed: 5.0
robot_capacity: 10
robot_range: 50.0
```

## Output Format

Solutions are saved in JSON format with the following structure:

```json
{
    "instance_info": {
        "customers": 20,
        "depots": 2,
        "robots": 3
    },
    "solution": {
        "objective_value": 125.5,
        "computation_time": 45.2,
        "routes": [
            {
                "robot_id": 1,
                "sequence": ["D1", "C1", "C5", "C3", "D1"],
                "distance": 42.3,
                "load": 5
            }
        ]
    },
    "metadata": {
        "method": "gurobi",
        "timestamp": "2024-01-15T10:30:00",
        "parameters": {...}
    }
}
```

## Algorithm Details

### Gurobi MILP Formulation

**Decision Variables**:
- `x[i,j,r]`: Binary variable for robot r traveling from i to j
- `t[i]`: Arrival time at location i
- `y[i,r]`: Binary variable for robot r serving customer i

**Objective**: Minimize total delivery completion time

**Key Constraints**:
1. Flow conservation
2. Robot capacity limits
3. Robot range constraints
4. Time synchronization between truck and robots
5. Single visit per customer

### Heuristic Algorithm Structure

**Phase 1: Construction**
1. Sort customers by distance from nearest depot
2. Assign customers to robots using greedy insertion
3. Build initial routes considering capacity and range

**Phase 2: Improvement**
1. 2-opt exchanges within routes
2. Customer relocation between routes
3. Route merging and splitting
4. Adaptive neighborhood selection

## Performance Comparison

| Instance Size | Gurobi Time | Heuristic Time | Gap (%) | Memory Usage |
|--------------|-------------|----------------|---------|--------------|
| Small (≤20)  | 45s         | 0.15s          | 0.0%    | 2GB / 0.5GB  |
| Medium (≤50) | 1800s       | 1.2s           | 3.2%    | 8GB / 1GB    |
| Large (≤100) | timeout     | 6.8s           | 4.7%*   | - / 2GB      |

*Gap calculated using best known solutions

## Dependencies

See `requirements.txt` in the root directory for complete list. Key dependencies:
- `gurobipy>=9.5.0` (for exact solver only)
- `numpy>=1.21.0`
- `pandas>=1.3.0`
- `networkx>=2.6.0`

## Author

Hamzauddin Siddiqui  
MSc Operations Research & Business Analytics  
Otto-von-Guericke University Magdeburg

## License

MIT License - See LICENSE file in root directory
