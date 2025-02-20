# 🏭 PP Tested Problem Instance with Correct Mathematical Model: Created by Vicky Mak-Hau

## 📌 Problem Statement

We have a **multi-period, multi-product production planning (PP) problem**. The planning involves **four time periods**:
- **Spring (91 days)**
- **Summer (94 days)**
- **Autumn (91 days)**
- **Winter (89 days)**

The production consists of **three types of cookware**:
- **Fry Pans**
- **Grill Pans**
- **Saucepans**

### **💰 Costs and Workforce**
- **Workers**: 50 regular workers are available.
- **Wage**: $20 per hour.
- **Work hours available per day**: 400 hours (no overtime allowed).
- **Time required per product**:
  - **Fry Pan**: 2 hours
  - **Grill Pan**: 4 hours
  - **Saucepan**: 2 hours

📌 **Labour costs are not minimized**, but workforce constraints must be respected.

---

## 📊 Product Costs Table

| **Product**  | **Unit Material Cost (\$)** | **Unit Shortage Cost (\$)** |
|-------------|----------------------|----------------------|
| **Fry Pan** | 12                   | 50                   |
| **Grill Pan** | 16                   | 60                   |
| **Saucepan** | 14                   | 40                   |

---

## 📈 Demand Forecast (Units per Season)

| **Product**  | **Spring (91 Days)** | **Summer (94 Days)** | **Autumn (91 Days)** | **Winter (89 Days)** |
|-------------|----------------|----------------|----------------|----------------|
| **Fry Pan**  | 20,000         | 16,000         | 15,000         | 28,000         |
| **Grill Pan** | 18,000         | 10,000         | 28,000         | 30,000         |
| **Saucepan**  | 16,000         | 18,000         | 17,000         | 25,000         |

📌 **Fixed Costs Per Product** (per season):
- **Fry Pan**: $1,600
- **Grill Pan**: $1,500
- **Saucepan**: $2,000

---

## 📌 **Mathematical Model**
### **🔹 Sets**
- **Products**: \( \{ \text{Fry Pans}, \text{Grill Pans}, \text{Saucepans} \} \)
- **Periods**: \( \{ \text{Spring}, \text{Summer}, \text{Autumn}, \text{Winter} \} \)

### **🔹 Parameters**
- **Days per period**: \( \text{daysInPeriods} = \{ 91, 94, 91, 89 \} \)
- **Build time (hours per product)**: \( \text{buildTime} = \{ 2, 4, 2 \} \)
- **Total work hours available per day**: \( 400 \)
- **Unit material cost**: \( \text{unitMaterialCost} = \{ 12, 16, 14 \} \)
- **Unit shortage cost**: \( \text{unitShortageCost} = \{ 50, 60, 40 \} \)
- **Fixed cost per product per season**: \( \text{fixedCost} = \{ 1600, 1500, 2000 \} \)
- **Predicted demand per product per season**:
  \[
  \text{demand} =
  \begin{bmatrix}
  20000 & 16000 & 15000 & 28000 \\
  18000 & 10000 & 28000 & 30000 \\
  16000 & 18000 & 17000 & 25000
  \end{bmatrix}
  \]

---

### **🔹 Decision Variables**
- \( nbToProduce_{i,j} \geq 0 \) = Number of units to produce for product \( i \) in period \( j \)
- \( toProduceOrNot_{i,j} \in \{0, 1\} \) = Binary variable indicating if product \( i \) is produced in period \( j \)
- \( nbShortage_{i,j} \geq 0 \) = Number of shortage units for product \( i \) in period \( j \)

---

### **🎯 Objective Function**
Minimize the **total cost**, including:
- **Material cost**
- **Shortage cost**
- **Fixed cost per season**
\[
\min \sum_{i \in \text{Products}} \sum_{j \in \text{Periods}} 
\left( \text{unitMaterialCost}_i \cdot nbToProduce_{i,j} +
       \text{unitShortageCost}_i \cdot nbShortage_{i,j} +
       \text{fixedCost}_i \cdot toProduceOrNot_{i,j} \right)
\]

---

### **🔹 Constraints**
#### **1. Production Logic**
- A product can be produced only if it is selected for production in that period:
\[
nbToProduce_{i,j} \leq \text{demand}_{i,j} \cdot toProduceOrNot_{i,j}, \quad \forall i, j
\]

#### **2. Demand Satisfaction**
- Total production + shortage must cover demand:
\[
nbToProduce_{i,j} + nbShortage_{i,j} \geq \text{demand}_{i,j}, \quad \forall i, j
\]

#### **3. Workforce Constraints**
- Total man-hours must not exceed available hours:
\[
\text{daysInPeriods}_j \cdot 400 \geq \text{buildTime}_i \cdot nbToProduce_{i,j}, \quad \forall i, j
\]

---


## 📌 **Mathematical Model (PP)**  

### **🔹 Sets**  
- **Products**: \( \{ \text{Fry Pans}, \text{Grill Pans}, \text{Saucepans} \} \)  
- **Periods**: \( \{ \text{Spring}, \text{Summer}, \text{Autumn}, \text{Winter} \} \)  

### **🔹 Parameters**  
- **Days per period**:  
  \[
  \text{daysInPeriods} = \{ 91, 94, 91, 89 \}
  \]
- **Build time (hours per product)**:  
  \[
  \text{buildTime} = \{ 2, 4, 2 \}
  \]
- **Total work hours available per day**:  
  \[
  400
  \]
- **Unit material cost**:  
  \[
  \text{unitMaterialCost} = \{ 12, 16, 14 \}
  \]
- **Unit shortage cost**:  
  \[
  \text{unitShortageCost} = \{ 50, 60, 40 \}
  \]
- **Fixed cost per product per season**:  
  \[
  \text{fixedCost} = \{ 1600, 1500, 2000 \}
  \]
- **Predicted demand per product per season**:  
  \[
  \text{demand} =
  \begin{bmatrix}
  20000 & 16000 & 15000 & 28000 \\
  18000 & 10000 & 28000 & 30000 \\
  16000 & 18000 & 17000 & 25000
  \end{bmatrix}
  \]

---

### **🔹 Decision Variables**  
- \( nbToProduce_{i,j} \geq 0 \) = Number of units to produce for product \( i \) in period \( j \)  
- \( toProduceOrNot_{i,j} \in \{0, 1\} \) = Binary variable indicating if product \( i \) is produced in period \( j \)  
- \( nbShortage_{i,j} \geq 0 \) = Number of shortage units for product \( i \) in period \( j \)  

---

### **🎯 Objective Function**  
Minimize the **total cost**, including:  
- **Material cost**  
- **Shortage cost**  
- **Fixed cost per season**  

\[
\min \sum_{i \in \text{Products}} \sum_{j \in \text{Periods}} 
\left( \text{unitMaterialCost}_i \cdot nbToProduce_{i,j} +
       \text{unitShortageCost}_i \cdot nbShortage_{i,j} +
       \text{fixedCost}_i \cdot toProduceOrNot_{i,j} \right)
\]

---

### **🔹 Constraints**  
#### **1. Production Logic**  
- A product can be produced only if it is selected for production in that period:  

\[
nbToProduce_{i,j} \leq \text{demand}_{i,j} \cdot toProduceOrNot_{i,j}, \quad \forall i, j
\]

#### **2. Demand Satisfaction**  
- Total production + shortage must cover demand:  

\[
nbToProduce_{i,j} + nbShortage_{i,j} \geq \text{demand}_{i,j}, \quad \forall i, j
\]

#### **3. Workforce Constraints**  
- Total man-hours must not exceed available hours:  

\[
\text{daysInPeriods}_j \cdot 400 \geq \text{buildTime}_i \cdot nbToProduce_{i,j}, \quad \forall i, j
\]
