# Attribute testcases

These testcases are designed to help describe behaviour in edge cases and ambiguities. All valid IDS implementations must demonstrate identical behaviour to these test cases.

## [FAIL] Invalid attribute names always fail

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>Foobar</simpleValue>
  </name>
</attribute>
~~~

~~~lua
#21=IfcWall('2iXMdP3PX8oOMqHOE59BGT',$,$,$,$,$,$,$,$)
~~~

[Sample IDS](fail-invalid_attribute_names_always_fail.ids) - [Sample IFC: #21](fail-invalid_attribute_names_always_fail.ifc)

## [PASS] Attributes with a string value should pass

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>Name</simpleValue>
  </name>
</attribute>
~~~

~~~lua
#21=IfcWall('1IjUD7Psj1WfOgA3q27cxy',$,'Foobar',$,$,$,$,$,$)
~~~

[Sample IDS](pass-attributes_with_a_string_value_should_pass.ids) - [Sample IFC: #21](pass-attributes_with_a_string_value_should_pass.ifc)

## [FAIL] Attributes with null values always fail

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>Name</simpleValue>
  </name>
</attribute>
~~~

~~~lua
#21=IfcWall('3cgsg9VVn6Nf4QRir987X5',$,$,$,$,$,$,$,$)
~~~

[Sample IDS](fail-attributes_with_null_values_always_fail.ids) - [Sample IFC: #21](fail-attributes_with_null_values_always_fail.ifc)

## [FAIL] Attributes with empty strings always fail

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>Name</simpleValue>
  </name>
</attribute>
~~~

~~~lua
#21=IfcWall('2F4eLApEnA$vhJNKb55eBU',$,'',$,$,$,$,$,$)
~~~

[Sample IDS](fail-attributes_with_empty_strings_always_fail.ids) - [Sample IFC: #21](fail-attributes_with_empty_strings_always_fail.ifc)

## [PASS] Attributes with a zero number have meaning and should pass

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>CountValue</simpleValue>
  </name>
</attribute>
~~~

~~~lua
#21=IfcQuantityCount('Foobar',$,$,0.,$)
~~~

[Sample IDS](pass-attributes_with_a_zero_number_have_meaning_and_should_pass.ids) - [Sample IFC: #21](pass-attributes_with_a_zero_number_have_meaning_and_should_pass.ifc)

## [PASS] Attributes with a boolean true should pass

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>IsCritical</simpleValue>
  </name>
</attribute>
~~~

~~~lua
#21=IfcTaskTime($,$,$,$,$,$,$,$,$,$,$,$,$,.T.,$,$,$,$,$,$)
~~~

[Sample IDS](pass-attributes_with_a_boolean_true_should_pass.ids) - [Sample IFC: #21](pass-attributes_with_a_boolean_true_should_pass.ifc)

## [PASS] Attributes with a boolean false should pass

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>IsCritical</simpleValue>
  </name>
</attribute>
~~~

~~~lua
#21=IfcTaskTime($,$,$,$,$,$,$,$,$,$,$,$,$,.F.,$,$,$,$,$,$)
~~~

[Sample IDS](pass-attributes_with_a_boolean_false_should_pass.ids) - [Sample IFC: #21](pass-attributes_with_a_boolean_false_should_pass.ifc)

## [FAIL] Attributes with an empty list always fail

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>RelatingPriorities</simpleValue>
  </name>
</attribute>
~~~

~~~lua
#23=IfcRelConnectsPathElements('2ldtlAGmX1vfhcDdXHaKMc',$,$,$,$,#21,#22,(),(),.ATSTART.,.ATEND.)
#21=IfcWall('2Jv55WRe56RRjP8U8VdMLB',$,$,$,$,$,$,$,$)
#22=IfcWall('0W_PUYC9v7rRpWDCrAWMe$',$,$,$,$,$,$,$,$)
~~~

[Sample IDS](fail-attributes_with_an_empty_list_always_fail.ids) - [Sample IFC: #23](fail-attributes_with_an_empty_list_always_fail.ifc)

## [FAIL] Attributes with an empty set always fail

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>LayerStyles</simpleValue>
  </name>
</attribute>
~~~

~~~lua
#22=IfcPresentationLayerWithStyle('Foo',$,(#21),$,.T.,.F.,.F.,())
#21=IfcCartesianPoint((0.,0.,0.))
~~~

[Sample IDS](fail-attributes_with_an_empty_set_always_fail.ids) - [Sample IFC: #22](fail-attributes_with_an_empty_set_always_fail.ifc)

## [FAIL] Attributes with a logical unknown always fail

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>LayerOn</simpleValue>
  </name>
</attribute>
~~~

~~~lua
#22=IfcPresentationLayerWithStyle('Foo',$,(#21),$,.U.,.F.,.F.,())
#21=IfcCartesianPoint((0.,0.,0.))
~~~

[Sample IDS](fail-attributes_with_a_logical_unknown_always_fail.ids) - [Sample IFC: #22](fail-attributes_with_a_logical_unknown_always_fail.ifc)

## [PASS] Attributes with a zero duration should pass

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>ScheduleDuration</simpleValue>
  </name>
</attribute>
~~~

~~~lua
#21=IfcTaskTime($,$,$,$,'P0D',$,$,$,$,$,$,$,$,$,$,$,$,$,$,$)
~~~

[Sample IDS](pass-attributes_with_a_zero_duration_should_pass.ids) - [Sample IFC: #21](pass-attributes_with_a_zero_duration_should_pass.ifc)

## [PASS] Attributes referencing an object should pass

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>TaskTime</simpleValue>
  </name>
</attribute>
~~~

~~~lua
#22=IfcTask('3TpfzbUErFivLJwz601MTf',$,$,$,$,$,$,$,$,.T.,$,#21,$)
#21=IfcTaskTime($,$,$,$,$,$,$,$,$,$,$,$,$,$,$,$,$,$,$,$)
~~~

[Sample IDS](pass-attributes_referencing_an_object_should_pass.ids) - [Sample IFC: #22](pass-attributes_referencing_an_object_should_pass.ifc)

## [PASS] Attributes with a select referencing an object should pass

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>DiffuseColour</simpleValue>
  </name>
</attribute>
~~~

~~~lua
#23=IfcSurfaceStyleRendering(#21,$,#22,$,$,$,$,$,.FLAT.)
#21=IfcColourRgb($,1.,1.,1.)
#22=IfcColourRgb($,1.,1.,1.)
~~~

[Sample IDS](pass-attributes_with_a_select_referencing_an_object_should_pass.ids) - [Sample IFC: #23](pass-attributes_with_a_select_referencing_an_object_should_pass.ifc)

## [PASS] Attributes with a select referencing a primitive should pass

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>DiffuseColour</simpleValue>
  </name>
</attribute>
~~~

~~~lua
#22=IfcSurfaceStyleRendering(#21,$,IfcNormalisedRatioMeasure(0.5),$,$,$,$,$,.FLAT.)
#21=IfcColourRgb($,1.,1.,1.)
IfcNormalisedRatioMeasure(0.5)
~~~

[Sample IDS](pass-attributes_with_a_select_referencing_a_primitive_should_pass.ids) - [Sample IFC: #22](pass-attributes_with_a_select_referencing_a_primitive_should_pass.ifc)

## [PASS] Attributes should check strings case sensitively 1/2

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>Name</simpleValue>
  </name>
  <value>
    <simpleValue>Foobar</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcWall('3w$3J1r6DDcAZUo_qcMv9d',$,'Foobar',$,$,$,$,$,$)
~~~

[Sample IDS](pass-attributes_should_check_strings_case_sensitively_1_2.ids) - [Sample IFC: #21](pass-attributes_should_check_strings_case_sensitively_1_2.ifc)

## [FAIL] Attributes should check strings case sensitively 2/2

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>Name</simpleValue>
  </name>
  <value>
    <simpleValue>Foobar</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcWall('1X3JfwTL18WRHiuSQV9DWU',$,'foobar',$,$,$,$,$,$)
~~~

[Sample IDS](fail-attributes_should_check_strings_case_sensitively_2_2.ids) - [Sample IFC: #21](fail-attributes_should_check_strings_case_sensitively_2_2.ifc)
