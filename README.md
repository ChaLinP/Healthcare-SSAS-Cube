# 🏥 Healthcare SSAS Cube

## 📚 Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Cube Design](#cube-design)
- [SSAS Cube Implementation](#ssas-cube-implementation)
- [How to Deploy the Cube](#how-to-deploy-the-cube)
- [Sample Database (.bak)](#sample-database-bak)
- [Related Projects](#related-projects)
- [License](#license)

---

## Overview

This project implements a SQL Server Analysis Services (SSAS) cube on top of a healthcare data warehouse modeled using a star schema. The cube allows for multidimensional analysis of healthcare metrics

---

## Dataset

The dataset originates from the [Synthea Project](https://synthea.mitre.org/downloads), consisting of synthetic healthcare records including:

1. Allergies  
2. Patients  
3. Claims  
4. Claims Transactions  
5. Care Plans  
6. Conditions  
7. Devices  
8. Encounters  
9. Imaging Studies  
10. Immunizations  
11. Medications  
12. Observations  
13. Organizations  
14. Payer Transitions  
15. Payers  
16. Procedures  
17. Providers  
18. Supplies

Selected entities were transformed and loaded into a star schema, and the cube is built over that schema.

---

## Cube Design

The cube includes:

### 🔹 Dimensions
- **Patient**
- **Provider**
- **Payer**
- **Date**
- **Organization**

### 🔹 Measures
- **Base Encounter Cost**
- **Total Claim Cost**
- **Payer Coverage**
- **Remaining Claim Amount**
- **Total Coverage Ratio**
- **Additional Charge**

These measures enable slicing and dicing of healthcare financials across various dimensions.

---

## SSAS Cube Implementation

The SSAS cube was implemented using **SQL Server Analysis Services (SSAS) Multidimensional** model. The implementation followed these steps:

1. **Create an Analysis Services Multidimensional Project**  
   A new SSAS Multidimensional project was created using **SQL Server Data Tools (SSDT)**.

2. **Create a Data Source**  
   Connected to the healthcare data warehouse in SQL Server — this is where the cube extracts its data from.

3. **Create a Data Source View (DSV)**  
   A DSV was created to select and visualize the required fact and dimension tables along with their relationships.

4. **Create the Cube Structure**  
   A cube was created using the DSV:
   - Added the `FactEncounters` fact table
   - Added `DimPatients`, `DimProviders`, `DimPayers`, `DimOrganizations`, and `DimDate` as dimensions

5. **Configure Measures and Dimensions**  
   - Selected relevant columns to expose as **measures**
   - Added dimension attributes
   - Created hierarchies where applicable (e.g., Date hierarchy)

6. **Deploy and Process the Cube**  
   Deployed the cube to an SSAS instance and processed it to populate data, making it ready for analysis in tools like **SSMS**, **Excel**, or **Power BI**.

---

## How to Deploy the Cube

1. Open **SQL Server Data Tools (SSDT)** or **Visual Studio with SSAS Extensions**.
2. Clone/download this repo and open the SSAS project solution file.
3. Connect to your local or remote SSAS instance.
4. Deploy and process the cube.
5. Use **SSMS**, **Excel**, or other BI tools to browse and analyze the cube.

---

## Sample Database (.bak)

To work with the cube, restore the provided backup file:

📥 **[Download healthcare_dw.bak](./Medical_DW.bak)**

### Restore Instructions

1. Open **SQL Server Management Studio (SSMS)**.
2. Right-click **Databases** → **Restore Database...**
3. Select **Device** and choose the `.bak` file.
4. Click **OK** to restore.

> ⚠️ Ensure the SQL Server service account has access to the file path.

---

## Related Projects

- [Healthcare OLTP to Data Warehouse](https://github.com/ChaLinP/Healthcare-OLTP-to-Data-Warehouse-for-Analytics)
- [Healthcare SSAS Cube](https://github.com/ChaLinP/Healthcare-SSAS-Cube)
- [Healthcare Power BI and Excel Documentation](https://github.com/ChaLinP/Healthcare-Power-BI-and-Excel-Documentation)

---

## 🪪 License

This project is licensed under the MIT License. See the [LICENSE](./LICENSE) file for details.
