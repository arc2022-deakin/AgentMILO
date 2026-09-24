# 📦 AgentMILO: A Knowledge-Based Conversational Agent for MILP Modeling

![GitHub License](https://img.shields.io/badge/license-Apache%202.0-blue.svg) 

### 📄 Published Paper

**AgentMILO: A Knowledge-Based Framework for Complex MILP Modelling Conversations with LLMs**

Published in the **2025 17th International Conference on Computer and Automation Engineering (ICCAE 2025)**, Perth, Australia.

🔗 **[Read the Published Paper (IEEE Xplore)](https://doi.org/10.1109/ICCAE64891.2025.10980596)**  

📚 **DOI:** [10.1109/ICCAE64891.2025.10980596](https://doi.org/10.1109/ICCAE64891.2025.10980596)

**Authors:** Jyotheesh Gaddam, Lele Zhang, Vicky Mak-Hau, John Yearwood, Bahadorreza Ofoghi, Diego Molla-Aliod

---

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

## 📂 Knowledge Graphs

This repository contains expert-designed knowledge graphs used in the AgentMILO framework for MILP modeling. These graphs provide structured representations of constraints, variables, and objectives to assist in MILP formulation.

#### Kowledge Graph 1: Production Planning: (Prepared by Vicky Mak-Hau)
![Production Planning](https://github.com/user-attachments/assets/560debc4-7fbc-462e-851a-cb710d9045a6)

#### Kowledge Graph 2: Travelling Salesman Problem: (Prepared by Lele Zhang)
![TSP](https://github.com/user-attachments/assets/d5cdb41b-78de-4a5c-9e28-2d2a3c7f2fc0)

---

## 📂 Problem Instances

The tested problem instances used in the AgentMILO framework are stored in the [`Problem Instances/`](Problem%20Instances/) folder.

### 📌 Included Instances & Credits
- [Production Planning (PP) Instance](Problem%20Instances/PP_instance.md) 🏭 - Created by Vicky Mak-Hau  
- [Traveling Salesperson (TSP) Instance](Problem%20Instances/TSP_instance.md) 🛣️ - Created by Lele Zhang  

---
## 🧑‍💻 Auto-Answering Agents Acting as Users  

In this framework, the auto-answering agents are designed to act as different types of users with varying levels of expertise in optimization. These are not real users, but simulated agents following distinct behavior patterns to interact with the system. Each agent mimics a unique interaction style, ensuring diverse testing scenarios.

🔗 Full system prompts for all auto-answering agents are available here:  
👉 [AgentMILO System Auto Answering Agent Prompts](Auto_Answering_Agents_Prompts.txt)  

### 📌 Auto-Answering Agent Profiles  

| Agent (User Type) | Description | Interaction Goals | Example Response |
|----------------------|----------------|----------------------|----------------------|
| Agent 1: Beginner & Hesitant | Has very little knowledge of optimization and lacks confidence. | Ask basic questions, seek clarification, request a summary, and obtain a mathematical model. | *"I think the problem is about finding the best solution, but I don’t really understand what ‘objective function’ means. Could you explain?"* |
| Agent 2: Some Knowledge & Structured | Understands key optimization concepts but needs clarification on advanced topics. | Provide structured problem details, confirm understanding, request a summary and mathematical model. | *"The problem asks me to minimize cost with some restrictions. I understand that, but I’m unsure how to define the objective function. Can you confirm?"* |
| Agent 3: Advanced & Technical | Knows constraints, variables, and optimization methods but seeks solver recommendations. | Use technical terms, request solver suggestions, expect a detailed mathematical model. | *"The problem is a mixed-integer linear program. Should I apply branch-and-cut or branch-and-bound?"* |
| Agent 4: Curious Learner | Understands some optimization but asks follow-up questions to deepen understanding. | Ask "why" certain methods are used, request a summary, expect detailed explanations. | *"How do constraints affect the solution? Can you provide an example?"* |
| Agent 5: Direct & Action-Oriented | Wants quick, straightforward answers with minimal explanation. | Provide only essential details, expect direct answers, request a summary and mathematical model. | *"The problem is about reducing costs. Just tell me the best method to use."* |
| Agent 6: Over-Explainer | Feels overwhelmed and shares excessive irrelevant information. | Ask for help sorting details, request a summary, seek reassurance. | *"This problem involves maximizing efficiency, but I’m also worried about schedules. Is that part of optimization?"* |
| Agent 7: Doubtful Expert | Has strong knowledge but second-guesses their own abilities. | Request validation of their own solutions, confirm mathematical model correctness. | *"This looks like quadratic programming, and I think I should use gradient-based methods. Am I correct?"* |
| Agent 8: Detail-Oriented | Likes step-by-step confirmations and explains problems thoroughly. | Provide extensive details, seek confirmation at each step, request a summary and mathematical model. | *"I’m thinking of two key variables and fuel constraints. Am I on the right track?"* |
| Agent 9: Concise Expert | Highly knowledgeable and prefers minimal but precise information. | Provide only critical details, request a quick summary and best solver recommendation. | *"The problem is a nonlinear optimization with two constraints. What’s the best solver?"* |
| Agent 10: Practical-Only | No interest in technical details—only cares about results. | Describe problems in practical terms, request a summary and mathematical model without deep understanding. | *"How do I increase revenue while cutting production costs? Just tell me the best solution."* |

The full system prompts include:
- Detailed behavior guidelines for each agent.
- Interaction rules, memory handling, and termination conditions.
- Example responses and expected behaviors.

### 🛠 Interaction Guidelines for Auto-Answering Agents
- Each agent (acting as a user) has predefined goals and response styles.
- All agents request summaries and mathematical models from the `Agent_IC` module.
- No agent is allowed to provide a summary or model—only request them.
- Sessions terminate once the summary and mathematical model are received.
- Each session starts with a memory reset to ensure unbiased interactions.

---

## 🏆 Experiments & Findings

AgentMILO was evaluated against a general LLM agent using:
- 10 distinct Auto Answering Agents acting as user profiles
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
├── 📁 Knowledge Graphs/                      # Expert-designed knowledge graphs for MILP modeling            
│ ├── 📄 Production Planning.mindatom         # Knowledge graph for production planning scenarios
│ ├── 📄 TSP.mindatom                         # Knowledge graph for travelling salesman probelm scenarios
├── 📁 Problem Instances/                     # Tested Problem Instances (TSP & PP)            
│ ├── 📄 Production Planning.md               # PP problem instance with mathematical model
│ ├── 📄 TSP.md                               # TSP problem instance with mathematical model
├── 📄 AgentMILO.ipynb                        # Jupyter Notebook (Code, Prompts, Knowledge Graphs, Conversations, Test Instances)
├── 📄 Auto_Answering_Agents_Prompts.txt      # Full Auto-Answering Agent Prompts
├── 📄 requirements.txt                       # Dependencies
├── 📄 LICENSE                                # License information
└── 📄 README.md                              # Project documentation

```
---

## 📜 License

This project is licensed under the Apache License 2.0 – See the [LICENSE](LICENSE) file for details.


---

## 🔔 Citation

If you use AgentMILO in your research, please cite:

```bibtex
@inproceedings{Gaddam2025AgentMILO,
  author    = {Jyotheesh Gaddam and Lele Zhang and Vicky Mak-Hau and John Yearwood and Bahadorreza Ofoghi and Diego Molla-Aliod},
  title     = {AgentMILO: A Knowledge-Based Framework for Complex MILP Modelling Conversations with LLMs},
  booktitle = {2025 17th International Conference on Computer and Automation Engineering (ICCAE)},
  pages     = {176--182},
  year      = {2025},
  publisher = {IEEE},
  doi       = {10.1109/ICCAE64891.2025.10980596}
}
```

---

## 👥 Authors & Acknowledgments

AgentMILO is developed by:

| Name                  | Institution                 | Email                                      |
|----------------------|---------------------------|--------------------------------------------|
| Jyotheesh Gaddam     | Deakin University         | 📧 [j.gaddam@deakin.edu.au](mailto:j.gaddam@deakin.edu.au) |
| Lele Zhang          | The University of Melbourne | 📧 [lele.zhang@unimelb.edu.au](mailto:lele.zhang@unimelb.edu.au) |
| Vicky Mak-Hau        | Deakin University         | 📧 [vicky.mak@deakin.edu.au](mailto:vicky.mak@deakin.edu.au) |
| John Yearwood        | Deakin University         | 📧 [john.yearwood@deakin.edu.au](mailto:john.yearwood@deakin.edu.au) |
| Bahadorreza Ofoghi   | Deakin University         | 📧 [b.ofoghi@deakin.edu.au](mailto:b.ofoghi@deakin.edu.au) |
| Diego Molla-Aliod    | Macquarie University      | 📧 [diego.molla-aliod@mq.edu.au](mailto:diego.molla-aliod@mq.edu.au) |

This research was fully funded by the Australian Research Council (ARC) Discovery Project DP220101925. We also acknowledge Deakin University, Macquarie University, and The University of Melbourne for providing essential resources.

---

## 📬 Contact
For questions or collaboration inquiries, please reach out via Email or open an issue on GitHub.
