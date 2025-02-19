# 📦 AgentMILO: A Knowledge-Based Conversational Agent for MILP Modeling

![GitHub License](https://img.shields.io/badge/license-MIT-blue.svg)  
AgentMILO is an LLM-powered conversational agent designed to assist non-expert users in modeling Mixed-Integer Linear Programming (MILP) problems. By integrating expert-designed knowledge graphs, AgentMILO helps users define constraints, variables, and objectives, ultimately generating structured MILP formulations.

This repository includes:
- Source Code for developing and running AgentMILO.
- Prompts optimized for MILP modeling.
- Expert-designed Knowledge Graphs for Production Planning (PP) and Traveling Salesman Problem (TSP) variations.
- Tested Problem Instances for benchmarking AgentMILO.
- Generated Conversations & Results comparing AgentMILO with a general LLM agent.
- Complete Experimental Setup for reproducibility.

---

## 📌 Features
✔ Conversational MILP Modeling – Guides users through problem specification.  
✔ Knowledge Graph Integration – Uses structured knowledge for question generation.  
✔ Support for PP & TSP Variations – Pre-built optimization domains.  
✔ AutoGen-based LLM Agent – Utilizes GPT-4o for dynamic conversations.  
✔ Reproducible Experiments – Includes problem instances, model outputs, and evaluation results.  

---

## 🚀 Installation & Setup

### 📂 Clone the Repository
```bash
git clone https://github.com/arc2022-deakin/AgentMILO.git
cd AgentMILO
```
### 📥 Install Dependencies
Ensure you have Python 3.8+ installed, then install the required dependencies:
```bash
pip install -r requirements.txt
```

### ▶️ Run AgentMILO
Since all the code is inside a .ipynb launch Jupyter Notebook or Google Colab open the notebook:
```bash
notebook AgentMILO.ipynb
```
Then, run the notebook cell by cell to interact with AgentMILO.

---

## 🏆 Experiments & Findings

AgentMILO was evaluated against a general LLM agent using:
- 10 distinct user profiles
- PP & TSP problem instances
- Key metrics: clarity, question quality, model accuracy, and ease of interaction

| Metric                        | General LLM (PP) | AgentMILO (PP) | General LLM (TSP) | AgentMILO (TSP) |
|--------------------------------|------------------|----------------|------------------|----------------|
| Clarity & Guidance            | 4.3              | 4.9            | 2.6              | 5.0            |
| Quality of Questions          | 4.8              | 4.9            | 2.7              | 5.0            |
| Summary Comprehensiveness     | 4.9              | 5.0            | 2.9              | 4.9            |
| Ease of Interaction           | 4.9              | 5.0            | 2.9              | 5.0            |
| Overall Satisfaction          | 4.4              | 4.9            | 2.6              | 5.0            |
| Mathematical Model Accuracy   | 3.9              | 4.2            | 3.4              | 4.7            |

---

## 📂 Repository Structure

```plaintext
📦 AgentMILO
├── 📄 AgentMILO.ipynb      # Jupyter Notebook (Code, Prompts, Knowledge Graphs, Conversations, Test Instances)
├── 📄 requirements.txt     # Dependencies
├── 📄 LICENSE              # License information
└── 📄 README.md            # Project documentation

```
---

## 📜 License

This project is licensed under the Apache License 2.0 – See the [LICENSE](LICENSE) file for details.


---

## 🔔 Citation

If you use **AgentMILO** in your research, please cite:

```bibtex
@article{AgentMILO2025,
  author    = {Jyotheesh Gaddam and Vicky Mak-Hau and Bahadorreza Ofoghi and John Yearwood and Diego Molla-Aliod and Lele Zhang},
  title     = {AgentMILO: A Knowledge-Based Framework for Complex MILP Modeling Conversations with LLMs},
  journal   = {ICCAE 2025},
  year      = {2025},
  doi       = {your-doi-here}
}
```

---

## 👥 Authors & Acknowledgments
AgentMILO is developed by:
- Jyotheesh Gaddam (Deakin University) - 📧 j.gaddam@deakin.edu.au
- Vicky Mak-Hau (Deakin University) - 📧 vicky.mak@deakin.edu.au
- Bahadorreza Ofoghi (Deakin University) - 📧 b.ofoghi@deakin.edu.au
- John Yearwood (Deakin University) - 📧 john.yearwood@deakin.edu.au
- Diego Molla-Aliod (Macquarie University) - 📧 diego.molla-aliod@mq.edu.au
- Lele Zhang (The University of Melbourne) - 📧 lele.zhang@unimelb.edu.au

This research is funded by the Australian Research Council (ARC) Discovery Project DP220101925. We also acknowledge Deakin University, Macquarie University, and The University of Melbourne for providing essential resources.

---

## 📬 Contact
For questions or collaboration inquiries, please reach out via Email or open an issue on GitHub.
