# 🛣️ TSP Tested Problem Instance with Correct Mathematical Model

## 📌 Problem Statement

Mary is responsible for delivering medicines to a group of patients. Each patient has a preferred time window for receiving their medicines:

- Patient A: 10 - 11
- Patient B: 9 - 12
- Patient C: 11 - 12
- Patient D: 9 - 10
- Patient E: 8 - 11
- Patient F: 8 - 10
- Patient G: 9 - 10

Mary will collect all medicines from a pharmacy at time 8 and deliver medicines to the patients. She must finish her work by time 12 and does not need to return to the pharmacy. The travel times between locations are shown below.

---

## 📊 Travel Time Matrix

|               | Pharmacy | Patient A | Patient B | Patient C | Patient D | Patient E | Patient F | Patient G |
|--------------|----------|-----------|-----------|-----------|-----------|-----------|-----------|-----------|
| Pharmacy | 0        | 0.5       | 1.0       | 0.7       | 0.8       | 1.2       | 3.0       | 0.3       |
| Patient A | 1.2     | 0.0       | 1.0       | 1.0       | 0.7       | 0.4       | 1.0       | 0.3       |
| Patient B | 1.0     | 0.5       | 0.0       | 1.2       | 0.3       | 0.2       | 2.0       | 1.3       |
| Patient C | 0.6     | 0.75      | 0.4       | 0.0       | 1.8       | 2.0       | 0.2       | 0.9       |
| Patient D | 2.0     | 1.5       | 0.6       | 0.7       | 0.0       | 1.2       | 1.0       | 1.3       |
| Patient E | 2.5     | 1.9       | 0.5       | 0.3       | 1.8       | 0.0       | 0.3       | 0.5       |
| Patient F | 1.0     | 0.5       | 1.0       | 0.7       | 0.8       | 1.2       | 0.0       | 3.0       |
| Patient G | 1.5     | 0.8       | 0.7       | 1.4       | 0.3       | 2.0       | 0.7       | 0.0       |

---

## 💰 Penalties
- Visiting a patient outside the time window incurs a penalty:
  - Early visit: $10  
  - Late visit: $15  
- Skipping a patient entirely incurs a different penalty:
  - Patient A: $30
  - Patient B: $25
  - Patient C: $50
  - Patient D: $30
  - Patient E: $30
  - Patient F: $40
  - Patient G: $25

Mary needs to plan her route to minimize total costs.

---

## 📌 Mathematical Model
### 🔹 Entities & Parameters
- Nodes: \( I = \{\text{Pharmacy}, \text{Patient A}, \dots, \text{Patient G}\} \)
- Starting point: Pharmacy
- Patient nodes: \( I^* = \{\text{Patient A}, \dots, \text{Patient G}\} \)
- Edges: \( E = \{ij \,|\, i,j \in I \text{ and } i \neq j\} \)
- Travel times: \( t_{ij} \) (given in the matrix)
- Penalties:
  - \( p_i^M \) for skipping patients.
  - \( p_i^E \) for early visits.
  - \( p_i^L \) for late visits.
- Time Constraints:
  - Start time: \( t_{\text{start}} = 8 \)
  - Due time: \( t_{\text{due}} = 12 \)

---

### 🔹 Decision Variables
- \( x_{ij} = 1 \) if edge \( ij \) is traversed, otherwise \( 0 \), for all \( ij \in E \)
- \( y_i = 1 \) if node \( i \) is visited, otherwise \( 0 \), for all \( i \in I \)
- \( u_i \) = order of visit for node \( i \)
- \( a_i \geq 0 \) = arrival time at node \( i \)
- \( z_i^E = 1 \) if visited before \( e_i \), otherwise \( 0 \)
- \( z_i^L = 1 \) if visited after \( l_i \), otherwise \( 0 \)

---

### 🎯 Objective Function
\[
\min \left( \sum_{i \in I^*} (p_i^E z_i^E + p_i^L z_i^L)  + \sum_{i \in I^*} p_i^M (1 - y_i) \right)
\]
Minimize total penalties for early/late visits and skipping patients.

---

### 🔹 Constraints
1. Node visitation condition:  
   \[
   y_i = \sum_{j \in I} x_{ji},\quad \forall i \in I
   \]
2. Flow conservation:  
   \[
   \sum_{j \in I} x_{ij} = \sum_{j \in I} x_{ji},\quad \forall i \in I^*
   \]
3. Arrival time constraint:  
   \[
   a_j \geq \sum_{i \in I} x_{ij} (a_i + s_i + t_{ij}),\quad \forall j \in I^*
   \]
4. Travel time limit:  
   \[
   a_i \leq t_{\text{due}},\quad \forall i \in I^*
   \]
5. Earliness/Lateness penalties:  
   \[
   M z_i^E \geq e_i - a_i,\quad \forall i \in I^*
   \]
   \[
   M z_i^L \geq a_i - l_i,\quad \forall i \in I^*
   \]
6. Subtour elimination (MTZ constraints):  
   \[
   u_i + 1 - u_j \leq M(1 - x_{ij}),\quad \forall ij \in E
   \]
7. Pharmacy is the starting point:  
   \[
   y_{\text{Pharmacy}} = 1, \quad u_{\text{Pharmacy}} = 0
   \]
8. Variable constraints:
   - \( y_i, x_{ij} \in \{0,1\} \), for all \( i \in I \), \( ij \in E \)
   - \( u_i \in \mathbb{Z}^+ \), for all \( i \in I \)
   - \( a_i \geq t_{\text{start}} \), for all \( i \in I \)

---
