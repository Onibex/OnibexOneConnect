# Introduction

This document provides a step-by-step guide for creating and configuring an entity within Onibex's SAP Data Modeler using transaction `ZONT_ONECM`.

An **entity** in the Data Modeler is defined as a **set of standard SAP tables and their key fields**, which are **logically connected through `INNER JOIN` and `LEFT OUTER JOIN` relationships**. Entities represent structured data models tailored to a specific business domain, enabling efficient querying, integration, and reuse of SAP data.

This guide outlines the essential processes, including selecting the appropriate domain and data type, defining entity attributes, assigning tables and relationships, configuring field and table aliases, and setting entity filters.

The guide helps users distinguish between **Master Data** (which remains relatively unchanged) and **Transactional Data** (which captures specific events within a business process). It also explains how to establish relationships between tables, modify field aliases, and apply filters to ensure data integrity and relevance.

By following the outlined procedures, users can effectively structure and optimize entities for efficient data management and business process integration within SAP. This ensures consistency, accuracy, and proper utilization of system resources while maintaining compliance with organizational standards.

---

## Create an Entity

Access the SAP Data Modeler using transaction **`ZONT_ONECM`**.

<img width="342" height="241" alt="image" src="https://github.com/user-attachments/assets/2c029ee3-2327-4def-8374-8baac036a718" />

To create a new entity manually, click on **"Create"**.

<img width="921" height="374" alt="image" src="https://github.com/user-attachments/assets/88f0a0c3-2260-48a8-8a84-29355c052375" />

After clicking **"Create"**, you will be taken to the entity configuration screen.

<img width="998" height="276" alt="image" src="https://github.com/user-attachments/assets/cca16806-ea56-48fe-8515-f9a50cc433c5" />

### Entity Name

In the **"Entity"** field, enter the name of the entity. This name must be unique and must not match any entity that has been previously loaded into the system.

<img width="492" height="47" alt="image" src="https://github.com/user-attachments/assets/cb47b23d-0d69-4188-b60e-3987828589e3" />


### Tag Data and Tag Metadata

In the **"Tag Data"** and **"Tag Metadata"** sections, check each box as needed to include the data contained in the tags located in the specified rows of the configuration (Tag 1 through Tag 5).

<img width="110" height="28" alt="image" src="https://github.com/user-attachments/assets/76cdb977-e6c8-47ec-abda-07102acfa381" /> <img width="118" height="23" alt="image" src="https://github.com/user-attachments/assets/2432e165-3478-4eb7-9953-166f5ee3ba75" />


Select these options only if your use case requires sending either the tag values or their associated metadata. ***(It is recommended to check them to easily track information.)***

- **Tag 1** is **mandatory**. It should contain the **Domain**, which represents the SAP business process associated with the entity. Select the most appropriate option from the available **dropdown list** that best describes the business context of this entity.
<img width="195" height="291" alt="image" src="https://github.com/user-attachments/assets/84ef9261-ce2c-4462-bd0f-37f32263f08d" />

- **Tags 2 and 3** contain **prefilled values** that are configured in the parameter tables (as explained in the [Customizing Parameters manual](https://help.onibex.com/portal/en/kb/articles/sap-data-modeler-customizing-parameters)). These values are used to **identify the SAP version and instance** from which this entity is sending data.
<img width="303" height="61" alt="image" src="https://github.com/user-attachments/assets/1612f590-880c-44c8-b18f-a802db8d72d7" />

- **Tags 4 and 5** are **optional**. They can contain any type of information that is relevant to the entity and may help further identify or describe it in more detail.
<img width="254" height="64" alt="image" src="https://github.com/user-attachments/assets/7d77a146-7edb-4077-b8bc-a73baecda0b9" />


---

## Assigning Tables and Relationships

After configuring the entity's Name and Tags, you can proceed to assign its tables and define the relationships between them.

Click on **"Build Join"**.
<img width="1011" height="390" alt="image" src="https://github.com/user-attachments/assets/983590bd-2e9d-4934-8259-c92bea008e3f" />

### Adding a Table

To add a table, click on the indicated symbol or use the shortcut **`SHIFT + F1`**.

A pop-up window will appear where you must enter the table name (you can also add Z Tables and CDS Views). For this example, use **`VBAK`** and click **"Continue"**.
<img width="921" height="423" alt="image" src="https://github.com/user-attachments/assets/3a5f5a3b-9fb0-49d5-85c7-9120b37657e2" />

The table will be added to the entity and displayed with its list of fields/columns, identifying key fields within each table.
<img width="921" height="437" alt="image" src="https://github.com/user-attachments/assets/9a859b28-963a-4ec4-8c0c-01e1ac74495a" />

### Adding Related Tables

If another table related to the first one is added, a relationship between key fields will be automatically established. For example, adding the **`VBAP`** table will create a relationship through the **`VBELN`** fields.
<img width="921" height="378" alt="image" src="https://github.com/user-attachments/assets/6b972343-5ffc-4359-855a-7d2841c0f78e" />

### Modifying Relationships

To change the relationship type between fields, right-click the relationship and select **"Inner Join"** or **"Left Outer Join"** as needed. Relationships can also be deleted.
<img width="921" height="365" alt="image" src="https://github.com/user-attachments/assets/4c883083-58fe-459e-9fa4-c0c1a209d8d9" />

To manually create a relationship between two fields, click on the desired field and drag the cursor to link it to another field. It will be identified with a dotted line and colored points (red and blue) to mark connection points.
<img width="921" height="382" alt="image" src="https://github.com/user-attachments/assets/d7274380-195b-45f2-b3f1-4c118cd9e246" />

If no existing relationships are found between two tables, click **"Join Conditions"** to let the modeler generate relationships automatically.
<img width="921" height="407" alt="image" src="https://github.com/user-attachments/assets/2c7a7a7e-f7bb-44cf-99f1-532c3cd4e36a" />
<img width="921" height="410" alt="image" src="https://github.com/user-attachments/assets/c6fbe3ab-490d-41a4-b92b-2a1ef42b962b" />

Once table additions and relationship configurations are complete, click **"Back"** to continue.

---

## Adding Columns to Selected Tables

After adding the desired tables, the next step is to select the required columns from each selected table.

Review each table on the left side of the screen, expand it to view all available columns, and then choose the specific columns you want to include in your entity configuration.

Click on **"Column Definition"**.
<img width="1011" height="390" alt="image" src="https://github.com/user-attachments/assets/7617adb9-d93e-40c3-8c9c-037e746cdbf1" />

Within this screen, you will see two main sections:

- **Left Side: Available Fields.** Displays the **selected tables**. When you expand a table from the list, you will see **all available columns** for that table.
- **Right Side: Selected Fields.** Also shows the **selected tables**, but in this section only the **columns you have selected** for each table will be visible. This allows you to review and manage the specific data fields that will be used.
<img width="1056" height="248" alt="image" src="https://github.com/user-attachments/assets/e3d5521a-030e-440d-bc7c-58f6200b83e5" />
<img width="1148" height="554" alt="image" src="https://github.com/user-attachments/assets/28c34bd4-dd86-4534-84cb-3e0c7758ee55" />

### Selecting Columns

To select a column, locate it in the expanded list on the left side of the screen and double-click on it. This action will add the column to your selection, and it will appear in the corresponding table on the right side.
<img width="1316" height="265" alt="image" src="https://github.com/user-attachments/assets/3c173708-8e68-4665-a2cc-b8241cfccd01" />

### Removing Columns

To remove a column from your selection, double-click on it in the list on the right side, and it will be removed from the selected fields.

Once the column additions are complete, click **"Back"** to continue.

📺 [Watch video tutorial: Adding Columns](https://www.youtube.com/watch?v=Ddo66vPcxvE](https://www.youtube.com/watch?v=zfHWnxKEfO4)

---

## Configuring Table and Field Aliases

After completing your table and column selection, you can proceed to configure the alias for each table.

Aliases are used to simplify table references and improve readability during the modeling process. They are especially useful when you prefer to work with friendly and easily identifiable names instead of technical table names. Aliases will also be reflected in the target subscriber, allowing for more intuitive interpretation of the data structure.

In the entity configuration, go to the **"Table Relations"** and **"Field List and Customizing"** sections (identified by expand/collapse buttons).
<img width="921" height="518" alt="image" src="https://github.com/user-attachments/assets/7463ab07-dcc4-4490-8488-b3b1fad751bd" />

### Table Aliases

The first list displays tables loaded into the entity with their technical name, alias, description, and key field relationships.
<img width="921" height="156" alt="image" src="https://github.com/user-attachments/assets/56fc7b0e-9a4d-49c4-83a2-27536284791f" />

> ⚠️ The **"ID"** column with a warning icon (if present) indicates that the table is being used in another entity with the same alias. Modifying fields in one entity will affect the other.

To change the alias and description, click on the text field and enter the new alias.
<img width="921" height="129" alt="image" src="https://github.com/user-attachments/assets/59287255-690d-4939-9b06-55649813ae88" />

### Field Aliases

Similarly, field/column aliases can be modified in the second list. Click on the **"Field Alias"** text field and enter the desired alias. **"Field Description"** can also be modified this way.
<img width="921" height="383" alt="image" src="https://github.com/user-attachments/assets/966a508e-d752-4632-bc3a-551f5053bc6d" />

> ℹ️ Key field aliases cannot be modified if their table alias is being used in another entity.

The **"KeyFlag"** column indicates whether a field is a key field for the table by default. The **"Selection"** column allows selecting a field as a batch data submission criterion (explained in another manual).
<img width="917" height="258" alt="image" src="https://github.com/user-attachments/assets/d6b7183f-fdf8-441f-b07c-fcbc894c45f8" />

---

## Configuring Entity Filters

If the entity should send data meeting specific criteria based on selected tables and fields, filters can be applied.

At the top of the entity configuration, click **"Define Filters"**.
<img width="1011" height="390" alt="image" src="https://github.com/user-attachments/assets/a3a344e5-20ae-443b-b73c-26ee9b27e6e7" />

This section displays folders representing the added tables. Expanding them reveals the selected fields/columns.
<img width="800" height="511" alt="image" src="https://github.com/user-attachments/assets/d0a28cfb-3534-439c-874b-c936fb6638e5" />

To select and filter a field, double-click it to open options for individual values or ranges on the right side. Multiple filters can be enabled as needed by double-clicking each field.
<img width="921" height="465" alt="image" src="https://github.com/user-attachments/assets/c8236fe5-00fd-4f00-9827-042146f37068" />

After selecting the filters, click **"Save"** at the bottom.

> ℹ️ **Example:** For this example, the entity is configured to send only sales order data created between **01.01.2024** and **31.12.2024**, transactions in **USD**, and organization **1710**.

---

## Configuring Main Customizing Data

Just before saving the entity, certain customizations must be defined to extract the data selected in the entity. These options are found in the **"Main Customizing Data"** section.
<img width="1161" height="289" alt="image" src="https://github.com/user-attachments/assets/d19a06be-6b24-4c5d-a47f-4691b71ad17c" />

Here is a general overview of each segment:

### 1. Data Type

Select whether the data is **Master (D)** or **Transactional (T)**. The difference between these types has been explained previously.
<img width="346" height="79" alt="image" src="https://github.com/user-attachments/assets/b4c4361c-8113-4925-b471-fa6d3eaf4408" />

### 2. Description

Provide a general description of the entity and its contents. This section is for informational purposes only.
<img width="233" height="32" alt="image" src="https://github.com/user-attachments/assets/457d4187-b9d2-4dad-bc81-abf916e37f46" />

### 3. Output Type

Choose the output type associated with this entity. This selection is necessary if the data will be transmitted in real time and if the corresponding output type has already been configured. Details on this configuration can be found in the [Customizing Output Types manual](https://help.onibex.com/portal/en/kb/articles/oneconnec#Customizing_Output_Types).
<img width="146" height="28" alt="image" src="https://github.com/user-attachments/assets/d0cf532c-6603-4e2e-9a01-899ddaae9293" />

### 4. Change Document Object and Object Type

If data transmission occurs in real time, in addition to being sent via the Output Type, it can also be triggered by an event. In this case, the **Change Document Object** and **Object Type** must be defined.
<img width="611" height="625" alt="image" src="https://github.com/user-attachments/assets/ab869d67-3677-49ba-8f1b-252ff4f7b004" />

> ℹ️ This configuration should be prepackaged in the OneConnect transport. If some data is missing, please contact the Onibex team.

### 5. Number of Records

Select the number of records the entity will send per request. The recommended value is **100** for optimal performance and stability during data transmission.
<img width="187" height="37" alt="image" src="https://github.com/user-attachments/assets/9d420f08-57bf-4e91-a1cb-fd69f3838428" />

### 6. Event ID

Check this box if the information being sent requires an **Event ID** to identify the executed event. Enabling this option is recommended to ensure traceability and proper event identification.
<img width="116" height="31" alt="image" src="https://github.com/user-attachments/assets/e498ffa0-9aa9-4ce0-961c-bd2f9ba71d7c" />

### 7. Auth Object

Here, you can assign an authorization object to the specific entity. This ensures that only SAP users with the defined authorization object can **modify or delete** the entity.

To configure it:

1. Enter the **Authorization Object** in the corresponding field.
2. Click on **"Set Values"**.
3. In the **Value** field, type the required value for the authorization object.
<img width="317" height="38" alt="image" src="https://github.com/user-attachments/assets/ec80ef46-fbc5-4afa-a27e-2935cbc9dfa0" />
<img width="182" height="76" alt="image" src="https://github.com/user-attachments/assets/209012e0-e8af-4a27-96aa-b623e8c156a2" />

### 8. Log

Here, you can choose where to store the process log of this entity. There are two available options:

- **Standard Log:** Saves all logs in the **standard OneConnect log table**.
- **Server File:** Stores all logs in a **`.txt`** file located in an **application server directory** (this option requires a valid directory path to be specified).
<img width="354" height="114" alt="image" src="https://github.com/user-attachments/assets/2c92771a-1d00-49c4-bf5e-60b5bc379ccb" />

---

## Save Entity Customization

After finishing the configuration of the entity, to save all the changes, go to **"Save Customizing"** in the header of the entity configuration.
<img width="1011" height="390" alt="image" src="https://github.com/user-attachments/assets/717856e2-f745-4878-a30c-ec49d10bd334" />

If changes are detected, the system will let you know. Select the package where the configuration will be located, then click on **"Save"**.
<img width="1137" height="683" alt="image" src="https://github.com/user-attachments/assets/76c56f03-fd9b-41d9-8a3a-f4140b8e7125" />

After saving the configuration in the selected package, the system will prompt you to provide a **Workbench request**. This request is required to store the created structures within the SAP system and ensure they are properly transported and version-controlled.
<img width="1128" height="657" alt="image" src="https://github.com/user-attachments/assets/d51d9126-75f4-41bb-9cf8-1e9ed11465c2" />

> ⚠️ **After clicking "Save", the system will begin processing the entity.** Depending on the number of tables and fields included, this process may take several minutes. **Please be patient and do not close SAP during this time.** Allow the system to complete the saving operation.

Once the process is finished, you will be automatically redirected to the **OneConnect main menu**, and a **confirmation message** will appear at the bottom of the screen. At this point, the entity will have been successfully created and will be **available for execution** in the **Entities list**.
<img width="352" height="46" alt="image" src="https://github.com/user-attachments/assets/bc049e6c-0a48-4771-87f1-835740c91839" />

---

## Technical Considerations

When defining and setting up an entity in the SAP Data Modeler, keep the following best practices in mind:

- **Use unique names:** Ensure that no two entities share the same name to avoid system conflicts and confusion.
- **Apply a language filter when required:** If a table within an entity contains a *Language* field, add a Language Filter to prevent data overflow or processing issues.
- **Avoid special characters:** Do not use special characters in technical names or aliases for tables and columns. Use only underscores (`_`) as separators.
- **Limit alias length:** While the system can handle long aliases, excessively long strings may cause issues in specific scenarios. Keep aliases concise.
- **Enable EventID and tags:** Activating EventID configuration and tags can help track and manage your data effectively.
- **Manage table aliases carefully:** Tables with the same alias are shared across multiple entities. If you need a table to be specific to one entity, assign it a unique alias.

---

## Video Tutorial

📺 [Watch the full video tutorial on YouTube](https://www.youtube.com/watch?v=FJ-ue0oAoYI)
