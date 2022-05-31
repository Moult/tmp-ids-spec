# Entity testcases

These testcases are designed to help describe behaviour in edge cases and ambiguities. All valid IDS implementations must demonstrate identical behaviour to these test cases.

## [FAIL] Invalid entities always fail

~~~xml
<entity>
  <name>
    <simpleValue>IFCRABBIT</simpleValue>
  </name>
</entity>
~~~

~~~lua
#21=IfcWall('1LEPrOiHz0CRJRmOmwbM3b',$,$,$,$,$,$,$,$)
~~~

[Sample IDS](fail-invalid_entities_always_fail.ids) - [Sample IFC: #21](fail-invalid_entities_always_fail.ifc)

## [PASS] A matching entity should pass

~~~xml
<entity>
  <name>
    <simpleValue>IFCWALL</simpleValue>
  </name>
</entity>
~~~

~~~lua
#21=IfcWall('19Dy1zb9vEn8A2UywI3XbU',$,$,$,$,$,$,$,$)
~~~

[Sample IDS](pass-a_matching_entity_should_pass.ids) - [Sample IFC: #21](pass-a_matching_entity_should_pass.ifc)

## [PASS] An matching entity should pass regardless of predefined type

~~~xml
<entity>
  <name>
    <simpleValue>IFCWALL</simpleValue>
  </name>
</entity>
~~~

~~~lua
#21=IfcWall('39bSeoj1z2LeVcmDAWOADh',$,$,$,$,$,$,$,.SOLIDWALL.)
~~~

[Sample IDS](pass-an_matching_entity_should_pass_regardless_of_predefined_type.ids) - [Sample IFC: #21](pass-an_matching_entity_should_pass_regardless_of_predefined_type.ifc)

## [FAIL] An entity not matching the specified class should fail

~~~xml
<entity>
  <name>
    <simpleValue>IFCWALL</simpleValue>
  </name>
</entity>
~~~

~~~lua
#21=IfcSlab('17kFWY$E98mwYab8iWWIMB',$,$,$,$,$,$,$,$)
~~~

[Sample IDS](fail-an_entity_not_matching_the_specified_class_should_fail.ids) - [Sample IFC: #21](fail-an_entity_not_matching_the_specified_class_should_fail.ifc)

## [FAIL] Subclasses are not considered as matching

~~~xml
<entity>
  <name>
    <simpleValue>IFCWALL</simpleValue>
  </name>
</entity>
~~~

~~~lua
#21=IfcWallStandardCase('1qBHvPICD45OeZN3Uy8Hfx',$,$,$,$,$,$,$,$)
~~~

[Sample IDS](fail-subclasses_are_not_considered_as_matching.ids) - [Sample IFC: #21](fail-subclasses_are_not_considered_as_matching.ifc)

## [FAIL] Entities must be specified as uppercase strings

~~~xml
<entity>
  <name>
    <simpleValue>IfcWall</simpleValue>
  </name>
</entity>
~~~

~~~lua
#21=IfcWall('3wieaWTZbBCPcpd9vUZu6O',$,$,$,$,$,$,$,$)
~~~

[Sample IDS](fail-entities_must_be_specified_as_uppercase_strings.ids) - [Sample IFC: #21](fail-entities_must_be_specified_as_uppercase_strings.ifc)

## [PASS] A matching predefined type should pass

~~~xml
<entity>
  <name>
    <simpleValue>IFCWALL</simpleValue>
  </name>
  <predefinedType>
    <simpleValue>SOLIDWALL</simpleValue>
  </predefinedType>
</entity>
~~~

~~~lua
#21=IfcWall('14BSfVqfrAEOrMZkxdjvGs',$,$,$,$,$,$,$,.SOLIDWALL.)
~~~

[Sample IDS](pass-a_matching_predefined_type_should_pass.ids) - [Sample IFC: #21](pass-a_matching_predefined_type_should_pass.ifc)

## [FAIL] A null predefined type should always fail a specified predefined types

~~~xml
<entity>
  <name>
    <simpleValue>IFCWALL</simpleValue>
  </name>
  <predefinedType>
    <simpleValue>SOLIDWALL</simpleValue>
  </predefinedType>
</entity>
~~~

~~~lua
#21=IfcWall('2mgvGnnerFmga9LiQlPaJ9',$,$,$,$,$,$,$,$)
~~~

[Sample IDS](fail-a_null_predefined_type_should_always_fail_a_specified_predefined_types.ids) - [Sample IFC: #21](fail-a_null_predefined_type_should_always_fail_a_specified_predefined_types.ifc)

## [FAIL] An entity not matching a specified predefined type will fail

~~~xml
<entity>
  <name>
    <simpleValue>IFCWALL</simpleValue>
  </name>
  <predefinedType>
    <simpleValue>SOLIDWALL</simpleValue>
  </predefinedType>
</entity>
~~~

~~~lua
#21=IfcWall('0bCX0l_uLDE8OLDkfaJhFI',$,$,$,$,$,$,$,.PARTITIONING.)
~~~

[Sample IDS](fail-an_entity_not_matching_a_specified_predefined_type_will_fail.ids) - [Sample IFC: #21](fail-an_entity_not_matching_a_specified_predefined_type_will_fail.ifc)

## [FAIL] A predefined type from an enumeration must be uppercase

~~~xml
<entity>
  <name>
    <simpleValue>IFCWALL</simpleValue>
  </name>
  <predefinedType>
    <simpleValue>solidwall</simpleValue>
  </predefinedType>
</entity>
~~~

~~~lua
#21=IfcWall('2ztVfJRtz9rPp0M7rbCGLb',$,$,$,$,$,$,$,.SOLIDWALL.)
~~~

[Sample IDS](fail-a_predefined_type_from_an_enumeration_must_be_uppercase.ids) - [Sample IFC: #21](fail-a_predefined_type_from_an_enumeration_must_be_uppercase.ifc)

## [PASS] A predefined type may specify a user-defined object type

~~~xml
<entity>
  <name>
    <simpleValue>IFCWALL</simpleValue>
  </name>
  <predefinedType>
    <simpleValue>WALDO</simpleValue>
  </predefinedType>
</entity>
~~~

~~~lua
#21=IfcWall('0JrjMFIhH62xiW1uxPlPkb',$,$,$,'WALDO',$,$,$,.USERDEFINED.)
~~~

[Sample IDS](pass-a_predefined_type_may_specify_a_user_defined_object_type.ids) - [Sample IFC: #21](pass-a_predefined_type_may_specify_a_user_defined_object_type.ifc)

## [FAIL] User-defined types are checked case sensitively

~~~xml
<entity>
  <name>
    <simpleValue>IFCWALL</simpleValue>
  </name>
  <predefinedType>
    <simpleValue>WALDO</simpleValue>
  </predefinedType>
</entity>
~~~

~~~lua
#21=IfcWall('0_14knRKfDdhkP_ZwoDEfa',$,$,$,'waldo',$,$,$,.USERDEFINED.)
~~~

[Sample IDS](fail-user_defined_types_are_checked_case_sensitively.ids) - [Sample IFC: #21](fail-user_defined_types_are_checked_case_sensitively.ifc)

## [PASS] A predefined type may specify a user-defined element type

~~~xml
<entity>
  <name>
    <simpleValue>IFCWALLTYPE</simpleValue>
  </name>
  <predefinedType>
    <simpleValue>WALDO</simpleValue>
  </predefinedType>
</entity>
~~~

~~~lua
#21=IfcWallType('0BxK49pg53BvzRgvMzd470',$,$,$,$,$,$,$,'WALDO',.USERDEFINED.)
~~~

[Sample IDS](pass-a_predefined_type_may_specify_a_user_defined_element_type.ids) - [Sample IFC: #21](pass-a_predefined_type_may_specify_a_user_defined_element_type.ifc)

## [PASS] A predefined type may specify a user-defined process type

~~~xml
<entity>
  <name>
    <simpleValue>IFCTASKTYPE</simpleValue>
  </name>
  <predefinedType>
    <simpleValue>TASKY</simpleValue>
  </predefinedType>
</entity>
~~~

~~~lua
#21=IfcTaskType('0djKIIVPjAMPg$CI9YoDUo',$,$,$,$,$,$,$,'TASKY',.USERDEFINED.,$)
~~~

[Sample IDS](pass-a_predefined_type_may_specify_a_user_defined_process_type.ids) - [Sample IFC: #21](pass-a_predefined_type_may_specify_a_user_defined_process_type.ifc)

## [FAIL] A predefined type must always specify a meaningful type, not USERDEFINED itself

~~~xml
<entity>
  <name>
    <simpleValue>IFCWALL</simpleValue>
  </name>
  <predefinedType>
    <simpleValue>USERDEFINED</simpleValue>
  </predefinedType>
</entity>
~~~

~~~lua
#21=IfcWall('0r2XpgNTv8IQr601Pv1MED',$,$,$,'WALDO',$,$,$,.USERDEFINED.)
~~~

[Sample IDS](fail-a_predefined_type_must_always_specify_a_meaningful_type__not_userdefined_itself.ids) - [Sample IFC: #21](fail-a_predefined_type_must_always_specify_a_meaningful_type__not_userdefined_itself.ifc)

## [PASS] Inherited predefined types should pass

~~~xml
<entity>
  <name>
    <simpleValue>IFCWALL</simpleValue>
  </name>
  <predefinedType>
    <simpleValue>X</simpleValue>
  </predefinedType>
</entity>
~~~

~~~lua
#21=IfcWall('3ZsRjZxobFxhFPN$8XP2i5',$,$,$,$,$,$,$,$)
#23=IfcRelDefinesByType('26LduHf051ofNl3c2S20mO',$,$,$,(#21),#22)
#22=IfcWallType('3GrFMioR1Erg_Y6usDZAxN',$,$,$,$,$,$,$,'X',.USERDEFINED.)
~~~

[Sample IDS](pass-inherited_predefined_types_should_pass.ids) - [Sample IFC: #21](pass-inherited_predefined_types_should_pass.ifc)

## [PASS] Overridden predefined types should pass

~~~xml
<entity>
  <name>
    <simpleValue>IFCWALL</simpleValue>
  </name>
  <predefinedType>
    <simpleValue>X</simpleValue>
  </predefinedType>
</entity>
~~~

~~~lua
#21=IfcWall('0oFPDT3rP5b85Nrij_cEHr',$,$,$,'X',$,$,$,.USERDEFINED.)
#23=IfcRelDefinesByType('0S$r6T5tr1Whog5Y3YHUSa',$,$,$,(#21),#22)
#22=IfcWallType('1YMszkBVv5JxiLoY66U7zT',$,$,$,$,$,$,$,$,.NOTDEFINED.)
~~~

[Sample IDS](pass-overridden_predefined_types_should_pass.ids) - [Sample IFC: #21](pass-overridden_predefined_types_should_pass.ifc)

## [PASS] Entities can be specified as an enumeration 1/3

~~~xml
<entity>
  <name>
    <xs:restriction base="xs:string">
      <xs:enumeration value="IFCWALL"/>
      <xs:enumeration value="IFCSLAB"/>
    </xs:restriction>
  </name>
</entity>
~~~

~~~lua
#21=IfcWall('2k_ysmagn0eOmNc4$o3t5j',$,$,$,$,$,$,$,$)
~~~

[Sample IDS](pass-entities_can_be_specified_as_an_enumeration_1_3.ids) - [Sample IFC: #21](pass-entities_can_be_specified_as_an_enumeration_1_3.ifc)

## [PASS] Entities can be specified as an enumeration 2/3

~~~xml
<entity>
  <name>
    <xs:restriction base="xs:string">
      <xs:enumeration value="IFCWALL"/>
      <xs:enumeration value="IFCSLAB"/>
    </xs:restriction>
  </name>
</entity>
~~~

~~~lua
#21=IfcSlab('0ooHSHpN1BKBOrTqtN9XgK',$,$,$,$,$,$,$,$)
~~~

[Sample IDS](pass-entities_can_be_specified_as_an_enumeration_2_3.ids) - [Sample IFC: #21](pass-entities_can_be_specified_as_an_enumeration_2_3.ifc)

## [FAIL] Entities can be specified as an enumeration 3/3

~~~xml
<entity>
  <name>
    <xs:restriction base="xs:string">
      <xs:enumeration value="IFCWALL"/>
      <xs:enumeration value="IFCSLAB"/>
    </xs:restriction>
  </name>
</entity>
~~~

~~~lua
#21=IfcBeam('2u$PCDpFDEvh8joWX8rTcq',$,$,$,$,$,$,$,$)
~~~

[Sample IDS](fail-entities_can_be_specified_as_an_enumeration_3_3.ids) - [Sample IFC: #21](fail-entities_can_be_specified_as_an_enumeration_3_3.ifc)

## [FAIL] Entities can be specified as a pattern 1/2

~~~xml
<entity>
  <name>
    <xs:restriction base="xs:string">
      <xs:pattern value="IFC.*TYPE"/>
    </xs:restriction>
  </name>
</entity>
~~~

~~~lua
#21=IfcWall('2oqh7k2rH7Jxy5KdRHeO7$',$,$,$,$,$,$,$,$)
~~~

[Sample IDS](fail-entities_can_be_specified_as_a_pattern_1_2.ids) - [Sample IFC: #21](fail-entities_can_be_specified_as_a_pattern_1_2.ifc)

## [PASS] Entities can be specified as a pattern 2/2

~~~xml
<entity>
  <name>
    <xs:restriction base="xs:string">
      <xs:pattern value="IFC.*TYPE"/>
    </xs:restriction>
  </name>
</entity>
~~~

~~~lua
#21=IfcWallType('1s0zBdr9XCyflNF0wPopr4',$,$,$,$,$,$,$,$,.ELEMENTEDWALL.)
~~~

[Sample IDS](pass-entities_can_be_specified_as_a_pattern_2_2.ids) - [Sample IFC: #21](pass-entities_can_be_specified_as_a_pattern_2_2.ifc)

## [PASS] Restrictions an be specified for the predefined type 1/3

~~~xml
<entity>
  <name>
    <simpleValue>IFCWALL</simpleValue>
  </name>
  <predefinedType>
    <xs:restriction base="xs:string">
      <xs:pattern value="FOO.*"/>
    </xs:restriction>
  </predefinedType>
</entity>
~~~

~~~lua
#21=IfcWall('2K$JImEIrAhh6dFIT5_slf',$,$,$,'FOOBAR',$,$,$,.USERDEFINED.)
~~~

[Sample IDS](pass-restrictions_an_be_specified_for_the_predefined_type_1_3.ids) - [Sample IFC: #21](pass-restrictions_an_be_specified_for_the_predefined_type_1_3.ifc)

## [PASS] Restrictions an be specified for the predefined type 2/3

~~~xml
<entity>
  <name>
    <simpleValue>IFCWALL</simpleValue>
  </name>
  <predefinedType>
    <xs:restriction base="xs:string">
      <xs:pattern value="FOO.*"/>
    </xs:restriction>
  </predefinedType>
</entity>
~~~

~~~lua
#21=IfcWall('0gHPNNQBfEzRLAC3GoibZa',$,$,$,'FOOBAZ',$,$,$,.USERDEFINED.)
~~~

[Sample IDS](pass-restrictions_an_be_specified_for_the_predefined_type_2_3.ids) - [Sample IFC: #21](pass-restrictions_an_be_specified_for_the_predefined_type_2_3.ifc)

## [FAIL] Restrictions an be specified for the predefined type 3/3

~~~xml
<entity>
  <name>
    <simpleValue>IFCWALL</simpleValue>
  </name>
  <predefinedType>
    <xs:restriction base="xs:string">
      <xs:pattern value="FOO.*"/>
    </xs:restriction>
  </predefinedType>
</entity>
~~~

~~~lua
#21=IfcWall('1uO2ycSSjFW9ixlzWIaUBo',$,$,$,'BAZFOO',$,$,$,.USERDEFINED.)
~~~

[Sample IDS](fail-restrictions_an_be_specified_for_the_predefined_type_3_3.ids) - [Sample IFC: #21](fail-restrictions_an_be_specified_for_the_predefined_type_3_3.ifc)
