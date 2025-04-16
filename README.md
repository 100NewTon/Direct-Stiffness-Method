# **Structural Analysis Program Report**  
**2D Frame Analysis Using Direct Stiffness Method**  

---

## **1. Project Overview**  
This Python program performs **structural analysis of 2D frames** using the **Direct Stiffness Method**. It computes:  
✔ **Displacements** at nodes  
✔ **Reaction forces** at supports  
✔ **Internal forces** in members  

**Key Features:**  
✅ Object-oriented implementation (`Node` & `Member` classes)  
✅ Handles multiple load types (point, distributed, trapezoidal)  
✅ Solves large systems using **NumPy** and **SymPy**  
✅ Outputs formatted results with **Tabulate**  

---

## **2. Methodology**  
### **2.1 Input Data Handling**  
- **Nodes:** Defined by coordinates, support type (fixed/pinned/roller), and external forces.  
- **Members:** Defined by start/end nodes, material properties (E, A, I), and applied loads.  

### **2.2 Matrix Formulation**  
1. **Local Stiffness Matrix (6×6):** Combines axial and bending effects.  
   ```python
   def l_stiffness_matrix(A, E, L, I):
       # Computes local stiffness matrix for a member
   ```
2. **Transformation Matrix:** Converts local to global coordinates.  
   ```python
   def transformation(theta):
       # Rotation matrix for coordinate transformation
   ```
3. **Global Stiffness Matrix:** Assembled from all members.  

### **2.3 Load Processing**  
- Fixed-end forces calculated for:  
  - Point loads  
  - Uniformly distributed loads (UDL)  
  - Trapezoidal loads  

### **2.4 Equation Solving**  
1. **Partitioning:** Separates free and restrained DOFs.  
2. **Solution:** Uses **SymPy** to solve:  
   ```
   [K]{U} = {F} - {F₀}
   ```
   where:  
   - `[K]` = Global stiffness matrix  
   - `{U}` = Displacement vector  
   - `{F}` = Applied forces  
   - `{F₀}` = Fixed-end forces  

---

## **3. Key Results**  
### **Example Case (3-Node Frame)**  
| Variable    | Value          |  
|-------------|----------------|  
| `u_2`       | 0.00518 m      |  
| `v_2`       | 0.00232 m      |  
| `θ_2`       | 4.285 rad      |  
| `Hu_1`      | -9.38 N        |  
| `Vu_1`      | -40.63 N       |  
| `Mu_3`      | 156.25 Nm      |  

**Interpretation:**  
- Node 2 displaces horizontally (5.18 mm) and vertically (2.32 mm).  
- Reactions at supports balance the applied 100 N load.  

---

## **4. Technical Highlights**  
### **4.1 Code Structure**  
```python
class Node:  # Stores node properties (coordinates, supports)
class Member:  # Defines member geometry, material, and loads

# Core functions:
calculate_global_stiffness_matrix()  # Assembles system matrix
calculate_fixed_end_forces()         # Computes equivalent nodal loads
solve_system()                      # Solves for displacements/reactions
```

### **4.2 Numerical Techniques**  
- **Sparse Matrix Handling:** Efficient assembly of large matrices.  
- **Symbolic Solving:** Uses SymPy for exact solutions.  
- **Validation:** Checks equilibrium (∑F = 0, ∑M = 0).  

---

## **5. Limitations & Future Work**  
- **Current Limitations:**  
  ❌ Limited to 2D frames (no out-of-plane loads).  
  ❌ No visualization of deformed shape.  

- **Future Improvements:**  
  ✅ Add 3D support.  
  ✅ Integrate matplotlib for plotting results.  

---

## **6. How to Use**  
1. **Input:** Define nodes/members via interactive prompts.  
2. **Run:**  
   ```python
   python frame_analysis.py
   ```
3. **Output:** Displacements and reactions in tabular format.  

---

## **7. Conclusion**  
This program provides a **robust, scalable solution** for 2D frame analysis, demonstrating:  
✔ **Core structural mechanics principles**  
✔ **Effective use of Python for engineering computations**  
✔ **Modular design for future extensions**  

**GitHub Link:** [Insert Repository URL]  

--- 
**Developed by:** [Manas Dwivedi]  
**Date:** [04/2025]
