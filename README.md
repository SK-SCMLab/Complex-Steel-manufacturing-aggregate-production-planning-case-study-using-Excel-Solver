# ☮️ Complex-Steel-manufacturing-aggregate-production-planning-case-study-using-Excel-Solver (Simplex LP)
This repository represents a comprehensive operations research case study at a steel production plant facility implementing aggregate production planning using Excel solver to minimise scrap generation across three specialised divisions. 

---

## 🪯 Case study Overview
This case study provides a complete framework for implementing aggregate production planning in steel manufacturing with detailed Excel-model, step-by-step implementation guides and comprehensive documentation that is suitable for industrial application
**Company Profile**: SteelMax Manufacturing
**Total daily capacity**: 50 metric ton
**Planning Horizon**: 30 days
**Primary objective**: Minimize total scrap generation
**Optimization tool**: Excel Solver (Simplex LP)

---

## 🅾️ Three Division structure
### 1. Hot Rolling Division (40% capacity --> 20 Metric Ton/day
- **Products**: Hot rolled coils, Steel plates, Steel strips, Structured steel
- **Operations**: Casting -> Conditioning -> Hot Rolling -> Annealing & Pickling
- **Resources**: 200 labor hours/day across 4 operations
- **Average scrap rate**: 5.4% (varies by product - 18% to 27%)

### 2. Cold Rolling Division (35% capacity --> 17.5 Metric Ton/Day)
- **Products**: Cold rolled coils, Galvanized steel, Automotive steel, Appliance steel
- **Operations**: Bell Annealing -> Cold Rolling -> Precision Strips -> Conditioning
- **Resources**: 175 labor hours/day across 4 operations
- **Average Scrap Rate**: 2.6% (varies by product: 8% to 12%)

### 3. Special Products Division (25% capacity --> 12.5 metric ton/day)
- **Products**: Precision tubes, High-Strength steel, Electrical steel, Tool steel
- **Operations**: Casting -> Hot Rolling -> Cold Rolling -> Precision Strips
- **Resources**: 125 labor hours/day across 4 operations
- **Average Scrap rate**: 7.1% (varies by product: 25% to 30%)

---

## ℹ️ Mathematical Optimization Model
### Decision variables
For each division i and product j:
- Xᵢⱼ = Daily production quantity of product j in division i (metric tons)
### Objective function (Total Scrap Minimization)
-        Minimize: Σ(i,j,k) [Scrap_Rate_ijk * Xᵢⱼ]
where k represents each operation in production sequence
### CONSTRAINT FRAMEWORK
#### Production Capacity Constraints: 
-        ΣⱼXᵢⱼ ≤ Daily_Capacity_i ∀i
#### Labour availability constraints:
-        Σⱼ(Labor_hours_ijk * Xᵢⱼ) ≤ Available_Hours_ik ∀i,k
#### Demand Fulfillment constraints:
-        Xᵢⱼ ≥ Minimum_Demand_ij ∀i,j
#### Non-negativity constraints:
-        Xᵢⱼ ≥ 0 ∀i,j

---

## ♎️ Excel Solver Implementation
### MODEL CONFIGURATION FOR EACH DIVISION
#### Hot Rolling Division Excel Model
- **Variables**: 4 (X_Hot_Rolled_Coils, X_Steel_Plates, X_Steel_Strips, X_Precision_Strips)
- **Objective**: Minimize 0.1800 * X₁ + 0.2300 * X₂ + 0.1900 * X₃ + 0.2700 * X₄
- **Constraints**: 9 Total (1 Capacity + 4 Labor + 4 Demand)
- **Solver Method**: Simplex LP

##### Implementation steps:
1. *Input parameters setup*: Division info, products, operations, scrap rates matrix
2. *Decision variables*: Production quantities to be optimized
3. *Objective function*: SUMPRODUCT(scrap_coefficients, decision variables)
4. *Constraints setup*: Capacity, labor and demand restrictions
5. *Solver configuration*: Minimize objective function by changing decision variables
6. *Result analysis*: Optimal production mix and scrap minimization can be achieved

##### Iterative refinement process
1. **Initial Solution generation**: Feasible starting point meeting all constraints
2. **Constraint validation**: Verify capacity, labor, and demand restrictions verified
3. **Objective improvement**: Iterative scrap minimization through variable adjustment
4. **Sensitivity analysis**: Test solution robustness to parameter changes
5. **Final verification**: Validate practical implementability in production environment

---

## ♻️ Requirements
- Microsoft Excel 2019 or later
- Knowledge on Excel Simplex LP solver
- Steel manufacturing process knowledge

---

*"Information is oil of 21st century, and analytics is the combustion engine" - Peter Soondergard*
