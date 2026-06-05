# PM Module: Real-Time Events Reference

This document lists the **Plant Maintenance (PM)** entities supported by OneConnect for real-time data extraction, along with their underlying SAP tables, CDS Views, and the event mechanisms (BOR and RAP) that trigger the streaming.

When configuring an entity in the SAP Data Modeler, the values below are used in the **Main Customizing Data** section to define the **Change Document Object** and the event that will trigger real-time data transmission.

---

## Entity Reference Table

| Entity | CDS View | Tables | Change Doc Object | BOR Event | RAP Event | Actions |
|---|---|---|---|---|---|---|
| **Equipment Master** | `I_EQUIPMENT`<br>`I_EQUIPMENTDATA`<br>`I_EQUIPMENTCATEGORY`<br>`I_EQUIPMENTTEXT`<br>`I_EQUIPMENTTIMESEG`<br>`I_EQUIPMENTBOMLINK` |  | `EQUI` | `A_EQUIPMENT` |  | CRE, UPD, DEL |
| **Functional Location** | `I_FUNCTIONALLOCATION`<br>`I_FUNCTIONALLOCATIONTEXT`<br>`I_FUNCTIONALLOCATIONDATA`<br>`I_FUNCTIONALLOCATIONPARTNERTP`<br>`I_FUNCTIONALLOCATIONCATEGORY`<br>`I_FUNCTIONALLOCATIONSTATUS`<br>`I_FUNCTIONALLOCBOMLINK` | `IFLOT`<br>`IFLOS`<br>`IHPA`<br>`IFLOTX`<br>`ILOA`<br>`T001W`<br>`TPST` |  | `CL_EAM_FL_EVENTS` | `R_FUNCTIONALLOCATIONTP` | CRE, UPD |
| **Maintenance Order** |  | `AFIH`<br>`AUFK`<br>`AFKO`<br>`AFVC`<br>`AFVV`<br>`ILOA`<br>`AFVU` |  | `BUS2007` | `R_MAINTENANCEORDERTP` | CRE, RELEASE, COMP |
| **Notification** | `I_QLTYNOTIFICATION`<br>`I_QUALITYNOTIFICATIONITEM`<br>`I_QLTYNOTIFICATIONTASK`<br>`I_QLTYNOTIFICATIONCAUSE`<br>`I_QLTYNOTIFICATIONACTIVITY` | `QMEL`<br>`QMIH`<br>`QMFE`<br>`ILOA`<br>`QMSM`<br>`QMMA`<br>`QMUR` |  | `BUS2078` | `R_MAINTENANCENOTIFICATIONTP` | CRE, RELEASE, COMP |
| **Work Clearance Document** |  |  | `WCD` |  |  | CRE, RELEASE, COMP, SET ACTIVE |

---

## Action Codes

| Code | Meaning |
|---|---|
| **CRE** | Creation |
| **UPD** | Change / Update |
| **DEL** | Delete |
| **RELEASE** | Release |
| **COMP** | Complete |
| **SET ACTIVE** | Activate record / status |

---

## Event Type Reference

OneConnect supports two SAP-standard event mechanisms for real-time data extraction:

| Event Type | Available In | Description |
|---|---|---|
| **BOR Event** | SAP ECC and S/4HANA | Classic Business Object Repository event mechanism. |
| **RAP Event** | SAP S/4HANA only | Modern RESTful ABAP Programming event mechanism. |

When both are listed for an entity, you can choose whichever fits your SAP version and architectural preferences. When only one is listed, that is the recommended (or only available) trigger for that entity.

> ℹ️ For an overview of all event mechanisms supported by OneConnect (BOR, RAP, BTE, PPF), see the [Architecture and Components manual](../../Technical_Information/02-Architecture_and_Components.md).
