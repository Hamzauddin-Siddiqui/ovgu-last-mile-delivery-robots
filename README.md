# Last-Mile Delivery with Autonomous Robots (TBRD)

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Gurobi](https://img.shields.io/badge/Gurobi-10.0+-red.svg)](https://www.gurobi.com/)
[![OVGU](https://img.shields.io/badge/Otto--von--Guericke-University-0066cc.svg)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 🎯 Project Overview

This research tackles the **Truck-Based Robot Delivery (TBRD)** problem - an innovative last-mile delivery system where autonomous robots are launched from trucks to serve customers and return to decentralized depots. The system addresses urban congestion and delivery inefficiencies by combining truck flexibility with robot efficiency.

**Context:** Academic Research | Otto-von-Guericke University | October 2024 - January 2025  
**Role:** Lead Researcher - Mathematical modeling, algorithm development, computational analysis  
**Impact:** Novel heuristic algorithm achieving 290× speedup over exact methods while maintaining solution quality

## 📊 Key Results

| Method | Small Instances (≤8 customers) | Large Instances (≥12 customers) | Avg. Runtime | Best Use Case |
|--------|--------------------------------|----------------------------------|--------------|---------------|
| **Gurobi Optimization** | 98% optimal solutions | 53% optimal solutions | 6.5 seconds | Exact solutions, proof of concept |
| **Heuristic Algorithm** | 34% optimal solutions | Practical feasibility | 0.775 seconds | Large-scale, time-critical deployment |

**Critical Performance Insights:**
- 🎯 **Robot Speed Threshold:** 5→6 km/h improvement yields 75% performance gain
- 📈 **Depot Optimization:** Diminishing returns beyond 5 depots per 4 km² area  
- ⚡ **Scalability:** Heuristic enables real-world deployment scenarios

## 🛠 Technical Stack

**Core Technologies:**
- **Programming:** Python 3.8+, Jupyter Notebooks
- **Optimization:** Gurobi Optimizer 10.0+, Mixed-Integer Programming
- **Analytics:** NumPy, Pandas, SciPy
- **Visualization:** Matplotlib, Seaborn

**Mathematical Methods:**
- **Optimization:** Linear programming, constraint programming, branch-and-bound
- **Heuristics:** Local search, neighborhood operations, parallel processing
- **Operations Research:** Vehicle routing, scheduling optimization, computational complexity analysis

## 📁 Repository Structure

```
├── src/                           # Source code implementations
│   ├── tbrd_gurobi.py            # Mathematical optimization model
│   ├── tbrd_heuristic.py         # Multi-phase heuristic algorithm
│   ├── instance_generator.py     # Test case generation system
│   └── performance_analyzer.py   # Computational study framework
├── data/                          # Datasets and instances
│   ├── sample_instances/          # Generated test problems
│   ├── benchmark_data/            # Computational study datasets
│   └── parameter_sets/            # Algorithm configuration files
├── docs/                          # Research documentation
│   ├── seminar_paper.pdf          # Complete academic paper (23 pages)
│   ├── presentation.pdf           # Conference-style presentation
│   ├── problem_description.pdf    # Initial research proposal
│   └── boysen_2018_reference.pdf  # Base literature (Boysen et al.)
├── results/                       # Computational outputs
│   ├── performance_comparison/    # Gurobi vs. Heuristic analysis
│   ├── sensitivity_analysis/      # Parameter impact studies
│   ├── scalability_study/         # Large instance performance
│   └── visualization/             # Charts and solution plots
├── notebooks/                     # Interactive analysis
│   ├── algorithm_development.ipynb    # Model building process
│   ├── computational_experiments.ipynb # Performance evaluation
│   ├── sensitivity_analysis.ipynb     # Parameter optimization
│   └── results_visualization.ipynb    # Chart generation
└── requirements.txt               # Python dependencies
```

## 🚀 Key Insights

### Methodology
The research combines **exact mathematical optimization** with **practical heuristic approaches** to solve the NP-hard TBRD scheduling problem. The Gurobi implementation provides optimal benchmarks for small instances, while the custom heuristic algorithm enables real-world scalability through local search with adaptive neighborhood operations.

### Implementation
**Mathematical Model:** Mixed-integer programming formulation with truck routing, robot assignment, and timing constraints. **Heuristic Algorithm:** Multi-phase local search using four neighborhood operations (N1-N4) with parallel processing and adaptive termination criteria.

### Results & Impact
The heuristic algorithm demonstrates **practical feasibility** for urban logistics deployment. While achieving 34% optimality rate on large instances, it delivers solutions **290× faster** than exact methods, enabling real-time operational decision-making essential for dynamic delivery environments.

## 📈 Research Contribution

**Literature Gap:** Previous TBRD research (Boysen et al., 2018) focused primarily on exact methods, limiting applicability to small-scale problems.

**Novel Approach:** First implementation combining mathematical rigor with scalable heuristics, featuring:
- Adaptive neighborhood selection with performance-based termination
- Parallel instance processing for statistical validation  
- Comprehensive parameter sensitivity analysis

**Validation:** Extensive computational study across 16 parameter combinations (25 instances each) demonstrates algorithm robustness and identifies critical performance thresholds.

**Future Work:** Integration with dynamic traffic data, multi-truck coordination, and real-world infrastructure constraints.

## 🔮 Extensions & Applications

**Immediate Applications:**
- E-commerce last-mile delivery (Amazon, HelloFresh)
- Urban package distribution networks
- Emergency medical supply delivery

**Research Extensions:**
- Dynamic robot availability during peak periods
- Multi-objective optimization (cost, time, sustainability)
- Integration with smart city infrastructure

**Industry Impact:**
- Scalable solution for logistics companies
- Framework for autonomous delivery startups
- Policy support for urban delivery regulation

## 👨‍💼 About This Project

**Hamzauddin Siddiqui**  
MSc Operations Research & Business Analytics | Otto-von-Guericke University  
*Specialization: Logistics optimization, supply chain analytics, mathematical modeling*

*Currently: Data Analyst at Bettermile (GLS eCom Lab) - applying optimization research to real-world logistics challenges*

## 📚 References

**Primary Literature:**
- Boysen, N., Briskorn, D., & Tschöke, M. (2018). Truck-based robot deliveries with handover. *European Journal of Operational Research*, 271(3), 1085-1099.

**Technical References:**
- Gurobi Optimization, LLC (2023). Gurobi Optimizer Reference Manual.
- Complete bibliography available in [research paper](docs/seminar_paper.pdf)

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

*This project demonstrates advanced operations research methodologies in urban logistics, combining theoretical mathematical optimization with practical algorithmic solutions to address real-world delivery challenges in smart cities.*
