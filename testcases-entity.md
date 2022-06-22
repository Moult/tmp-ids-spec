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
#1=IFCWALL('0PN66raHH4QQ1g$6zEGrRU',$,$,$,$,$,$,$,$); /* Testcase */
~~~

[Sample IDS](fail-invalid_entities_always_fail.ids) - [Sample IFC: 1](fail-invalid_entities_always_fail.ifc)

## [PASS] A matching entity should pass

~~~xml
<entity>
  <name>
    <simpleValue>IFCWALL</simpleValue>
  </name>
</entity>
~~~

~~~lua
#1=IFCWALL('1aR5Hnwcz98OES8HsBjdSG',$,$,$,$,$,$,$,$); /* Testcase */
~~~

[Sample IDS](pass-a_matching_entity_should_pass.ids) - [Sample IFC: 1](pass-a_matching_entity_should_pass.ifc)

## [PASS] An matching entity should pass regardless of predefined type

~~~xml
<entity>
  <name>
    <simpleValue>IFCWALL</simpleValue>
  </name>
</entity>
~~~

~~~lua
#1=IFCWALL('1hle$JuvfBpAV2if17caId',$,$,$,$,$,$,$,.SOLIDWALL.); /* Testcase */
~~~

[Sample IDS](pass-an_matching_entity_should_pass_regardless_of_predefined_type.ids) - [Sample IFC: 1](pass-an_matching_entity_should_pass_regardless_of_predefined_type.ifc)

## [FAIL] An entity not matching the specified class should fail

~~~xml
<entity>
  <name>
    <simpleValue>IFCWALL</simpleValue>
  </name>
</entity>
~~~

~~~lua
#1=IFCSLAB('2oTmJMZhDEsfN6jMl0vh4m',$,$,$,$,$,$,$,$); /* Testcase */
~~~

[Sample IDS](fail-an_entity_not_matching_the_specified_class_should_fail.ids) - [Sample IFC: 1](fail-an_entity_not_matching_the_specified_class_should_fail.ifc)

## [FAIL] Subclasses are not considered as matching

~~~xml
<entity>
  <name>
    <simpleValue>IFCWALL</simpleValue>
  </name>
</entity>
~~~

~~~lua
#1=IFCWALLSTANDARDCASE('3fmNQdmkH1T82kcVuxDl1D',$,$,$,$,$,$,$,$); /* Testcase */
~~~

[Sample IDS](fail-subclasses_are_not_considered_as_matching.ids) - [Sample IFC: 1](fail-subclasses_are_not_considered_as_matching.ifc)

## [FAIL] Entities must be specified as uppercase strings

~~~xml
<entity>
  <name>
    <simpleValue>IfcWall</simpleValue>
  </name>
</entity>
~~~

~~~lua
#1=IFCWALL('0$sTjqhFX3lhre0RoDE16J',$,$,$,$,$,$,$,$); /* Testcase */
~~~

[Sample IDS](fail-entities_must_be_specified_as_uppercase_strings.ids) - [Sample IFC: 1](fail-entities_must_be_specified_as_uppercase_strings.ifc)

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
#1=IFCWALL('2Hl5xImwXDLOXfUVghElTR',$,$,$,$,$,$,$,.SOLIDWALL.); /* Testcase */
~~~

[Sample IDS](pass-a_matching_predefined_type_should_pass.ids) - [Sample IFC: 1](pass-a_matching_predefined_type_should_pass.ifc)

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
#1=IFCWALL('1NKsCXcmv0$Ao6_9NSlpjG',$,$,$,$,$,$,$,$); /* Testcase */
~~~

[Sample IDS](fail-a_null_predefined_type_should_always_fail_a_specified_predefined_types.ids) - [Sample IFC: 1](fail-a_null_predefined_type_should_always_fail_a_specified_predefined_types.ifc)

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
#1=IFCWALL('1FtvA_VyH5v9_45ykOQxof',$,$,$,$,$,$,$,.PARTITIONING.); /* Testcase */
~~~

[Sample IDS](fail-an_entity_not_matching_a_specified_predefined_type_will_fail.ids) - [Sample IFC: 1](fail-an_entity_not_matching_a_specified_predefined_type_will_fail.ifc)

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
#1=IFCWALL('1UukhMMhX7wP88EGcOeBby',$,$,$,$,$,$,$,.SOLIDWALL.); /* Testcase */
~~~

[Sample IDS](fail-a_predefined_type_from_an_enumeration_must_be_uppercase.ids) - [Sample IFC: 1](fail-a_predefined_type_from_an_enumeration_must_be_uppercase.ifc)

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
#1=IFCWALL('0lop$i0an22hC0GFtfkRQe',$,$,$,'WALDO',$,$,$,.USERDEFINED.); /* Testcase */
~~~

[Sample IDS](pass-a_predefined_type_may_specify_a_user_defined_object_type.ids) - [Sample IFC: 1](pass-a_predefined_type_may_specify_a_user_defined_object_type.ifc)

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
#1=IFCWALL('3Rdm1JzOH2vvg59Tfi$Tyl',$,$,$,'waldo',$,$,$,.USERDEFINED.); /* Testcase */
~~~

[Sample IDS](fail-user_defined_types_are_checked_case_sensitively.ids) - [Sample IFC: 1](fail-user_defined_types_are_checked_case_sensitively.ifc)

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
#1=IFCWALLTYPE('0OXXtCYYbAQP9mrN_CnIKe',$,$,$,$,$,$,$,'WALDO',.USERDEFINED.); /* Testcase */
~~~

[Sample IDS](pass-a_predefined_type_may_specify_a_user_defined_element_type.ids) - [Sample IFC: 1](pass-a_predefined_type_may_specify_a_user_defined_element_type.ifc)

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
#1=IFCTASKTYPE('31wzn1tiP7vh7$fnZojOsg',$,$,$,$,$,$,$,'TASKY',.USERDEFINED.,$); /* Testcase */
~~~

[Sample IDS](pass-a_predefined_type_may_specify_a_user_defined_process_type.ids) - [Sample IFC: 1](pass-a_predefined_type_may_specify_a_user_defined_process_type.ifc)

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
#1=IFCWALL('29XOgfwprC$B9YVqonvU4_',$,$,$,'WALDO',$,$,$,.USERDEFINED.); /* Testcase */
~~~

[Sample IDS](fail-a_predefined_type_must_always_specify_a_meaningful_type__not_userdefined_itself.ids) - [Sample IFC: 1](fail-a_predefined_type_must_always_specify_a_meaningful_type__not_userdefined_itself.ifc)

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
#1=IFCWALL('2ERMTIzsL7Lv5n4IjG0fWg',$,$,$,$,$,$,$,$); /* Testcase */
#2=IFCWALLTYPE('1wrVkTQIL0PO34wIeg9lmQ',$,$,$,$,$,$,$,'X',.USERDEFINED.);
#3=IFCRELDEFINESBYTYPE('2wKaA4Ykb6lRo6ytiBOb0d',$,$,$,(#1),#2);
~~~

[Sample IDS](pass-inherited_predefined_types_should_pass.ids) - [Sample IFC: 1](pass-inherited_predefined_types_should_pass.ifc)

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
#1=IFCWALL('3pd6qLf7z2t8VMwKxx26Qg',$,$,$,'X',$,$,$,.USERDEFINED.); /* Testcase */
#2=IFCWALLTYPE('2qs3jH$lzC8vxg$isYkC6C',$,$,$,$,$,$,$,$,.NOTDEFINED.);
#3=IFCRELDEFINESBYTYPE('0ZtwWfPGXEL85XS7gFcCGg',$,$,$,(#1),#2);
~~~

[Sample IDS](pass-overridden_predefined_types_should_pass.ids) - [Sample IFC: 1](pass-overridden_predefined_types_should_pass.ifc)

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
#1=IFCWALL('0tSzdGkKb89htb2XjPEbxA',$,$,$,$,$,$,$,$); /* Testcase */
~~~

[Sample IDS](pass-entities_can_be_specified_as_an_enumeration_1_3.ids) - [Sample IFC: 1](pass-entities_can_be_specified_as_an_enumeration_1_3.ifc)

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
#1=IFCSLAB('1iyN6FMOP7GwbozUuU42m0',$,$,$,$,$,$,$,$); /* Testcase */
~~~

[Sample IDS](pass-entities_can_be_specified_as_an_enumeration_2_3.ids) - [Sample IFC: 1](pass-entities_can_be_specified_as_an_enumeration_2_3.ifc)

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
#1=IFCBEAM('2bBUe2R0b9dvOpCnq_Qfkm',$,$,$,$,$,$,$,$); /* Testcase */
~~~

[Sample IDS](fail-entities_can_be_specified_as_an_enumeration_3_3.ids) - [Sample IFC: 1](fail-entities_can_be_specified_as_an_enumeration_3_3.ifc)

## [FAIL] Entities can be specified as a XSD regex pattern 1/2

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
#1=IFCWALL('23RVloAM566P_TmX4fYS_M',$,$,$,$,$,$,$,$); /* Testcase */
~~~

[Sample IDS](fail-entities_can_be_specified_as_a_xsd_regex_pattern_1_2.ids) - [Sample IFC: 1](fail-entities_can_be_specified_as_a_xsd_regex_pattern_1_2.ifc)

## [PASS] Entities can be specified as a XSD regex pattern 2/2

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
#1=IFCWALLTYPE('19v0GfRDD2UPa5aSDxsRTZ',$,$,$,$,$,$,$,$,.ELEMENTEDWALL.); /* Testcase */
~~~

[Sample IDS](pass-entities_can_be_specified_as_a_xsd_regex_pattern_2_2.ids) - [Sample IFC: 1](pass-entities_can_be_specified_as_a_xsd_regex_pattern_2_2.ifc)

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
#1=IFCWALL('3_26sgRW96r8d$iSmhzJFh',$,$,$,'FOOBAR',$,$,$,.USERDEFINED.); /* Testcase */
~~~

[Sample IDS](pass-restrictions_an_be_specified_for_the_predefined_type_1_3.ids) - [Sample IFC: 1](pass-restrictions_an_be_specified_for_the_predefined_type_1_3.ifc)

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
#1=IFCWALL('2lcbUouZ93U9bunLnnaGJ$',$,$,$,'FOOBAZ',$,$,$,.USERDEFINED.); /* Testcase */
~~~

[Sample IDS](pass-restrictions_an_be_specified_for_the_predefined_type_2_3.ids) - [Sample IFC: 1](pass-restrictions_an_be_specified_for_the_predefined_type_2_3.ifc)

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
#1=IFCWALL('1m9oC3eIX7Og9Jx6gVeY83',$,$,$,'BAZFOO',$,$,$,.USERDEFINED.); /* Testcase */
~~~

[Sample IDS](fail-restrictions_an_be_specified_for_the_predefined_type_3_3.ids) - [Sample IFC: 1](fail-restrictions_an_be_specified_for_the_predefined_type_3_3.ifc)
