# Identifying Compatible CDS Views

The purpose of this manual is to provide a simple and practical guide to identifying CDS Views within SAP that are compatible with the OneConnect Data Modeler. It outlines the necessary steps in a clear and concise manner, allowing users to quickly locate and validate views suitable for integration with OneConnect's data modeling tools.

---

## Considerations to Identify Compatible CDS Views and CDS View Entities

The SAP Data Modeler is compatible with the following CDS Views and CDS View Entities:

1. **Standard Views**
2. **Custom Views**

These include the following view types:

- **Private Views** (prefix `P_*`)
- **Interface Views** (prefix `I_*`)
- **Consumption Views** (prefix `C_*`)

### Compatibility Condition

While identifying compatible CDS Views, it is important to ensure the following condition is met:

> ⚠️ **Important:** The CDS View must **not** contain the authorization **`#PRIVILEGED_ONLY`** in its Data Definition (`@AccessControl.authorizationCheck: #PRIVILEGED_ONLY`).

To ensure that the CDS View or CDS View Entity does not have the `#PRIVILEGED_ONLY` authorization restriction, follow the steps below.

---

## Verifying the Authorization Check

### Step 1: Access Transaction SE11

In the SAP GUI, open transaction **`SE11`** (ABAP Dictionary). This transaction enables you to view and explore table structures, as well as browse and query table data directly within the SAP system.

<img width="189" height="111" alt="image" src="https://github.com/user-attachments/assets/1578f29e-648c-464e-a176-4f01604cf4c7" />

### Step 2: Select Data Type

Select the **"Data Type"** option, type the name of the CDS View, and click on **"Display"**.
<img width="853" height="582" alt="image" src="https://github.com/user-attachments/assets/10828d33-5e1b-4789-95b9-f5a7cc6f6da6" />

### Step 3: Inspect the Content

Select the **"Content"** tab. In the **Data Definition** section for the CDS View, identify that the value of the parameter **`@AccessControl: authorizationCheck`** is not marked as `#PRIVILEGED_ONLY`.

| Value | Compatible with OneConnect? |
|---|---|
| `#CHECK` | ✅ Yes |
| `#NOT_REQUIRED` | ✅ Yes |
| `#MANDATORY` | ✅ Yes |
| `#PRIVILEGED_ONLY` | ❌ No |
<img width="1033" height="677" alt="image" src="https://github.com/user-attachments/assets/5ee5f13e-92a3-43ea-bfb5-dbb82bc294dd" />

---

## Optional: Identifying CDS Views / SQL View Names Compatible with the SAP Data Modeler

In addition to using CDS Views directly in the SAP Data Modeler, it is also possible to use the **SQL table names** of each view, if one has been defined. The SQL table name can be identified by following these steps.

### Step 1: Access Transaction SE16

In the SAP GUI, open transaction **`SE16`** (Data Browser). This transaction allows you to browse and query table data directly within SAP.

<img width="190" height="113" alt="image" src="https://github.com/user-attachments/assets/a432b493-240f-47d9-b941-7f14ebb57290" />

### Step 2: Search the DD02L Table

In the **Table Name** field, enter **`DD02L`** and press **`Enter`**.
<img width="849" height="268" alt="image" src="https://github.com/user-attachments/assets/6c732ae4-0d0d-4610-9a35-9e4c440c4b58" />

> ℹ️ The `DD02L` table contains metadata for all transparent tables and views defined in the system, including CDS Views.

### Step 3: Apply Search Criteria

In the search criteria screen for table `DD02L`, configure the following fields:

| Field | Value |
|---|---|
| **Table Name** | Enter a search pattern using the format `I<Module>(Optional)*<EntityName>*`. This pattern helps narrow down the list to CDS Views following a specific naming convention (e.g., `I*CUSTOMER*` to find views related to customers). |
| **Table Category** | Select the value **`VIEW`**. This ensures that only view objects (not transparent tables or other types) are included in the results. |
<img width="383" height="61" alt="image" src="https://github.com/user-attachments/assets/8a647858-3086-46a8-a3ff-0bf83ba9b3d6" />
<img width="604" height="97" alt="image" src="https://github.com/user-attachments/assets/d0387b4d-1acc-47e6-9675-e33177412969" />

### Step 4: Execute the Search

Click the **Execute** button (or press **`F8`**) to run the search based on the criteria provided. The system will return a list of all view objects that match the specified pattern and are categorized as `VIEW`.

From the results, locate the desired CDS View by reviewing the entries and identifying its **Table Name**, which typically corresponds to the SQL View Name defined for the CDS View.
<img width="919" height="668" alt="image" src="https://github.com/user-attachments/assets/2f929d17-3a5f-4419-901e-a7dc895adfdb" />

### Step 5: Use the Table Name in OneConnect Data Modeler

Take the identified **Table Name** (SQL View Name) and enter it into the OneConnect Data Modeler exactly as shown.
<img width="835" height="355" alt="image" src="https://github.com/user-attachments/assets/8f50b9c2-c470-47ff-a694-cd09f1550342" />

---

> ℹ️ For further support with modeling or configuration in OneConnect, please contact the Onibex team.
