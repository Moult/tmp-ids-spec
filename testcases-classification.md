# Classification testcases

These testcases are designed to help describe behaviour in edge cases and ambiguities. All valid IDS implementations must demonstrate identical behaviour to these test cases.

## [FAIL] A classification facet with no data matches any classification 1/2

~~~xml
<classification minOccurs="1" maxOccurs="1"/>
~~~

~~~lua
#1=IFCPROJECT('09waczB0TB$hP3cVMWKh6v',$,$,$,$,$,$,$,$);
#2=IFCCLASSIFICATION($,$,$,'Foobar',$,$,$);
#3=IFCRELASSOCIATESCLASSIFICATION('0fShJTRKP9SPlVzqIn__dg',$,$,$,(#1),#2);
#4=IFCWALL('1Ev6VPwkb8DxG$KvUQ61Tj',$,$,$,$,$,$,$,$); /* Testcase */
#5=IFCWALL('3IpqHJLorDWOMZfkAsnFyj',$,$,$,$,$,$,$,$);
#6=IFCCLASSIFICATIONREFERENCE($,'1',$,#2,$,$);
#7=IFCRELASSOCIATESCLASSIFICATION('0ySnj2nlzA1PPRHJQQKB8o',$,$,$,(#5),#6);
#8=IFCWALL('3z07og1cf0tRksLXTFwrha',$,$,$,$,$,$,$,$);
#9=IFCCLASSIFICATIONREFERENCE($,'11',$,#2,$,$);
#10=IFCRELASSOCIATESCLASSIFICATION('3r2bqqaZXEE9_leqfSfwZw',$,$,$,(#8),#9);
#11=IFCWALL('3$KOb38H15zuNJocC0Evl1',$,$,$,$,$,$,$,$);
#12=IFCCLASSIFICATIONREFERENCE($,'22',$,#13,$,$);
#13=IFCCLASSIFICATIONREFERENCE($,'2',$,#2,$,$);
#15=IFCRELASSOCIATESCLASSIFICATION('3BndngXerCqR2YTUUqxbaP',$,$,$,(#11),#12);
~~~

[Sample IDS](fail-a_classification_facet_with_no_data_matches_any_classification_1_2.ids) - [Sample IFC: 4](fail-a_classification_facet_with_no_data_matches_any_classification_1_2.ifc)

## [PASS] A classification facet with no data matches any classification 2/2

~~~xml
<classification minOccurs="1" maxOccurs="1"/>
~~~

~~~lua
#1=IFCPROJECT('09waczB0TB$hP3cVMWKh6v',$,$,$,$,$,$,$,$);
#2=IFCCLASSIFICATION($,$,$,'Foobar',$,$,$);
#3=IFCRELASSOCIATESCLASSIFICATION('0fShJTRKP9SPlVzqIn__dg',$,$,$,(#1),#2);
#4=IFCWALL('1Ev6VPwkb8DxG$KvUQ61Tj',$,$,$,$,$,$,$,$);
#5=IFCWALL('3IpqHJLorDWOMZfkAsnFyj',$,$,$,$,$,$,$,$); /* Testcase */
#6=IFCCLASSIFICATIONREFERENCE($,'1',$,#2,$,$);
#7=IFCRELASSOCIATESCLASSIFICATION('0ySnj2nlzA1PPRHJQQKB8o',$,$,$,(#5),#6);
#8=IFCWALL('3z07og1cf0tRksLXTFwrha',$,$,$,$,$,$,$,$);
#9=IFCCLASSIFICATIONREFERENCE($,'11',$,#2,$,$);
#10=IFCRELASSOCIATESCLASSIFICATION('3r2bqqaZXEE9_leqfSfwZw',$,$,$,(#8),#9);
#11=IFCWALL('3$KOb38H15zuNJocC0Evl1',$,$,$,$,$,$,$,$);
#12=IFCCLASSIFICATIONREFERENCE($,'22',$,#13,$,$);
#13=IFCCLASSIFICATIONREFERENCE($,'2',$,#2,$,$);
#15=IFCRELASSOCIATESCLASSIFICATION('3BndngXerCqR2YTUUqxbaP',$,$,$,(#11),#12);
~~~

[Sample IDS](pass-a_classification_facet_with_no_data_matches_any_classification_2_2.ids) - [Sample IFC: 5](pass-a_classification_facet_with_no_data_matches_any_classification_2_2.ifc)

## [PASS] Values should match exactly if lightweight classifications are used

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>1</simpleValue>
  </value>
</classification>
~~~

~~~lua
#1=IFCPROJECT('09waczB0TB$hP3cVMWKh6v',$,$,$,$,$,$,$,$);
#2=IFCCLASSIFICATION($,$,$,'Foobar',$,$,$);
#3=IFCRELASSOCIATESCLASSIFICATION('0fShJTRKP9SPlVzqIn__dg',$,$,$,(#1),#2);
#4=IFCWALL('1Ev6VPwkb8DxG$KvUQ61Tj',$,$,$,$,$,$,$,$);
#5=IFCWALL('3IpqHJLorDWOMZfkAsnFyj',$,$,$,$,$,$,$,$); /* Testcase */
#6=IFCCLASSIFICATIONREFERENCE($,'1',$,#2,$,$);
#7=IFCRELASSOCIATESCLASSIFICATION('0ySnj2nlzA1PPRHJQQKB8o',$,$,$,(#5),#6);
#8=IFCWALL('3z07og1cf0tRksLXTFwrha',$,$,$,$,$,$,$,$);
#9=IFCCLASSIFICATIONREFERENCE($,'11',$,#2,$,$);
#10=IFCRELASSOCIATESCLASSIFICATION('3r2bqqaZXEE9_leqfSfwZw',$,$,$,(#8),#9);
#11=IFCWALL('3$KOb38H15zuNJocC0Evl1',$,$,$,$,$,$,$,$);
#12=IFCCLASSIFICATIONREFERENCE($,'22',$,#13,$,$);
#13=IFCCLASSIFICATIONREFERENCE($,'2',$,#2,$,$);
#15=IFCRELASSOCIATESCLASSIFICATION('3BndngXerCqR2YTUUqxbaP',$,$,$,(#11),#12);
~~~

[Sample IDS](pass-values_should_match_exactly_if_lightweight_classifications_are_used.ids) - [Sample IFC: 5](pass-values_should_match_exactly_if_lightweight_classifications_are_used.ifc)

## [PASS] Values match subreferences if full classifications are used (e.g. EF_25_10 should match EF_25_10_25, EF_25_10_30, etc)

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>2</simpleValue>
  </value>
</classification>
~~~

~~~lua
#1=IFCPROJECT('09waczB0TB$hP3cVMWKh6v',$,$,$,$,$,$,$,$);
#2=IFCCLASSIFICATION($,$,$,'Foobar',$,$,$);
#3=IFCRELASSOCIATESCLASSIFICATION('0fShJTRKP9SPlVzqIn__dg',$,$,$,(#1),#2);
#4=IFCWALL('1Ev6VPwkb8DxG$KvUQ61Tj',$,$,$,$,$,$,$,$);
#5=IFCWALL('3IpqHJLorDWOMZfkAsnFyj',$,$,$,$,$,$,$,$);
#6=IFCCLASSIFICATIONREFERENCE($,'1',$,#2,$,$);
#7=IFCRELASSOCIATESCLASSIFICATION('0ySnj2nlzA1PPRHJQQKB8o',$,$,$,(#5),#6);
#8=IFCWALL('3z07og1cf0tRksLXTFwrha',$,$,$,$,$,$,$,$);
#9=IFCCLASSIFICATIONREFERENCE($,'11',$,#2,$,$);
#10=IFCRELASSOCIATESCLASSIFICATION('3r2bqqaZXEE9_leqfSfwZw',$,$,$,(#8),#9);
#11=IFCWALL('3$KOb38H15zuNJocC0Evl1',$,$,$,$,$,$,$,$); /* Testcase */
#12=IFCCLASSIFICATIONREFERENCE($,'22',$,#13,$,$);
#13=IFCCLASSIFICATIONREFERENCE($,'2',$,#2,$,$);
#15=IFCRELASSOCIATESCLASSIFICATION('3BndngXerCqR2YTUUqxbaP',$,$,$,(#11),#12);
~~~

[Sample IDS](pass-values_match_subreferences_if_full_classifications_are_used__e_g__ef_25_10_should_match_ef_25_10_25__ef_25_10_30__etc_.ids) - [Sample IFC: 11](pass-values_match_subreferences_if_full_classifications_are_used__e_g__ef_25_10_should_match_ef_25_10_25__ef_25_10_30__etc_.ifc)

## [PASS] Systems should match exactly 1/5

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <system>
    <simpleValue>Foobar</simpleValue>
  </system>
</classification>
~~~

~~~lua
#1=IFCPROJECT('09waczB0TB$hP3cVMWKh6v',$,$,$,$,$,$,$,$); /* Testcase */
#2=IFCCLASSIFICATION($,$,$,'Foobar',$,$,$);
#3=IFCRELASSOCIATESCLASSIFICATION('0fShJTRKP9SPlVzqIn__dg',$,$,$,(#1),#2);
#4=IFCWALL('1Ev6VPwkb8DxG$KvUQ61Tj',$,$,$,$,$,$,$,$);
#5=IFCWALL('3IpqHJLorDWOMZfkAsnFyj',$,$,$,$,$,$,$,$);
#6=IFCCLASSIFICATIONREFERENCE($,'1',$,#2,$,$);
#7=IFCRELASSOCIATESCLASSIFICATION('0ySnj2nlzA1PPRHJQQKB8o',$,$,$,(#5),#6);
#8=IFCWALL('3z07og1cf0tRksLXTFwrha',$,$,$,$,$,$,$,$);
#9=IFCCLASSIFICATIONREFERENCE($,'11',$,#2,$,$);
#10=IFCRELASSOCIATESCLASSIFICATION('3r2bqqaZXEE9_leqfSfwZw',$,$,$,(#8),#9);
#11=IFCWALL('3$KOb38H15zuNJocC0Evl1',$,$,$,$,$,$,$,$);
#12=IFCCLASSIFICATIONREFERENCE($,'22',$,#13,$,$);
#13=IFCCLASSIFICATIONREFERENCE($,'2',$,#2,$,$);
#15=IFCRELASSOCIATESCLASSIFICATION('3BndngXerCqR2YTUUqxbaP',$,$,$,(#11),#12);
~~~

[Sample IDS](pass-systems_should_match_exactly_1_5.ids) - [Sample IFC: 1](pass-systems_should_match_exactly_1_5.ifc)

## [FAIL] Systems should match exactly 2/5

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <system>
    <simpleValue>Foobar</simpleValue>
  </system>
</classification>
~~~

~~~lua
#1=IFCPROJECT('09waczB0TB$hP3cVMWKh6v',$,$,$,$,$,$,$,$);
#2=IFCCLASSIFICATION($,$,$,'Foobar',$,$,$);
#3=IFCRELASSOCIATESCLASSIFICATION('0fShJTRKP9SPlVzqIn__dg',$,$,$,(#1),#2);
#4=IFCWALL('1Ev6VPwkb8DxG$KvUQ61Tj',$,$,$,$,$,$,$,$); /* Testcase */
#5=IFCWALL('3IpqHJLorDWOMZfkAsnFyj',$,$,$,$,$,$,$,$);
#6=IFCCLASSIFICATIONREFERENCE($,'1',$,#2,$,$);
#7=IFCRELASSOCIATESCLASSIFICATION('0ySnj2nlzA1PPRHJQQKB8o',$,$,$,(#5),#6);
#8=IFCWALL('3z07og1cf0tRksLXTFwrha',$,$,$,$,$,$,$,$);
#9=IFCCLASSIFICATIONREFERENCE($,'11',$,#2,$,$);
#10=IFCRELASSOCIATESCLASSIFICATION('3r2bqqaZXEE9_leqfSfwZw',$,$,$,(#8),#9);
#11=IFCWALL('3$KOb38H15zuNJocC0Evl1',$,$,$,$,$,$,$,$);
#12=IFCCLASSIFICATIONREFERENCE($,'22',$,#13,$,$);
#13=IFCCLASSIFICATIONREFERENCE($,'2',$,#2,$,$);
#15=IFCRELASSOCIATESCLASSIFICATION('3BndngXerCqR2YTUUqxbaP',$,$,$,(#11),#12);
~~~

[Sample IDS](fail-systems_should_match_exactly_2_5.ids) - [Sample IFC: 4](fail-systems_should_match_exactly_2_5.ifc)

## [PASS] Systems should match exactly 3/5

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <system>
    <simpleValue>Foobar</simpleValue>
  </system>
</classification>
~~~

~~~lua
#1=IFCPROJECT('09waczB0TB$hP3cVMWKh6v',$,$,$,$,$,$,$,$);
#2=IFCCLASSIFICATION($,$,$,'Foobar',$,$,$);
#3=IFCRELASSOCIATESCLASSIFICATION('0fShJTRKP9SPlVzqIn__dg',$,$,$,(#1),#2);
#4=IFCWALL('1Ev6VPwkb8DxG$KvUQ61Tj',$,$,$,$,$,$,$,$);
#5=IFCWALL('3IpqHJLorDWOMZfkAsnFyj',$,$,$,$,$,$,$,$); /* Testcase */
#6=IFCCLASSIFICATIONREFERENCE($,'1',$,#2,$,$);
#7=IFCRELASSOCIATESCLASSIFICATION('0ySnj2nlzA1PPRHJQQKB8o',$,$,$,(#5),#6);
#8=IFCWALL('3z07og1cf0tRksLXTFwrha',$,$,$,$,$,$,$,$);
#9=IFCCLASSIFICATIONREFERENCE($,'11',$,#2,$,$);
#10=IFCRELASSOCIATESCLASSIFICATION('3r2bqqaZXEE9_leqfSfwZw',$,$,$,(#8),#9);
#11=IFCWALL('3$KOb38H15zuNJocC0Evl1',$,$,$,$,$,$,$,$);
#12=IFCCLASSIFICATIONREFERENCE($,'22',$,#13,$,$);
#13=IFCCLASSIFICATIONREFERENCE($,'2',$,#2,$,$);
#15=IFCRELASSOCIATESCLASSIFICATION('3BndngXerCqR2YTUUqxbaP',$,$,$,(#11),#12);
~~~

[Sample IDS](pass-systems_should_match_exactly_3_5.ids) - [Sample IFC: 5](pass-systems_should_match_exactly_3_5.ifc)

## [PASS] Systems should match exactly 4/5

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <system>
    <simpleValue>Foobar</simpleValue>
  </system>
</classification>
~~~

~~~lua
#1=IFCPROJECT('09waczB0TB$hP3cVMWKh6v',$,$,$,$,$,$,$,$);
#2=IFCCLASSIFICATION($,$,$,'Foobar',$,$,$);
#3=IFCRELASSOCIATESCLASSIFICATION('0fShJTRKP9SPlVzqIn__dg',$,$,$,(#1),#2);
#4=IFCWALL('1Ev6VPwkb8DxG$KvUQ61Tj',$,$,$,$,$,$,$,$);
#5=IFCWALL('3IpqHJLorDWOMZfkAsnFyj',$,$,$,$,$,$,$,$);
#6=IFCCLASSIFICATIONREFERENCE($,'1',$,#2,$,$);
#7=IFCRELASSOCIATESCLASSIFICATION('0ySnj2nlzA1PPRHJQQKB8o',$,$,$,(#5),#6);
#8=IFCWALL('3z07og1cf0tRksLXTFwrha',$,$,$,$,$,$,$,$); /* Testcase */
#9=IFCCLASSIFICATIONREFERENCE($,'11',$,#2,$,$);
#10=IFCRELASSOCIATESCLASSIFICATION('3r2bqqaZXEE9_leqfSfwZw',$,$,$,(#8),#9);
#11=IFCWALL('3$KOb38H15zuNJocC0Evl1',$,$,$,$,$,$,$,$);
#12=IFCCLASSIFICATIONREFERENCE($,'22',$,#13,$,$);
#13=IFCCLASSIFICATIONREFERENCE($,'2',$,#2,$,$);
#15=IFCRELASSOCIATESCLASSIFICATION('3BndngXerCqR2YTUUqxbaP',$,$,$,(#11),#12);
~~~

[Sample IDS](pass-systems_should_match_exactly_4_5.ids) - [Sample IFC: 8](pass-systems_should_match_exactly_4_5.ifc)

## [PASS] Systems should match exactly 5/5

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <system>
    <simpleValue>Foobar</simpleValue>
  </system>
</classification>
~~~

~~~lua
#1=IFCPROJECT('09waczB0TB$hP3cVMWKh6v',$,$,$,$,$,$,$,$);
#2=IFCCLASSIFICATION($,$,$,'Foobar',$,$,$);
#3=IFCRELASSOCIATESCLASSIFICATION('0fShJTRKP9SPlVzqIn__dg',$,$,$,(#1),#2);
#4=IFCWALL('1Ev6VPwkb8DxG$KvUQ61Tj',$,$,$,$,$,$,$,$);
#5=IFCWALL('3IpqHJLorDWOMZfkAsnFyj',$,$,$,$,$,$,$,$);
#6=IFCCLASSIFICATIONREFERENCE($,'1',$,#2,$,$);
#7=IFCRELASSOCIATESCLASSIFICATION('0ySnj2nlzA1PPRHJQQKB8o',$,$,$,(#5),#6);
#8=IFCWALL('3z07og1cf0tRksLXTFwrha',$,$,$,$,$,$,$,$);
#9=IFCCLASSIFICATIONREFERENCE($,'11',$,#2,$,$);
#10=IFCRELASSOCIATESCLASSIFICATION('3r2bqqaZXEE9_leqfSfwZw',$,$,$,(#8),#9);
#11=IFCWALL('3$KOb38H15zuNJocC0Evl1',$,$,$,$,$,$,$,$); /* Testcase */
#12=IFCCLASSIFICATIONREFERENCE($,'22',$,#13,$,$);
#13=IFCCLASSIFICATIONREFERENCE($,'2',$,#2,$,$);
#15=IFCRELASSOCIATESCLASSIFICATION('3BndngXerCqR2YTUUqxbaP',$,$,$,(#11),#12);
~~~

[Sample IDS](pass-systems_should_match_exactly_5_5.ids) - [Sample IFC: 11](pass-systems_should_match_exactly_5_5.ifc)

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
#1=IFCPROJECT('09waczB0TB$hP3cVMWKh6v',$,$,$,$,$,$,$,$);
#2=IFCCLASSIFICATION($,$,$,'Foobar',$,$,$);
#3=IFCRELASSOCIATESCLASSIFICATION('0fShJTRKP9SPlVzqIn__dg',$,$,$,(#1),#2);
#4=IFCWALL('1Ev6VPwkb8DxG$KvUQ61Tj',$,$,$,$,$,$,$,$);
#5=IFCWALL('3IpqHJLorDWOMZfkAsnFyj',$,$,$,$,$,$,$,$); /* Testcase */
#6=IFCCLASSIFICATIONREFERENCE($,'1',$,#2,$,$);
#7=IFCRELASSOCIATESCLASSIFICATION('0ySnj2nlzA1PPRHJQQKB8o',$,$,$,(#5),#6);
#8=IFCWALL('3z07og1cf0tRksLXTFwrha',$,$,$,$,$,$,$,$);
#9=IFCCLASSIFICATIONREFERENCE($,'11',$,#2,$,$);
#10=IFCRELASSOCIATESCLASSIFICATION('3r2bqqaZXEE9_leqfSfwZw',$,$,$,(#8),#9);
#11=IFCWALL('3$KOb38H15zuNJocC0Evl1',$,$,$,$,$,$,$,$);
#12=IFCCLASSIFICATIONREFERENCE($,'22',$,#13,$,$);
#13=IFCCLASSIFICATIONREFERENCE($,'2',$,#2,$,$);
#15=IFCRELASSOCIATESCLASSIFICATION('3BndngXerCqR2YTUUqxbaP',$,$,$,(#11),#12);
~~~

[Sample IDS](pass-restrictions_can_be_used_for_values_1_3.ids) - [Sample IFC: 5](pass-restrictions_can_be_used_for_values_1_3.ifc)

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
#1=IFCPROJECT('09waczB0TB$hP3cVMWKh6v',$,$,$,$,$,$,$,$);
#2=IFCCLASSIFICATION($,$,$,'Foobar',$,$,$);
#3=IFCRELASSOCIATESCLASSIFICATION('0fShJTRKP9SPlVzqIn__dg',$,$,$,(#1),#2);
#4=IFCWALL('1Ev6VPwkb8DxG$KvUQ61Tj',$,$,$,$,$,$,$,$);
#5=IFCWALL('3IpqHJLorDWOMZfkAsnFyj',$,$,$,$,$,$,$,$);
#6=IFCCLASSIFICATIONREFERENCE($,'1',$,#2,$,$);
#7=IFCRELASSOCIATESCLASSIFICATION('0ySnj2nlzA1PPRHJQQKB8o',$,$,$,(#5),#6);
#8=IFCWALL('3z07og1cf0tRksLXTFwrha',$,$,$,$,$,$,$,$); /* Testcase */
#9=IFCCLASSIFICATIONREFERENCE($,'11',$,#2,$,$);
#10=IFCRELASSOCIATESCLASSIFICATION('3r2bqqaZXEE9_leqfSfwZw',$,$,$,(#8),#9);
#11=IFCWALL('3$KOb38H15zuNJocC0Evl1',$,$,$,$,$,$,$,$);
#12=IFCCLASSIFICATIONREFERENCE($,'22',$,#13,$,$);
#13=IFCCLASSIFICATIONREFERENCE($,'2',$,#2,$,$);
#15=IFCRELASSOCIATESCLASSIFICATION('3BndngXerCqR2YTUUqxbaP',$,$,$,(#11),#12);
~~~

[Sample IDS](pass-restrictions_can_be_used_for_values_2_3.ids) - [Sample IFC: 8](pass-restrictions_can_be_used_for_values_2_3.ifc)

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
#1=IFCPROJECT('09waczB0TB$hP3cVMWKh6v',$,$,$,$,$,$,$,$);
#2=IFCCLASSIFICATION($,$,$,'Foobar',$,$,$);
#3=IFCRELASSOCIATESCLASSIFICATION('0fShJTRKP9SPlVzqIn__dg',$,$,$,(#1),#2);
#4=IFCWALL('1Ev6VPwkb8DxG$KvUQ61Tj',$,$,$,$,$,$,$,$);
#5=IFCWALL('3IpqHJLorDWOMZfkAsnFyj',$,$,$,$,$,$,$,$);
#6=IFCCLASSIFICATIONREFERENCE($,'1',$,#2,$,$);
#7=IFCRELASSOCIATESCLASSIFICATION('0ySnj2nlzA1PPRHJQQKB8o',$,$,$,(#5),#6);
#8=IFCWALL('3z07og1cf0tRksLXTFwrha',$,$,$,$,$,$,$,$);
#9=IFCCLASSIFICATIONREFERENCE($,'11',$,#2,$,$);
#10=IFCRELASSOCIATESCLASSIFICATION('3r2bqqaZXEE9_leqfSfwZw',$,$,$,(#8),#9);
#11=IFCWALL('3$KOb38H15zuNJocC0Evl1',$,$,$,$,$,$,$,$); /* Testcase */
#12=IFCCLASSIFICATIONREFERENCE($,'22',$,#13,$,$);
#13=IFCCLASSIFICATIONREFERENCE($,'2',$,#2,$,$);
#15=IFCRELASSOCIATESCLASSIFICATION('3BndngXerCqR2YTUUqxbaP',$,$,$,(#11),#12);
~~~

[Sample IDS](fail-restrictions_can_be_used_for_values_3_3.ids) - [Sample IFC: 11](fail-restrictions_can_be_used_for_values_3_3.ifc)

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
#1=IFCPROJECT('09waczB0TB$hP3cVMWKh6v',$,$,$,$,$,$,$,$);
#2=IFCCLASSIFICATION($,$,$,'Foobar',$,$,$);
#3=IFCRELASSOCIATESCLASSIFICATION('0fShJTRKP9SPlVzqIn__dg',$,$,$,(#1),#2);
#4=IFCWALL('1Ev6VPwkb8DxG$KvUQ61Tj',$,$,$,$,$,$,$,$); /* Testcase */
#5=IFCWALL('3IpqHJLorDWOMZfkAsnFyj',$,$,$,$,$,$,$,$);
#6=IFCCLASSIFICATIONREFERENCE($,'1',$,#2,$,$);
#7=IFCRELASSOCIATESCLASSIFICATION('0ySnj2nlzA1PPRHJQQKB8o',$,$,$,(#5),#6);
#8=IFCWALL('3z07og1cf0tRksLXTFwrha',$,$,$,$,$,$,$,$);
#9=IFCCLASSIFICATIONREFERENCE($,'11',$,#2,$,$);
#10=IFCRELASSOCIATESCLASSIFICATION('3r2bqqaZXEE9_leqfSfwZw',$,$,$,(#8),#9);
#11=IFCWALL('3$KOb38H15zuNJocC0Evl1',$,$,$,$,$,$,$,$);
#12=IFCCLASSIFICATIONREFERENCE($,'22',$,#13,$,$);
#13=IFCCLASSIFICATIONREFERENCE($,'2',$,#2,$,$);
#15=IFCRELASSOCIATESCLASSIFICATION('3BndngXerCqR2YTUUqxbaP',$,$,$,(#11),#12);
~~~

[Sample IDS](fail-restrictions_can_be_used_for_systems_1_2.ids) - [Sample IFC: 4](fail-restrictions_can_be_used_for_systems_1_2.ifc)

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
#1=IFCPROJECT('09waczB0TB$hP3cVMWKh6v',$,$,$,$,$,$,$,$);
#2=IFCCLASSIFICATION($,$,$,'Foobar',$,$,$);
#3=IFCRELASSOCIATESCLASSIFICATION('0fShJTRKP9SPlVzqIn__dg',$,$,$,(#1),#2);
#4=IFCWALL('1Ev6VPwkb8DxG$KvUQ61Tj',$,$,$,$,$,$,$,$);
#5=IFCWALL('3IpqHJLorDWOMZfkAsnFyj',$,$,$,$,$,$,$,$); /* Testcase */
#6=IFCCLASSIFICATIONREFERENCE($,'1',$,#2,$,$);
#7=IFCRELASSOCIATESCLASSIFICATION('0ySnj2nlzA1PPRHJQQKB8o',$,$,$,(#5),#6);
#8=IFCWALL('3z07og1cf0tRksLXTFwrha',$,$,$,$,$,$,$,$);
#9=IFCCLASSIFICATIONREFERENCE($,'11',$,#2,$,$);
#10=IFCRELASSOCIATESCLASSIFICATION('3r2bqqaZXEE9_leqfSfwZw',$,$,$,(#8),#9);
#11=IFCWALL('3$KOb38H15zuNJocC0Evl1',$,$,$,$,$,$,$,$);
#12=IFCCLASSIFICATIONREFERENCE($,'22',$,#13,$,$);
#13=IFCCLASSIFICATIONREFERENCE($,'2',$,#2,$,$);
#15=IFCRELASSOCIATESCLASSIFICATION('3BndngXerCqR2YTUUqxbaP',$,$,$,(#11),#12);
~~~

[Sample IDS](pass-restrictions_can_be_used_for_systems_2_2.ids) - [Sample IFC: 5](pass-restrictions_can_be_used_for_systems_2_2.ifc)

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
#1=IFCPROJECT('09waczB0TB$hP3cVMWKh6v',$,$,$,$,$,$,$,$);
#2=IFCCLASSIFICATION($,$,$,'Foobar',$,$,$);
#3=IFCRELASSOCIATESCLASSIFICATION('0fShJTRKP9SPlVzqIn__dg',$,$,$,(#1),#2);
#4=IFCWALL('1Ev6VPwkb8DxG$KvUQ61Tj',$,$,$,$,$,$,$,$);
#5=IFCWALL('3IpqHJLorDWOMZfkAsnFyj',$,$,$,$,$,$,$,$); /* Testcase */
#6=IFCCLASSIFICATIONREFERENCE($,'1',$,#2,$,$);
#7=IFCRELASSOCIATESCLASSIFICATION('0ySnj2nlzA1PPRHJQQKB8o',$,$,$,(#5),#6);
#8=IFCWALL('3z07og1cf0tRksLXTFwrha',$,$,$,$,$,$,$,$);
#9=IFCCLASSIFICATIONREFERENCE($,'11',$,#2,$,$);
#10=IFCRELASSOCIATESCLASSIFICATION('3r2bqqaZXEE9_leqfSfwZw',$,$,$,(#8),#9);
#11=IFCWALL('3$KOb38H15zuNJocC0Evl1',$,$,$,$,$,$,$,$);
#12=IFCCLASSIFICATIONREFERENCE($,'22',$,#13,$,$);
#13=IFCCLASSIFICATIONREFERENCE($,'2',$,#2,$,$);
#15=IFCRELASSOCIATESCLASSIFICATION('3BndngXerCqR2YTUUqxbaP',$,$,$,(#11),#12);
~~~

[Sample IDS](pass-both_system_and_value_must_match__all__not_any__if_specified_1_2.ids) - [Sample IFC: 5](pass-both_system_and_value_must_match__all__not_any__if_specified_1_2.ifc)

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
#1=IFCPROJECT('09waczB0TB$hP3cVMWKh6v',$,$,$,$,$,$,$,$);
#2=IFCCLASSIFICATION($,$,$,'Foobar',$,$,$);
#3=IFCRELASSOCIATESCLASSIFICATION('0fShJTRKP9SPlVzqIn__dg',$,$,$,(#1),#2);
#4=IFCWALL('1Ev6VPwkb8DxG$KvUQ61Tj',$,$,$,$,$,$,$,$);
#5=IFCWALL('3IpqHJLorDWOMZfkAsnFyj',$,$,$,$,$,$,$,$);
#6=IFCCLASSIFICATIONREFERENCE($,'1',$,#2,$,$);
#7=IFCRELASSOCIATESCLASSIFICATION('0ySnj2nlzA1PPRHJQQKB8o',$,$,$,(#5),#6);
#8=IFCWALL('3z07og1cf0tRksLXTFwrha',$,$,$,$,$,$,$,$); /* Testcase */
#9=IFCCLASSIFICATIONREFERENCE($,'11',$,#2,$,$);
#10=IFCRELASSOCIATESCLASSIFICATION('3r2bqqaZXEE9_leqfSfwZw',$,$,$,(#8),#9);
#11=IFCWALL('3$KOb38H15zuNJocC0Evl1',$,$,$,$,$,$,$,$);
#12=IFCCLASSIFICATIONREFERENCE($,'22',$,#13,$,$);
#13=IFCCLASSIFICATIONREFERENCE($,'2',$,#2,$,$);
#15=IFCRELASSOCIATESCLASSIFICATION('3BndngXerCqR2YTUUqxbaP',$,$,$,(#11),#12);
~~~

[Sample IDS](fail-both_system_and_value_must_match__all__not_any__if_specified_2_2.ids) - [Sample IFC: 8](fail-both_system_and_value_must_match__all__not_any__if_specified_2_2.ifc)

## [PASS] Occurrences override the type classification per system 1/3

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>11</simpleValue>
  </value>
</classification>
~~~

~~~lua
#1=IFCPROJECT('09waczB0TB$hP3cVMWKh6v',$,$,$,$,$,$,$,$);
#2=IFCCLASSIFICATION($,$,$,'Foobar',$,$,$);
#3=IFCRELASSOCIATESCLASSIFICATION('0fShJTRKP9SPlVzqIn__dg',$,$,$,(#1),#2);
#4=IFCWALL('1Ev6VPwkb8DxG$KvUQ61Tj',$,$,$,$,$,$,$,$);
#5=IFCWALL('3IpqHJLorDWOMZfkAsnFyj',$,$,$,$,$,$,$,$);
#6=IFCCLASSIFICATIONREFERENCE($,'1',$,#2,$,$);
#7=IFCRELASSOCIATESCLASSIFICATION('0ySnj2nlzA1PPRHJQQKB8o',$,$,$,(#5),#6);
#8=IFCWALL('3z07og1cf0tRksLXTFwrha',$,$,$,$,$,$,$,$);
#9=IFCCLASSIFICATIONREFERENCE($,'11',$,#2,$,$);
#10=IFCRELASSOCIATESCLASSIFICATION('3r2bqqaZXEE9_leqfSfwZw',$,$,$,(#8,#16),#9);
#11=IFCWALL('3$KOb38H15zuNJocC0Evl1',$,$,$,$,$,$,$,$);
#12=IFCCLASSIFICATIONREFERENCE($,'22',$,#13,$,$);
#13=IFCCLASSIFICATIONREFERENCE($,'2',$,#2,$,$);
#15=IFCRELASSOCIATESCLASSIFICATION('3BndngXerCqR2YTUUqxbaP',$,$,$,(#11,#17),#12);
#16=IFCWALL('1kMmos_gT3tfAYnna3_nxC',$,$,$,$,$,$,$,$); /* Testcase */
#17=IFCWALLTYPE('0IXylVDbn64fZ8Hl539Mt0',$,$,$,$,$,$,$,$,.ELEMENTEDWALL.);
#18=IFCRELDEFINESBYTYPE('3cAzW6JrbF0A1Ico3iXFmg',$,$,$,(#16),#17);
#19=IFCCLASSIFICATION($,$,$,'Foobaz',$,$,$);
#20=IFCRELASSOCIATESCLASSIFICATION('0DQ_5wcY93x97$qQl2K$e4',$,$,$,(#1),#19);
#21=IFCCLASSIFICATIONREFERENCE($,'X',$,#19,$,$);
#22=IFCRELASSOCIATESCLASSIFICATION('1PiiZ7sI119fVll5yYq110',$,$,$,(#17),#21);
~~~

[Sample IDS](pass-occurrences_override_the_type_classification_per_system_1_3.ids) - [Sample IFC: 16](pass-occurrences_override_the_type_classification_per_system_1_3.ifc)

## [FAIL] Occurrences override the type classification per system 2/3

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>22</simpleValue>
  </value>
</classification>
~~~

~~~lua
#1=IFCPROJECT('09waczB0TB$hP3cVMWKh6v',$,$,$,$,$,$,$,$);
#2=IFCCLASSIFICATION($,$,$,'Foobar',$,$,$);
#3=IFCRELASSOCIATESCLASSIFICATION('0fShJTRKP9SPlVzqIn__dg',$,$,$,(#1),#2);
#4=IFCWALL('1Ev6VPwkb8DxG$KvUQ61Tj',$,$,$,$,$,$,$,$);
#5=IFCWALL('3IpqHJLorDWOMZfkAsnFyj',$,$,$,$,$,$,$,$);
#6=IFCCLASSIFICATIONREFERENCE($,'1',$,#2,$,$);
#7=IFCRELASSOCIATESCLASSIFICATION('0ySnj2nlzA1PPRHJQQKB8o',$,$,$,(#5),#6);
#8=IFCWALL('3z07og1cf0tRksLXTFwrha',$,$,$,$,$,$,$,$);
#9=IFCCLASSIFICATIONREFERENCE($,'11',$,#2,$,$);
#10=IFCRELASSOCIATESCLASSIFICATION('3r2bqqaZXEE9_leqfSfwZw',$,$,$,(#8,#16),#9);
#11=IFCWALL('3$KOb38H15zuNJocC0Evl1',$,$,$,$,$,$,$,$);
#12=IFCCLASSIFICATIONREFERENCE($,'22',$,#13,$,$);
#13=IFCCLASSIFICATIONREFERENCE($,'2',$,#2,$,$);
#15=IFCRELASSOCIATESCLASSIFICATION('3BndngXerCqR2YTUUqxbaP',$,$,$,(#11,#17),#12);
#16=IFCWALL('1kMmos_gT3tfAYnna3_nxC',$,$,$,$,$,$,$,$); /* Testcase */
#17=IFCWALLTYPE('0IXylVDbn64fZ8Hl539Mt0',$,$,$,$,$,$,$,$,.ELEMENTEDWALL.);
#18=IFCRELDEFINESBYTYPE('3cAzW6JrbF0A1Ico3iXFmg',$,$,$,(#16),#17);
#19=IFCCLASSIFICATION($,$,$,'Foobaz',$,$,$);
#20=IFCRELASSOCIATESCLASSIFICATION('0DQ_5wcY93x97$qQl2K$e4',$,$,$,(#1),#19);
#21=IFCCLASSIFICATIONREFERENCE($,'X',$,#19,$,$);
#22=IFCRELASSOCIATESCLASSIFICATION('1PiiZ7sI119fVll5yYq110',$,$,$,(#17),#21);
~~~

[Sample IDS](fail-occurrences_override_the_type_classification_per_system_2_3.ids) - [Sample IFC: 16](fail-occurrences_override_the_type_classification_per_system_2_3.ifc)

## [PASS] Occurrences override the type classification per system 3/3

~~~xml
<classification minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>X</simpleValue>
  </value>
</classification>
~~~

~~~lua
#1=IFCPROJECT('09waczB0TB$hP3cVMWKh6v',$,$,$,$,$,$,$,$);
#2=IFCCLASSIFICATION($,$,$,'Foobar',$,$,$);
#3=IFCRELASSOCIATESCLASSIFICATION('0fShJTRKP9SPlVzqIn__dg',$,$,$,(#1),#2);
#4=IFCWALL('1Ev6VPwkb8DxG$KvUQ61Tj',$,$,$,$,$,$,$,$);
#5=IFCWALL('3IpqHJLorDWOMZfkAsnFyj',$,$,$,$,$,$,$,$);
#6=IFCCLASSIFICATIONREFERENCE($,'1',$,#2,$,$);
#7=IFCRELASSOCIATESCLASSIFICATION('0ySnj2nlzA1PPRHJQQKB8o',$,$,$,(#5),#6);
#8=IFCWALL('3z07og1cf0tRksLXTFwrha',$,$,$,$,$,$,$,$);
#9=IFCCLASSIFICATIONREFERENCE($,'11',$,#2,$,$);
#10=IFCRELASSOCIATESCLASSIFICATION('3r2bqqaZXEE9_leqfSfwZw',$,$,$,(#8,#16),#9);
#11=IFCWALL('3$KOb38H15zuNJocC0Evl1',$,$,$,$,$,$,$,$);
#12=IFCCLASSIFICATIONREFERENCE($,'22',$,#13,$,$);
#13=IFCCLASSIFICATIONREFERENCE($,'2',$,#2,$,$);
#15=IFCRELASSOCIATESCLASSIFICATION('3BndngXerCqR2YTUUqxbaP',$,$,$,(#11,#17),#12);
#16=IFCWALL('1kMmos_gT3tfAYnna3_nxC',$,$,$,$,$,$,$,$); /* Testcase */
#17=IFCWALLTYPE('0IXylVDbn64fZ8Hl539Mt0',$,$,$,$,$,$,$,$,.ELEMENTEDWALL.);
#18=IFCRELDEFINESBYTYPE('3cAzW6JrbF0A1Ico3iXFmg',$,$,$,(#16),#17);
#19=IFCCLASSIFICATION($,$,$,'Foobaz',$,$,$);
#20=IFCRELASSOCIATESCLASSIFICATION('0DQ_5wcY93x97$qQl2K$e4',$,$,$,(#1),#19);
#21=IFCCLASSIFICATIONREFERENCE($,'X',$,#19,$,$);
#22=IFCRELASSOCIATESCLASSIFICATION('1PiiZ7sI119fVll5yYq110',$,$,$,(#17),#21);
~~~

[Sample IDS](pass-occurrences_override_the_type_classification_per_system_3_3.ids) - [Sample IFC: 16](pass-occurrences_override_the_type_classification_per_system_3_3.ifc)
