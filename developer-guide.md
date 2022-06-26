# Developer guide

**Warning: IDS is not yet formally released.**

An IDS file is simply an XML file, with its schema defined in XSD. You may open any existing IDS file and inspect its contents to get a feel for how an IDS is structured.

An IDS is considered valid if it passes the XSD-based validation check. All sample IDS files available in the buildingSMART directory of public IDS templates are guaranteed to be valid.

 - [Download the latest IDS v0.6 XSD schema](https://github.com/buildingSMART/IDS/blob/master/Development/0.6/ids_06.xsd)
 - [Download sample IDS files from the directory of public IDS templates](todo)

There are many freely available online tools and programming libraries that can perform XSD validation. Here is [one such XSD validation tool](https://www.liquid-technologies.com/online-xsd-validator) to save you an online search.

## Authoring IDS

If you are writing software to read and author IDS files only, you **must** meet the following criteria:

 - All IDS software must read and write valid IDS files only.
 - No proprietary extensions are allowed. If auxiliary systems (e.g. additional loaded metadata) are used to augment IDS or the correlating IFC model, they should be made clear to the user that it is external to IDS.
 - No data loss shall occur. Loading an IDS and saving the IDS shall preserve all of its information. Minor syntax formatting changes are allowed, so long as the data remains unchanged.
 - Your software should pass all test cases in the [Authoring Testcases](todo) document.

In addition, it is highly recommended to also provide the following features for users:

 - When users write an IFC class in an **Entity Facet**, your interface should restrict allowable values to valid IFC class names in the selected IFC schema for the specification. Autocompletion is recommended.
 - When users write a predefined type in an **Entity Facet**, your interface should recommend allowable values based on the nominated IFC class. However, it should still allow users to write a custom predefined type. Autocompletion is recommended.
 - When users have already specified an **Entity Facet** and are creating an **Attribute Facet**, your interface should restrict allowable values based on the nominated IFC class. Your interface should also guide the user to use the right data type based on the nominated attribute name.
 - When users have already specified an **Entity Facet** and are creating a **Property Facet**, your interface should recommend allowable property sets based on the nominated IFC class and predefined type. However, it should also allow users to write a custom property set name. If a standardised (e.g. `Pset_` or `Qto_`) property set is nominated, your interface should restrict the allowable property names and recommend the appropriate data type to be used.
 - You may also choose to preload standardised classification names for commonly known systems, as well as the classification references to prevent spelling errors. You may choose to use this [IFC directory for classification systems](https://github.com/Moult/ifcclassification).
 - When users are nominating a **Material Facet**, your interface should recommend the IFC recommended material categories (one of 'concrete', 'steel', 'aluminium', 'block', 'brick', 'stone', 'wood', 'glass', 'gypsum', 'plastic', or 'earth')

## Checking IDS against IFC

Any software implementing IDS checking **must** comply with the following test suites.

 - Overall integration testscases (todo)
 - [Entity testcases](testcases-entity.md)
 - [Attribute testcases](testcases-attribute.md)
 - [Classification testcases](testcases-classification.md)
 - [Property testcases](testcases-property.md)
 - [Material testcases](testcases-material.md)
 - [Part testcases](testcases-parts.md)

## Generating reports from IDS results

TODO: specify rules about BCF

## Handling IFC compatibility

If the software is not capable of parsing the specified IFC version nominated by the IDS specification, then the user should be made aware of the limitation.

## Handling different IDS versions

IDS is not yet formally released and so there is no guarantee of vendor support for any IDS version.

## Available developer libraries

To help you get started with development, here is a directory of IDS libraries that you may use in your application. Please feel free to [submit your library](https://github.com/buildingSMART/IDS/pulls).

Language | License | Library
--- | --- | ---
C# | ? | [XBim](todo)
Python | LGPL-3.0-or-later | [IfcOpenShell](todo)
? | ? | ODA?
Javascript | ? | Something or other

## More reading

 - [Add your implementation to the software vendors directory](https://technical.buildingsmart.org/resources/software-implementations/)
 - [Make a suggestion for improvement](https://github.com/buildingSMART/IDS/issues)
