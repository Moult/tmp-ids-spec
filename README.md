# Information Delivery Specifications

**Information Delivery Specifications (IDS)** is a buildingSMART standard for specifying and checking information requirements from IFC models. It is designed as a free, simple, standardised approach to model checking.

## Introduction

An IDS is a file format ending in `.ids` containing a list of information **Specifications**. For example, a single **Specification** might say that "_all walls must have a fire rating property_". Model authors receiving an IDS file can use it to ensure all required information is provided for each **Specification**. Model recipients may use the IDS file to check whether the IFC model meets all of the **Specifications**. Reports may also be generated to list the results of **Specification** compliance checks.

[ ... image ... ]

IDS file creation tools and model checking tools are provided by many [software vendors](https://technical.buildingsmart.org/resources/software-implementations/). You can write your own customised IDS **Specifications** from scratch or use a [public IDS templates](todo) as a template. Any IFC model produced from any software can be checked by an IDS file.

To get started quickly, [download a sample IDS file](todo) and load it up in one of the software from our [software vendors](https://technical.buildingsmart.org/resources/software-implementations/) directory.

## How to create a specification

A **Specification** is designed to be easy for humans to understand. However, **Specifications** are also highly structured so that computer software may automatically and accurately check information requirements with no ambiguity. Every **Specification** has three parts:

 1. **Description**: a description of why the **Specification** is important to your project and instructions of how to achieve it. This part is designed for humans to read and understand why information is being requested.
 2. **Applicability**: which type of objects the **Specification** applies to. There are many different types of objects in IFC models, such as walls, doors, and windows, but each **Specification** will only apply to certain objects.
 3. **Requirements**: what information is required for the objects specified in part 2, such as required properties or classifications.

For example, the **Specification** of "_all walls must have a fire rating property_" is structured like so:

 1. **Description**: wall fire ratings are critical for building code compliance
 2. **Applicability**: this specification applies to all wall objects
 3. **Requirements**: the aforementioned wall objects must have a fire rating property

**Applicability** and **Requirements** can be described in terms of five different **Facets** of information:

Facet Type | Facet Parameters | Example applicability | Example requirement
--- | --- | --- | ---
**Entity** | **IFC Class** and **Predefined Type** | Applies to "IfcWall" with predefined type of "SHEAR" | Must be an "IfcWall" with a predefined type of "SHEAR"
**Attribute** | **Name** and **Value** | Applies to elements with the attribute "Name" having the value "W01" | Must have the attribute "Name" with the value "W01"
**Classification** | **System** and **Value** | Applies to elements classified under "Uniclass 2015" as "EF_25_10_25" | Must have a "Uniclass 2015" classification reference of "EF_25_10_25"
**Property** | **Property Set**, **Name**, and **Value** | Applies to elements with a property set of "Pset_WallCommon" with a "LoadBearing" property set to "TRUE" | Must have a "Pset_WallCommon" property set with a "LoadBearing" property set to "TRUE"
**Material** | **Value** | Applies to "concrete" elements | Must have a "concrete" material
**Parts** | **Entity** and **Relationship** | Applies to elements that are "contained in" an "IfcSpace" | Must be "contained in" an "IfcSpace"

You can combine multiple **Facets** together in either the **Applicability** or **Requirements** section to describe a wide variety of **Specifications**. Some **Facets** may have optional parameters. For example, if you want to specify that a property should exist, but not the exact value, you may omit the value parameter of the **Property Facet**.

You may also specify a list of valid values, or a range of numbers, or text pattern for some **Facet Parameters**. These are known as **Complex Restrictions**. For example, you would use a **Complex Restriction** to specify that a fire rating property must choose from either the value "0HR", "1HR", or "2HR" only.

Here are a few examples to whet your appetite:

Description | Applicability | Requirements
--- | --- | ---
External load bearing walls need to have a fire rating property for code compliance | <ul><li>**Entity Facet** (**IFC Class** is IfcWall)</li><li>**Property Facet** (**Property Set** is Pset_WallCommon, **Name** is LoadBearing, **Value** is TRUE)</li></ul> | <ul><li>**Property Facet** (**Property Set** is Pset_WallCommon, **Name** is FireRating)</li></ul>
Bedrooms should have a minimum area of 10m2 | <ul><li>**Entity Facet** (**IFC Class** is IfcSpace)</li><li>**Attribute Facet** (**Description** must contain the text "BEDROOM")</li></ul> | <ul><li>**Property Facet** (**Property Set** is Qto_SpaceBaseQuantities, **Name** is NetFloorArea, **Value** is >= 10)</li></ul>
All brick wall types must be classified and follow the approved naming convention | <ul><li>**Entity Facet** (**IFC Class** is IfcWallType)</li><li>**Material Facet** (**Value** is brick)</li></ul> | <ul><li>**Classification Facet** (**System** is Uniclass 2015, **Value** must start with EF_25_10)</li><li>**Attribute Facet** (**Name** is Name, **Value** must be the letters "WT" followed by 2 numbers, such as WT01, WT02, etc)</li></ul>

To see the full capabilities of what each information each **Facet** can specify, see the sections below for more detail.

Some information cannot be checked by IDS. For example, geometry checks like "_all walls need to be 3m away from the site boundary_" are not possible. Checks that rely on calculated or dynamic values are also not possible, like "_the total area of all office spaces must be more than 300m2_" or "_the names of all door types must be unique_" are not possible.

### Specifying complex restrictions

TODO

### Specifying entities

Every entity in an IFC model has an "IFC Class" **Name**. For example, wall entities will have an IFC class of IfcWall. Classes aren’t just for categorising elements. They also indicate what types of properties and relationships it is allowed to have. For example, a Wall Class can have a fire rating property, but a Grid Class cannot. Here are a list of valid IFC class names:

 - [IFC4 list of IFC class names](https://standards.buildingsmart.org/IFC/RELEASE/IFC4/ADD2_TC1/HTML/link/inheritance-general-usage-all%20entities.htm)
 - [IFC2X3 list of IFC class names](https://standards.buildingsmart.org/IFC/RELEASE/IFC2x3/TC1/HTML/alphabeticalorder_entities.htm)

Some entities may also optionally have a **Predefined Type**. This is a further level of entity categorisation in addition to the IFC Class **Name**. For example, an IfcWall may have a **Predefined Type** of SHEAR, or PARTITIONING. Whereas the IFC Class **Name** is specified by the IFC standard, the **Predefined Type** may also contain custom values by the user.

TODO: describe how a user knows what predefined types are possible

One of the most important aspects of writing a specification is to ensure that it applies to the appropriate IFC class.

Parameter | Required | Restrictions Allowed | Allowed Values | Meaning
--- | --- | --- | --- | ---
**Name** | ✅ | ✅ | A valid IFC class from the IFC schema. | The IFC Class must match exactly
**Predefined Type** | ❌ | ✅ | A valid predefined type from the IFC schema, or any custom text value. | The IFC Predefined Type must match exactly

#### Examples

Intention | Facet Definition
--- | ---
All partition walls | Name="IFCWALL", PredefinedType="PARTITIONING"
All type elements | Name="IFC.*TYPE"


### Specifying attributes

### Specifying classifications

### Specifying properties

### Specifying materials

### Specifying parts

## Start using IDS in your projects

## Implementing IDS as a developer

TODO see unit tests, XSD, etc
