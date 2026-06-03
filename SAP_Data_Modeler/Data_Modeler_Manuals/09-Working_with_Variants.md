# Working with Variants

This guide explains how to create, configure, and use variants within entities. Variants allow you to predefine parameters, dynamic dates, or selection options that can be reused across executions. By leveraging variants, you can streamline processes, ensure consistency, and schedule jobs more efficiently.

---

## Getting Started

### 1. Execute the Entity Normally

To begin working with variants for an entity, first execute the entity as usual.
<img width="921" height="601" alt="image" src="https://github.com/user-attachments/assets/c1fda3d5-8680-45cc-8b18-8bc71688e3a9" />

### 2. Select the Fields and Save

Select the fields you want to define as variants and click **"Save"**.
<img width="921" height="517" alt="image" src="https://github.com/user-attachments/assets/4e8c2963-8569-43a2-9438-a12cb4a51f04" />

> ℹ️ At this stage, it is not necessary to assign values to these fields. You can leave the values blank.

### 3. Save the Variant

On the following screen, choose **"Save Variant"** to start defining the dynamic variants for the selected fields.
<img width="921" height="517" alt="image" src="https://github.com/user-attachments/assets/1d0b3c92-97d7-4e1e-ad45-67fd6bbcc346" />

---

## Defining a Variant

When creating a new variant, complete the following steps:

### 1. Assign a Name and Description

Provide a clear and descriptive name along with a short explanation of the variant's purpose. This helps you and other users easily identify it later when running the entity.
<img width="921" height="358" alt="image" src="https://github.com/user-attachments/assets/5284ccfc-6d83-4c19-ad29-4e39cc8eeb0d" />

> ⚠️ Make sure that the variant name does not exceed **14 characters**.

### 2. Choose Fixed Variant (Optional)

If you select the option **"Take values from previous screen"**, the system will save this as a **Fixed Variant**. In this case, the variant will use exactly the same field values you selected in the previous step (the screen where you identified the columns).
<img width="921" height="271" alt="image" src="https://github.com/user-attachments/assets/471b3847-7ff0-4867-a06e-0857fb7965b0" />

> ℹ️ This option is useful when you want to lock the variant to a specific predefined configuration.

### 3. Define Variable Values

In the table shown, you will see all the fields that were selected as variables. For each field, you can assign values or logic conditions (such as ranges or dynamic dates) depending on the type of variable you want to configure.
<img width="921" height="168" alt="image" src="https://github.com/user-attachments/assets/40425f20-acfe-476a-aa90-a6ed52e452a1" />

---

## Variable Types

For each variable, select the **Variable Type**. The following options are available:

| Type | Name | Description |
|---|---|---|
| **T** | Table Variable from TVARVC | Uses a variable previously defined in `TVARVC` by referencing it. |
| **D** | Dynamic Date Calculation (Local Date) | Defines a dynamic date based on the user's local time. *(Only available if the selected field is a date.)* |
| **X** | Dynamic Date Calculation (System Date) | Defines a dynamic date based on the system's local time. *(Only available if the selected field is a date.)* |

---

## Using Table Variables from TVARVC

When selecting this option, enter the name of the parameter previously created in `TVARVC` under **"Explanation"**.
<img width="921" height="302" alt="image" src="https://github.com/user-attachments/assets/e43c0dc7-0a88-42d0-afcb-b2c9d1e7a92b" />

### Creating a Parameter in TVARVC

### Step 1: Access Transaction STVARV

Open transaction **`STVARV`**.

### Step 2: Enable Edit Mode

Select **"Edit/Change"**.
<img width="921" height="455" alt="image" src="https://github.com/user-attachments/assets/0e03d46f-113f-43eb-a7be-d6da52177104" />

### Step 3: Choose Parameter Type

Choose whether to create a **Parameter** or a **Selection Option**, then click **"Create"**.
<img width="921" height="457" alt="image" src="https://github.com/user-attachments/assets/ad25ca5f-150d-4238-9cea-6575958155f5" />

| Type | Description |
|---|---|
| **Parameter** | Assign a name and a **fixed value** for the variant, then save. |
<img width="921" height="517" alt="image" src="https://github.com/user-attachments/assets/d0acb981-5fe4-412d-91f8-20531eecd717" />

| Type | Description |
|---|---|
| **Selection Option** | Assign a name and the required **ranges or multiple values**. You can also include logical conditions (e.g., include, exclude, greater than). Then save. |
<img width="921" height="520" alt="image" src="https://github.com/user-attachments/assets/4d2df284-e9cf-4902-a023-6801b8caf387" />

---

## Using Dynamic Date Calculation

Dynamic Date Calculation is especially useful when you need to work with dates that change depending on when the entity is executed. Instead of setting a fixed date, you can define a relative date or a range of dates that will always adjust automatically to the execution time.

To configure this type of variable, follow these steps:

### Step 1: Select SIGN

In the **SIGN** column, decide whether you want to include or exclude the values:

| Sign | Behavior |
|---|---|
| **I** (Include) | The system will use the selected date(s) as part of the results. |
| **E** (Exclude) | The system will filter out records that match the selected date(s). |

> ⚠️ **Important:** You can select **only one option per variant**, so make sure to assign only one sign.

### Step 2: Select Option

In the **Option** column, define the logical condition that applies to the date field. Some common options include:

| Option | Description |
|---|---|
| **Equal** | Matches an exact date. |
| **Not Equal** | Excludes a specific date. |
| **Greater Than** | Includes records after a specific date. |
| **Less Than** | Includes records before a specific date. |
<img width="921" height="786" alt="image" src="https://github.com/user-attachments/assets/762e4bbf-ae80-4c90-86df-272013a124da" />

### Step 3: Enter Values (X and Y)

If the option you choose requires one or more values (`X` and `Y`), a new window will appear where you can define the relative values for `X` and `Y`. Use the following signs:

| Symbol | Meaning |
|---|---|
| **`X` Value** | Number of days. |
| **`Y` Value** | Number of days. |
| **`-` (minus)** | Indicates past days relative to the execution date. |
| **`+` (plus)** | Indicates future days relative to the execution date. |
<img width="921" height="727" alt="image" src="https://github.com/user-attachments/assets/229d55dd-d5db-47d3-a318-a7934fd9b908" />

> ℹ️ **Example:** Suppose you want to extract data created between today and the last 10 days. In this case:
>
> - `Y Value +0` = today's date.
> - `X Value -10` = 10 days before today.
>
> This ensures that every time the entity runs, it automatically adjusts to always include today and the past 10 days.

### Step 4: Save the Variant

Once you confirm the values, click **"Save"**. The variant will now be stored and can be reused in future executions or scheduled jobs, ensuring consistent and dynamic date filtering.
<img width="921" height="320" alt="image" src="https://github.com/user-attachments/assets/fa087f95-f40d-4737-8a52-dc3df563aff7" />

---

## Executing Entities with Variants

Once a variant has been created for a specific entity, a new field called **"Variant"** will appear when executing the entity. By clicking the matchcode, you can select any previously saved variant for that entity.

From here, you can run the entity in real time or schedule a job for one-time or periodic execution using the defined variant.
<img width="921" height="695" alt="image" src="https://github.com/user-attachments/assets/a3a74033-abb0-43e4-b4ae-ec55cbb61ce8" />
