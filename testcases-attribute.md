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
#21=IfcWall('1puWpLzOf0EPMYK0nDJMDS',$,$,$,$,$,$,$,$)
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
#21=IfcWall('2BO5VLbJT5XBAYKSC6dAMT',$,'Foobar',$,$,$,$,$,$)
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
#21=IfcWall('0mRnr7rXr6FxT6BLhvMXcu',$,$,$,$,$,$,$,$)
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
#21=IfcWall('0bWASbkkP5XAGDQmzIA7ME',$,'',$,$,$,$,$,$)
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
#23=IfcRelConnectsPathElements('0bsSAsOmv8vRNlW3WLAD0s',$,$,$,$,#21,#22,(),(),.ATSTART.,.ATEND.)
#21=IfcWall('3cltbDZkbFB8VmpLXZtjYi',$,$,$,$,$,$,$,$)
#22=IfcWall('37R3_1RJjDKu1OqTiIuGFS',$,$,$,$,$,$,$,$)
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
#22=IfcTask('3lR$Q3UTb8HBlXDf1AKx8o',$,$,$,$,$,$,$,$,.T.,$,#21,$)
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

## [FAIL] Inverse attributes cannot be checked and always fail

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>EngagedIn</simpleValue>
  </name>
</attribute>
~~~

~~~lua
#21=IfcPerson($,$,$,$,$,$,$,$)
#23=IfcPersonAndOrganization(#21,#22,$)
#22=IfcOrganization($,'Foo',$,$,$)
~~~

[Sample IDS](fail-inverse_attributes_cannot_be_checked_and_always_fail.ids) - [Sample IFC: #21](fail-inverse_attributes_cannot_be_checked_and_always_fail.ifc)

## [FAIL] Derived attributes cannot be checked and always fail

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>Dim</simpleValue>
  </name>
</attribute>
~~~

~~~lua
#21=IfcCartesianPoint((0.,0.,0.))
~~~

[Sample IDS](fail-derived_attributes_cannot_be_checked_and_always_fail.ids) - [Sample IFC: #21](fail-derived_attributes_cannot_be_checked_and_always_fail.ifc)

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
#21=IfcWall('0cKLM8Dpz1rhbi0FJ5Y7dg',$,'Foobar',$,$,$,$,$,$)
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
#21=IfcWall('2L2zsABxD28et6inRWyPT4',$,'foobar',$,$,$,$,$,$)
~~~

[Sample IDS](fail-attributes_should_check_strings_case_sensitively_2_2.ids) - [Sample IFC: #21](fail-attributes_should_check_strings_case_sensitively_2_2.ifc)

## [FAIL] Value checks always fail for objects

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>TaskTime</simpleValue>
  </name>
  <value>
    <simpleValue>Foobar</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#22=IfcTask('3ibsGt9jHAO8iyGIodmFQZ',$,$,$,$,$,$,$,$,.F.,$,#21,$)
#21=IfcTaskTime($,$,$,$,$,$,$,$,$,$,$,$,$,$,$,$,$,$,$,$)
~~~

[Sample IDS](fail-value_checks_always_fail_for_objects.ids) - [Sample IFC: #22](fail-value_checks_always_fail_for_objects.ifc)

## [FAIL] Value checks always fail for selects

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>DiffuseColour</simpleValue>
  </name>
  <value>
    <simpleValue>Foobar</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#22=IfcSurfaceStyleRendering(#21,$,IfcNormalisedRatioMeasure(0.5),$,$,$,$,$,.FLAT.)
#21=IfcColourRgb($,1.,1.,1.)
IfcNormalisedRatioMeasure(0.5)
~~~

[Sample IDS](fail-value_checks_always_fail_for_selects.ids) - [Sample IFC: #22](fail-value_checks_always_fail_for_selects.ifc)

## [FAIL] Value checks always fail for lists

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>Coordinates</simpleValue>
  </name>
  <value>
    <simpleValue>Foobar</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcCartesianPoint((0.,0.,0.))
~~~

[Sample IDS](fail-value_checks_always_fail_for_lists.ids) - [Sample IFC: #21](fail-value_checks_always_fail_for_lists.ifc)

## [PASS] GlobalIds are treated as strings and not expanded

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>GlobalId</simpleValue>
  </name>
  <value>
    <simpleValue>3nr_EehQX9oxJyZKBa$8vq</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcWall('3nr_EehQX9oxJyZKBa$8vq',$,$,$,$,$,$,$,$)
~~~

[Sample IDS](pass-globalids_are_treated_as_strings_and_not_expanded.ids) - [Sample IFC: #21](pass-globalids_are_treated_as_strings_and_not_expanded.ifc)

## [FAIL] IDS does not bother with string truncation such as for identifiers

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>Identification</simpleValue>
  </name>
  <value>
    <simpleValue>123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345_extra_characters</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcPerson('123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789012345',$,$,$,$,$,$,$)
~~~

[Sample IDS](fail-ids_does_not_bother_with_string_truncation_such_as_for_identifiers.ids) - [Sample IFC: #21](fail-ids_does_not_bother_with_string_truncation_such_as_for_identifiers.ifc)

## [PASS] Numeric values are checked using type casting 1/4

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>RefractionIndex</simpleValue>
  </name>
  <value>
    <simpleValue>42</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcSurfaceStyleRefraction(42.,$)
~~~

[Sample IDS](pass-numeric_values_are_checked_using_type_casting_1_4.ids) - [Sample IFC: #21](pass-numeric_values_are_checked_using_type_casting_1_4.ifc)

## [PASS] Numeric values are checked using type casting 2/4

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>RefractionIndex</simpleValue>
  </name>
  <value>
    <simpleValue>42.</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcSurfaceStyleRefraction(42.,$)
~~~

[Sample IDS](pass-numeric_values_are_checked_using_type_casting_2_4.ids) - [Sample IFC: #21](pass-numeric_values_are_checked_using_type_casting_2_4.ifc)

## [PASS] Numeric values are checked using type casting 3/4

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>RefractionIndex</simpleValue>
  </name>
  <value>
    <simpleValue>42.0</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcSurfaceStyleRefraction(42.,$)
~~~

[Sample IDS](pass-numeric_values_are_checked_using_type_casting_3_4.ids) - [Sample IFC: #21](pass-numeric_values_are_checked_using_type_casting_3_4.ifc)

## [FAIL] Numeric values are checked using type casting 4/4

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>RefractionIndex</simpleValue>
  </name>
  <value>
    <simpleValue>42</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcSurfaceStyleRefraction(42.3,$)
~~~

[Sample IDS](fail-numeric_values_are_checked_using_type_casting_4_4.ids) - [Sample IFC: #21](fail-numeric_values_are_checked_using_type_casting_4_4.ifc)

## [FAIL] Only specifically formatted numbers are allowed 1/4

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>RefractionIndex</simpleValue>
  </name>
  <value>
    <simpleValue>42,3</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcSurfaceStyleRefraction(42.3,$)
~~~

[Sample IDS](fail-only_specifically_formatted_numbers_are_allowed_1_4.ids) - [Sample IFC: #21](fail-only_specifically_formatted_numbers_are_allowed_1_4.ifc)

## [FAIL] Only specifically formatted numbers are allowed 2/4

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>RefractionIndex</simpleValue>
  </name>
  <value>
    <simpleValue>123,4.5</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcSurfaceStyleRefraction(1234.5,$)
~~~

[Sample IDS](fail-only_specifically_formatted_numbers_are_allowed_2_4.ids) - [Sample IFC: #21](fail-only_specifically_formatted_numbers_are_allowed_2_4.ifc)

## [PASS] Only specifically formatted numbers are allowed 3/4

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>RefractionIndex</simpleValue>
  </name>
  <value>
    <simpleValue>1.2345e3</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcSurfaceStyleRefraction(1234.5,$)
~~~

[Sample IDS](pass-only_specifically_formatted_numbers_are_allowed_3_4.ids) - [Sample IFC: #21](pass-only_specifically_formatted_numbers_are_allowed_3_4.ifc)

## [PASS] Only specifically formatted numbers are allowed 3/4

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>RefractionIndex</simpleValue>
  </name>
  <value>
    <simpleValue>1.2345E3</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcSurfaceStyleRefraction(1234.5,$)
~~~

[Sample IDS](pass-only_specifically_formatted_numbers_are_allowed_3_4.ids) - [Sample IFC: #21](pass-only_specifically_formatted_numbers_are_allowed_3_4.ifc)

## [PASS] Integers follow the same rules as numbers

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>NumberOfRisers</simpleValue>
  </name>
  <value>
    <simpleValue>42</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcStairFlight('3rYh787VD52eXvr2MFMeW5',$,$,$,$,$,$,$,42,$,$,$,$)
~~~

[Sample IDS](pass-integers_follow_the_same_rules_as_numbers.ids) - [Sample IFC: #21](pass-integers_follow_the_same_rules_as_numbers.ifc)

## [PASS] Integers follow the same rules as numbers 2/2

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>NumberOfRisers</simpleValue>
  </name>
  <value>
    <simpleValue>42.0</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcStairFlight('3GR$EJ0F9AFQjadylOd$Pi',$,$,$,$,$,$,$,42,$,$,$,$)
~~~

[Sample IDS](pass-integers_follow_the_same_rules_as_numbers_2_2.ids) - [Sample IFC: #21](pass-integers_follow_the_same_rules_as_numbers_2_2.ifc)

## [PASS] Integers are always floored when cast 1/2

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>NumberOfRisers</simpleValue>
  </name>
  <value>
    <simpleValue>42.3</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcStairFlight('38CRvcp1TE6RfT2Nsn7DbS',$,$,$,$,$,$,$,42,$,$,$,$)
~~~

[Sample IDS](pass-integers_are_always_floored_when_cast_1_2.ids) - [Sample IFC: #21](pass-integers_are_always_floored_when_cast_1_2.ifc)

## [PASS] Integers are always floored when cast 2/2

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>NumberOfRisers</simpleValue>
  </name>
  <value>
    <simpleValue>42.7</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcStairFlight('2kal2Zg4bD_BpOCow7hu8R',$,$,$,$,$,$,$,42,$,$,$,$)
~~~

[Sample IDS](pass-integers_are_always_floored_when_cast_2_2.ids) - [Sample IFC: #21](pass-integers_are_always_floored_when_cast_2_2.ifc)

## [PASS] Integers are always floored when cast 2/2

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>NumberOfRisers</simpleValue>
  </name>
  <value>
    <simpleValue>42.7</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcStairFlight('0vsfgHwl513BBXSu9joebj',$,$,$,$,$,$,$,42,$,$,$,$)
~~~

[Sample IDS](pass-integers_are_always_floored_when_cast_2_2.ids) - [Sample IFC: #21](pass-integers_are_always_floored_when_cast_2_2.ifc)

## [FAIL] Booleans must be specified as uppercase strings 1/3

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>IsMilestone</simpleValue>
  </name>
  <value>
    <simpleValue>TRUE</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcTask('25xaitxmjFoO4bQl_bpIdd',$,$,$,$,$,$,$,$,.F.,$,$,$)
~~~

[Sample IDS](fail-booleans_must_be_specified_as_uppercase_strings_1_3.ids) - [Sample IFC: #21](fail-booleans_must_be_specified_as_uppercase_strings_1_3.ifc)

## [PASS] Booleans must be specified as uppercase strings 2/3

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>IsMilestone</simpleValue>
  </name>
  <value>
    <simpleValue>FALSE</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcTask('29$7_aDZH8Uvb3wRjQ3tCP',$,$,$,$,$,$,$,$,.F.,$,$,$)
~~~

[Sample IDS](pass-booleans_must_be_specified_as_uppercase_strings_2_3.ids) - [Sample IFC: #21](pass-booleans_must_be_specified_as_uppercase_strings_2_3.ifc)

## [FAIL] Booleans must be specified as uppercase strings 2/3

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>IsMilestone</simpleValue>
  </name>
  <value>
    <simpleValue>False</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcTask('0v1UdPFB98pAgHQC8DBU$2',$,$,$,$,$,$,$,$,.F.,$,$,$)
~~~

[Sample IDS](fail-booleans_must_be_specified_as_uppercase_strings_2_3.ids) - [Sample IFC: #21](fail-booleans_must_be_specified_as_uppercase_strings_2_3.ifc)

## [PASS] Dates are treated as strings 1/2

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>EditionDate</simpleValue>
  </name>
  <value>
    <simpleValue>2022-01-01</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcClassification($,$,'2022-01-01','Name',$,$,$)
~~~

[Sample IDS](pass-dates_are_treated_as_strings_1_2.ids) - [Sample IFC: #21](pass-dates_are_treated_as_strings_1_2.ifc)

## [FAIL] Dates are treated as strings 1/2

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>EditionDate</simpleValue>
  </name>
  <value>
    <simpleValue>2022-01-01</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcClassification($,$,'2022-01-01+00:00','Name',$,$,$)
~~~

[Sample IDS](fail-dates_are_treated_as_strings_1_2.ids) - [Sample IFC: #21](fail-dates_are_treated_as_strings_1_2.ifc)

## [FAIL] Durations are treated as strings 1/2

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>ScheduleDuration</simpleValue>
  </name>
  <value>
    <simpleValue>PT16H</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcClassification($,$,'PT16H','Name',$,$,$)
~~~

[Sample IDS](fail-durations_are_treated_as_strings_1_2.ids) - [Sample IFC: #21](fail-durations_are_treated_as_strings_1_2.ifc)

## [FAIL] Durations are treated as strings 2/2

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>ScheduleDuration</simpleValue>
  </name>
  <value>
    <simpleValue>PT16H</simpleValue>
  </value>
</attribute>
~~~

~~~lua
#21=IfcClassification($,$,'P2D','Name',$,$,$)
~~~

[Sample IDS](fail-durations_are_treated_as_strings_2_2.ids) - [Sample IFC: #21](fail-durations_are_treated_as_strings_2_2.ifc)

## [PASS] Name restrictions may be used 1/4

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <xs:restriction base="xs:string">
      <xs:pattern value=".*Name.*"/>
    </xs:restriction>
  </name>
</attribute>
~~~

~~~lua
#22=IfcMaterialLayerSet((#21),'Foo',$)
#21=IfcMaterialLayer($,1.,$,$,$,$,$)
~~~

[Sample IDS](pass-name_restrictions_may_be_used_1_4.ids) - [Sample IFC: #22](pass-name_restrictions_may_be_used_1_4.ifc)

## [PASS] Name restrictions may be used 2/4

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <xs:restriction base="xs:string">
      <xs:pattern value=".*Name.*"/>
    </xs:restriction>
  </name>
</attribute>
~~~

~~~lua
#21=IfcMaterialConstituentSet('Foo',$,$)
~~~

[Sample IDS](pass-name_restrictions_may_be_used_2_4.ids) - [Sample IFC: #21](pass-name_restrictions_may_be_used_2_4.ifc)

## [FAIL] Name restrictions may be used 3/4

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <xs:restriction base="xs:string">
      <xs:enumeration value="Name"/>
      <xs:enumeration value="Description"/>
    </xs:restriction>
  </name>
</attribute>
~~~

~~~lua
#21=IfcWall('3drj7pxfP9iQaF9IXxYJO8',$,'Foo',$,$,$,$,$,$)
~~~

[Sample IDS](fail-name_restrictions_may_be_used_3_4.ids) - [Sample IFC: #21](fail-name_restrictions_may_be_used_3_4.ifc)

## [PASS] Name restrictions may be used 4/4

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <xs:restriction base="xs:string">
      <xs:enumeration value="Name"/>
      <xs:enumeration value="Description"/>
    </xs:restriction>
  </name>
</attribute>
~~~

~~~lua
#21=IfcWall('1z2LPvdTP6nQ56_XvfAGey',$,'Foo','Bar',$,$,$,$,$)
~~~

[Sample IDS](pass-name_restrictions_may_be_used_4_4.ids) - [Sample IFC: #21](pass-name_restrictions_may_be_used_4_4.ifc)

## [PASS] Value restrictions may be used 1/3

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>Name</simpleValue>
  </name>
  <value>
    <xs:restriction base="xs:string">
      <xs:enumeration value="Foo"/>
      <xs:enumeration value="Bar"/>
    </xs:restriction>
  </value>
</attribute>
~~~

~~~lua
#21=IfcWall('1tquzHaFzDvQck$gS42a8O',$,'Foo',$,$,$,$,$,$)
~~~

[Sample IDS](pass-value_restrictions_may_be_used_1_3.ids) - [Sample IFC: #21](pass-value_restrictions_may_be_used_1_3.ifc)

## [PASS] Value restrictions may be used 2/3

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>Name</simpleValue>
  </name>
  <value>
    <xs:restriction base="xs:string">
      <xs:enumeration value="Foo"/>
      <xs:enumeration value="Bar"/>
    </xs:restriction>
  </value>
</attribute>
~~~

~~~lua
#21=IfcWall('2dMgJkBqr5TRg6vQubqw$e',$,'Bar',$,$,$,$,$,$)
~~~

[Sample IDS](pass-value_restrictions_may_be_used_2_3.ids) - [Sample IFC: #21](pass-value_restrictions_may_be_used_2_3.ifc)

## [FAIL] Value restrictions may be used 3/3

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>Name</simpleValue>
  </name>
  <value>
    <xs:restriction base="xs:string">
      <xs:enumeration value="Foo"/>
      <xs:enumeration value="Bar"/>
    </xs:restriction>
  </value>
</attribute>
~~~

~~~lua
#21=IfcWall('3mvOY6nOrAUehnFvTGiU6A',$,'Foobar',$,$,$,$,$,$)
~~~

[Sample IDS](fail-value_restrictions_may_be_used_3_3.ids) - [Sample IFC: #21](fail-value_restrictions_may_be_used_3_3.ifc)

## [FAIL] Attributes are not inherited by the occurrence

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>Name</simpleValue>
  </name>
  <value>
    <xs:restriction base="xs:string">
      <xs:enumeration value="Foo"/>
      <xs:enumeration value="Bar"/>
    </xs:restriction>
  </value>
</attribute>
~~~

~~~lua
#21=IfcWall('04C30teKzCzfXGNbREN6ux',$,$,$,$,$,$,$,$)
#23=IfcRelDefinesByType('0aDuDfkjLAkuHxvIUB_Yn8',$,$,$,(#21),#22)
#22=IfcWallType('3GprlX5dD2IecQyhR6GqEy',$,$,'Foobar',$,$,$,$,$,.ELEMENTEDWALL.)
~~~

[Sample IDS](fail-attributes_are_not_inherited_by_the_occurrence.ids) - [Sample IFC: #21](fail-attributes_are_not_inherited_by_the_occurrence.ifc)

## [PASS] Strict numeric checking may also occur within enumeration restrictions

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>RefractionIndex</simpleValue>
  </name>
  <value>
    <xs:restriction base="xs:string">
      <xs:enumeration value="42"/>
    </xs:restriction>
  </value>
</attribute>
~~~

~~~lua
#21=IfcSurfaceStyleRefraction(42.,$)
~~~

[Sample IDS](pass-strict_numeric_checking_may_also_occur_within_enumeration_restrictions.ids) - [Sample IFC: #21](pass-strict_numeric_checking_may_also_occur_within_enumeration_restrictions.ifc)

## [PASS] Strict numeric checking may be done with a bounds restriction

~~~xml
<attribute minOccurs="1" maxOccurs="1">
  <name>
    <simpleValue>RefractionIndex</simpleValue>
  </name>
  <value>
    <xs:restriction base="xs:decimal">
      <xs:minInclusive value="42" fixed="false"/>
      <xs:maxInclusive value="42" fixed="false"/>
    </xs:restriction>
  </value>
</attribute>
~~~

~~~lua
#21=IfcSurfaceStyleRefraction(42.,$)
~~~

[Sample IDS](pass-strict_numeric_checking_may_be_done_with_a_bounds_restriction.ids) - [Sample IFC: #21](pass-strict_numeric_checking_may_be_done_with_a_bounds_restriction.ifc)
