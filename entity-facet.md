# Entity facet

Every entity in an IFC model has an "IFC Class" **Name**. For example, wall entities will have an IFC class of IfcWall. Classes aren’t just for categorising elements. They also indicate what types of properties and relationships it is allowed to have. For example, a Wall Class can have a fire rating property, but a Grid Class cannot. Here are a list of valid IFC class names:

 - [IFC4 list of IFC class names](https://standards.buildingsmart.org/IFC/RELEASE/IFC4/ADD2_TC1/HTML/link/inheritance-general-usage-all%20entities.htm)
 - [IFC2X3 list of IFC class names](https://standards.buildingsmart.org/IFC/RELEASE/IFC2x3/TC1/HTML/alphabeticalorder_entities.htm)

Some entities may also optionally have a **Predefined Type**. This is a further level of entity categorisation in addition to the IFC Class **Name**. For example, an IfcWall may have a **Predefined Type** of SHEAR, or PARTITIONING. Whereas the IFC Class **Name** is specified by the IFC standard, the **Predefined Type** may also contain custom values by the user.

TODO: describe how a user knows what predefined types are possible

One of the most important aspects of writing a specification is to ensure that it applies to the appropriate IFC class. Typically, every single **Specification** will have an **Entity Facet** used in its **Applicability** section.

## Parameters

Parameter | Required | Restrictions Allowed | Allowed Values | Meaning
--- | --- | --- | --- | ---
**Name** | ✅ | ✅ | A valid IFC class from the IFC schema. | The IFC Class must match exactly
**Predefined Type** | ❌ | ✅ | A valid predefined type from the IFC schema, or any custom text value. | The IFC Predefined Type must match exactly

## Examples

Intention | Facet Definition
--- | ---
All partition walls | Name="IFCWALL", PredefinedType="PARTITIONING"
All type elements | Name="IFC.*TYPE"
