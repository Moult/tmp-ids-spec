# Classification testcases

These testcases are designed to help describe behaviour in edge cases and ambiguities. All valid IDS implementations must demonstrate identical behaviour to these test cases.

## [FAIL] A classification facet with no data matches any classification 1/2

~~~xml
<classification minOccurs="1" maxOccurs="1"/>
~~~

~~~lua
#21=IfcWall('0K1ESAyqH1FR7p9ul1ianU',$,$,$,$,$,$,$,$)
~~~

[Sample IDS](fail-a_classification_facet_with_no_data_matches_any_classification_1_2.ids) - [Sample IFC: #21](fail-a_classification_facet_with_no_data_matches_any_classification_1_2.ifc)

## [PASS] A classification facet with no data matches any classification 2/2

~~~xml
<classification minOccurs="1" maxOccurs="1"/>
~~~

~~~lua
#21=IfcWall('0OAgBQTuvEzwOjEU89L2LV',$,$,$,$,$,$,$,$)
#24=IfcRelAssociatesClassification('2L0EZNmXL2FweMpcNfccIi',$,$,$,(#21),#23)
#23=IfcClassificationReference($,'1',$,#22,$,$)
#22=IfcClassification($,$,$,'Foobar',$,$,$)
~~~

[Sample IDS](pass-a_classification_facet_with_no_data_matches_any_classification_2_2.ids) - [Sample IFC: #21](pass-a_classification_facet_with_no_data_matches_any_classification_2_2.ifc)

## [PASS] Values should match exactly if lightweight classifications are used

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>1</simpleValue>
  </value>
</classification>
~~~

~~~lua
#21=IfcWall('0OAgBQTuvEzwOjEU89L2LV',$,$,$,$,$,$,$,$)
#24=IfcRelAssociatesClassification('2L0EZNmXL2FweMpcNfccIi',$,$,$,(#21),#23)
#23=IfcClassificationReference($,'1',$,#22,$,$)
#22=IfcClassification($,$,$,'Foobar',$,$,$)
~~~

[Sample IDS](pass-values_should_match_exactly_if_lightweight_classifications_are_used.ids) - [Sample IFC: #21](pass-values_should_match_exactly_if_lightweight_classifications_are_used.ifc)

## [PASS] Values match subreferences if full classifications are used (e.g. EF_25_10 should match EF_25_10_25, EF_25_10_30, etc)

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>2</simpleValue>
  </value>
</classification>
~~~

~~~lua
#21=IfcWall('0SwE5yiRLAXfeGg0VwWLEO',$,$,$,$,$,$,$,$)
#25=IfcRelAssociatesClassification('3kHvsEPW97v8XAPTZ$lpu_',$,$,$,(#21),#24)
#24=IfcClassificationReference($,'22',$,#23,$,$)
#23=IfcClassificationReference($,'2',$,#22,$,$)
#22=IfcClassification($,$,$,'Foobar',$,$,$)
~~~

[Sample IDS](pass-values_match_subreferences_if_full_classifications_are_used__e_g__ef_25_10_should_match_ef_25_10_25__ef_25_10_30__etc_.ids) - [Sample IFC: #21](pass-values_match_subreferences_if_full_classifications_are_used__e_g__ef_25_10_should_match_ef_25_10_25__ef_25_10_30__etc_.ifc)

## [PASS] Systems should match exactly 1/5

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <system>
    <simpleValue>Foobar</simpleValue>
  </system>
</classification>
~~~

~~~lua
#21=IfcProject('2yropMsfP3VgLt9dA6He8L',$,$,$,$,$,$,$,$)
#23=IfcRelAssociatesClassification('04on08_3b8HhWg3FkKmjuv',$,$,$,(#21),#22)
#22=IfcClassification($,$,$,'Foobar',$,$,$)
~~~

[Sample IDS](pass-systems_should_match_exactly_1_5.ids) - [Sample IFC: #21](pass-systems_should_match_exactly_1_5.ifc)

## [FAIL] Systems should match exactly 2/5

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <system>
    <simpleValue>Foobar</simpleValue>
  </system>
</classification>
~~~

~~~lua
#21=IfcWall('0K1ESAyqH1FR7p9ul1ianU',$,$,$,$,$,$,$,$)
~~~

[Sample IDS](fail-systems_should_match_exactly_2_5.ids) - [Sample IFC: #21](fail-systems_should_match_exactly_2_5.ifc)

## [PASS] Systems should match exactly 3/5

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <system>
    <simpleValue>Foobar</simpleValue>
  </system>
</classification>
~~~

~~~lua
#21=IfcWall('0OAgBQTuvEzwOjEU89L2LV',$,$,$,$,$,$,$,$)
#24=IfcRelAssociatesClassification('2L0EZNmXL2FweMpcNfccIi',$,$,$,(#21),#23)
#23=IfcClassificationReference($,'1',$,#22,$,$)
#22=IfcClassification($,$,$,'Foobar',$,$,$)
~~~

[Sample IDS](pass-systems_should_match_exactly_3_5.ids) - [Sample IFC: #21](pass-systems_should_match_exactly_3_5.ifc)

## [PASS] Systems should match exactly 4/5

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <system>
    <simpleValue>Foobar</simpleValue>
  </system>
</classification>
~~~

~~~lua
#21=IfcWall('1MzlH8RWbE4OEOhF8QP7i5',$,$,$,$,$,$,$,$)
#24=IfcRelAssociatesClassification('30kAc63Db5b9ZgqVx$3MRW',$,$,$,(#21),#23)
#23=IfcClassificationReference($,'11',$,#22,$,$)
#22=IfcClassification($,$,$,'Foobar',$,$,$)
~~~

[Sample IDS](pass-systems_should_match_exactly_4_5.ids) - [Sample IFC: #21](pass-systems_should_match_exactly_4_5.ifc)

## [PASS] Systems should match exactly 5/5

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <system>
    <simpleValue>Foobar</simpleValue>
  </system>
</classification>
~~~

~~~lua
#21=IfcWall('0SwE5yiRLAXfeGg0VwWLEO',$,$,$,$,$,$,$,$)
#25=IfcRelAssociatesClassification('3kHvsEPW97v8XAPTZ$lpu_',$,$,$,(#21),#24)
#24=IfcClassificationReference($,'22',$,#23,$,$)
#23=IfcClassificationReference($,'2',$,#22,$,$)
#22=IfcClassification($,$,$,'Foobar',$,$,$)
~~~

[Sample IDS](pass-systems_should_match_exactly_5_5.ids) - [Sample IFC: #21](pass-systems_should_match_exactly_5_5.ifc)

## [PASS] Restrictions can be used for values 1/3

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <value>
    <xs:restriction base="xs:string">
      <xs:pattern value="1.*"/>
    </xs:restriction>
  </value>
</classification>
~~~

~~~lua
#21=IfcWall('0OAgBQTuvEzwOjEU89L2LV',$,$,$,$,$,$,$,$)
#24=IfcRelAssociatesClassification('2L0EZNmXL2FweMpcNfccIi',$,$,$,(#21),#23)
#23=IfcClassificationReference($,'1',$,#22,$,$)
#22=IfcClassification($,$,$,'Foobar',$,$,$)
~~~

[Sample IDS](pass-restrictions_can_be_used_for_values_1_3.ids) - [Sample IFC: #21](pass-restrictions_can_be_used_for_values_1_3.ifc)

## [PASS] Restrictions can be used for values 2/3

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <value>
    <xs:restriction base="xs:string">
      <xs:pattern value="1.*"/>
    </xs:restriction>
  </value>
</classification>
~~~

~~~lua
#21=IfcWall('1MzlH8RWbE4OEOhF8QP7i5',$,$,$,$,$,$,$,$)
#24=IfcRelAssociatesClassification('30kAc63Db5b9ZgqVx$3MRW',$,$,$,(#21),#23)
#23=IfcClassificationReference($,'11',$,#22,$,$)
#22=IfcClassification($,$,$,'Foobar',$,$,$)
~~~

[Sample IDS](pass-restrictions_can_be_used_for_values_2_3.ids) - [Sample IFC: #21](pass-restrictions_can_be_used_for_values_2_3.ifc)

## [FAIL] Restrictions can be used for values 3/3

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <value>
    <xs:restriction base="xs:string">
      <xs:pattern value="1.*"/>
    </xs:restriction>
  </value>
</classification>
~~~

~~~lua
#21=IfcWall('0SwE5yiRLAXfeGg0VwWLEO',$,$,$,$,$,$,$,$)
#25=IfcRelAssociatesClassification('3kHvsEPW97v8XAPTZ$lpu_',$,$,$,(#21),#24)
#24=IfcClassificationReference($,'22',$,#23,$,$)
#23=IfcClassificationReference($,'2',$,#22,$,$)
#22=IfcClassification($,$,$,'Foobar',$,$,$)
~~~

[Sample IDS](fail-restrictions_can_be_used_for_values_3_3.ids) - [Sample IFC: #21](fail-restrictions_can_be_used_for_values_3_3.ifc)

## [FAIL] Restrictions can be used for systems 1/2

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <system>
    <xs:restriction base="xs:string">
      <xs:pattern value="Foo.*"/>
    </xs:restriction>
  </system>
</classification>
~~~

~~~lua
#21=IfcWall('0K1ESAyqH1FR7p9ul1ianU',$,$,$,$,$,$,$,$)
~~~

[Sample IDS](fail-restrictions_can_be_used_for_systems_1_2.ids) - [Sample IFC: #21](fail-restrictions_can_be_used_for_systems_1_2.ifc)

## [PASS] Restrictions can be used for systems 2/2

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <system>
    <xs:restriction base="xs:string">
      <xs:pattern value="Foo.*"/>
    </xs:restriction>
  </system>
</classification>
~~~

~~~lua
#21=IfcWall('0OAgBQTuvEzwOjEU89L2LV',$,$,$,$,$,$,$,$)
#24=IfcRelAssociatesClassification('2L0EZNmXL2FweMpcNfccIi',$,$,$,(#21),#23)
#23=IfcClassificationReference($,'1',$,#22,$,$)
#22=IfcClassification($,$,$,'Foobar',$,$,$)
~~~

[Sample IDS](pass-restrictions_can_be_used_for_systems_2_2.ids) - [Sample IFC: #21](pass-restrictions_can_be_used_for_systems_2_2.ifc)

## [PASS] Both system and value must match (all, not any) if specified 1/2

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>1</simpleValue>
  </value>
  <system>
    <simpleValue>Foobar</simpleValue>
  </system>
</classification>
~~~

~~~lua
#21=IfcWall('0OAgBQTuvEzwOjEU89L2LV',$,$,$,$,$,$,$,$)
#24=IfcRelAssociatesClassification('2L0EZNmXL2FweMpcNfccIi',$,$,$,(#21),#23)
#23=IfcClassificationReference($,'1',$,#22,$,$)
#22=IfcClassification($,$,$,'Foobar',$,$,$)
~~~

[Sample IDS](pass-both_system_and_value_must_match__all__not_any__if_specified_1_2.ids) - [Sample IFC: #21](pass-both_system_and_value_must_match__all__not_any__if_specified_1_2.ifc)

## [FAIL] Both system and value must match (all, not any) if specified 2/2

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>1</simpleValue>
  </value>
  <system>
    <simpleValue>Foobar</simpleValue>
  </system>
</classification>
~~~

~~~lua
#21=IfcWall('1MzlH8RWbE4OEOhF8QP7i5',$,$,$,$,$,$,$,$)
#24=IfcRelAssociatesClassification('30kAc63Db5b9ZgqVx$3MRW',$,$,$,(#21),#23)
#23=IfcClassificationReference($,'11',$,#22,$,$)
#22=IfcClassification($,$,$,'Foobar',$,$,$)
~~~

[Sample IDS](fail-both_system_and_value_must_match__all__not_any__if_specified_2_2.ids) - [Sample IFC: #21](fail-both_system_and_value_must_match__all__not_any__if_specified_2_2.ifc)

## [PASS] Occurrences override the type classification per system 1/3

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>11</simpleValue>
  </value>
</classification>
~~~

~~~lua
#21=IfcWall('1MNOaqZdDDOh8sh_3KMOmt',$,$,$,$,$,$,$,$)
#25=IfcRelAssociatesClassification('30kAc63Db5b9ZgqVx$3MRW',$,$,$,(#22,#21),#24)
#22=IfcWall('1MzlH8RWbE4OEOhF8QP7i5',$,$,$,$,$,$,$,$)
#24=IfcClassificationReference($,'11',$,#23,$,$)
#23=IfcClassification($,$,$,'Foobar',$,$,$)
#27=IfcRelDefinesByType('0qTEjyemvFTfbEZRmY1cBx',$,$,$,(#21),#26)
#26=IfcWallType('1wv6TyY8b6_x_5CLq316t9',$,$,$,$,$,$,$,$,.ELEMENTEDWALL.)
~~~

[Sample IDS](pass-occurrences_override_the_type_classification_per_system_1_3.ids) - [Sample IFC: #21](pass-occurrences_override_the_type_classification_per_system_1_3.ifc)

## [FAIL] Occurrences override the type classification per system 2/3

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>22</simpleValue>
  </value>
</classification>
~~~

~~~lua
#21=IfcWall('1MNOaqZdDDOh8sh_3KMOmt',$,$,$,$,$,$,$,$)
#25=IfcRelAssociatesClassification('30kAc63Db5b9ZgqVx$3MRW',$,$,$,(#22,#21),#24)
#22=IfcWall('1MzlH8RWbE4OEOhF8QP7i5',$,$,$,$,$,$,$,$)
#24=IfcClassificationReference($,'11',$,#23,$,$)
#23=IfcClassification($,$,$,'Foobar',$,$,$)
#27=IfcRelDefinesByType('0qTEjyemvFTfbEZRmY1cBx',$,$,$,(#21),#26)
#26=IfcWallType('1wv6TyY8b6_x_5CLq316t9',$,$,$,$,$,$,$,$,.ELEMENTEDWALL.)
~~~

[Sample IDS](fail-occurrences_override_the_type_classification_per_system_2_3.ids) - [Sample IFC: #21](fail-occurrences_override_the_type_classification_per_system_2_3.ifc)

## [PASS] Occurrences override the type classification per system 3/3

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>X</simpleValue>
  </value>
</classification>
~~~

~~~lua
#21=IfcWall('1MNOaqZdDDOh8sh_3KMOmt',$,$,$,$,$,$,$,$)
#25=IfcRelAssociatesClassification('30kAc63Db5b9ZgqVx$3MRW',$,$,$,(#22,#21),#24)
#22=IfcWall('1MzlH8RWbE4OEOhF8QP7i5',$,$,$,$,$,$,$,$)
#24=IfcClassificationReference($,'11',$,#23,$,$)
#23=IfcClassification($,$,$,'Foobar',$,$,$)
#27=IfcRelDefinesByType('0qTEjyemvFTfbEZRmY1cBx',$,$,$,(#21),#26)
#26=IfcWallType('1wv6TyY8b6_x_5CLq316t9',$,$,$,$,$,$,$,$,.ELEMENTEDWALL.)
~~~

[Sample IDS](pass-occurrences_override_the_type_classification_per_system_3_3.ids) - [Sample IFC: #21](pass-occurrences_override_the_type_classification_per_system_3_3.ifc)
