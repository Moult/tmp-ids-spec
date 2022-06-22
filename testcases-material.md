# Material testcases

These testcases are designed to help describe behaviour in edge cases and ambiguities. All valid IDS implementations must demonstrate identical behaviour to these test cases.

## [FAIL] Elements without a material always fail

~~~xml
<material minOccurs="1" maxOccurs="1"/>
~~~

~~~lua
#1=IFCWALL('319PHYQJ983OMIXOhty3wX',$,$,$,$,$,$,$,$); /* Testcase */
~~~

[Sample IDS](fail-elements_without_a_material_always_fail.ids) - [Sample IFC: 1](fail-elements_without_a_material_always_fail.ifc)

## [PASS] Elements with any material will pass an empty material facet

~~~xml
<material minOccurs="1" maxOccurs="1"/>
~~~

~~~lua
#1=IFCWALL('319PHYQJ983OMIXOhty3wX',$,$,$,$,$,$,$,$); /* Testcase */
#2=IFCMATERIAL('Unnamed',$,$);
#3=IFCRELASSOCIATESMATERIAL('2UT14UeKn8Jgvg8AVitqxV',$,$,$,(#1),#2);
~~~

[Sample IDS](pass-elements_with_any_material_will_pass_an_empty_material_facet.ids) - [Sample IFC: 1](pass-elements_with_any_material_will_pass_an_empty_material_facet.ifc)

## [FAIL] Material with no data will fail a value check

~~~xml
<material minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>Foo</simpleValue>
  </value>
</material>
~~~

~~~lua
#1=IFCWALL('0BRc9rmaj4b8Rpv2AtUYeQ',$,$,$,$,$,$,$,$); /* Testcase */
#2=IFCMATERIAL('Unnamed',$,$);
#3=IFCRELASSOCIATESMATERIAL('0J4ry8qxH87vhK1Vg7VgHg',$,$,$,(#1),#2);
~~~

[Sample IDS](fail-material_with_no_data_will_fail_a_value_check.ids) - [Sample IFC: 1](fail-material_with_no_data_will_fail_a_value_check.ifc)

## [PASS] A material name may pass the value check

~~~xml
<material minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>Foo</simpleValue>
  </value>
</material>
~~~

~~~lua
#1=IFCWALL('0BRc9rmaj4b8Rpv2AtUYeQ',$,$,$,$,$,$,$,$); /* Testcase */
#2=IFCMATERIAL('Foo',$,$);
#3=IFCRELASSOCIATESMATERIAL('0J4ry8qxH87vhK1Vg7VgHg',$,$,$,(#1),#2);
~~~

[Sample IDS](pass-a_material_name_may_pass_the_value_check.ids) - [Sample IFC: 1](pass-a_material_name_may_pass_the_value_check.ifc)

## [PASS] A material category may pass the value check

~~~xml
<material minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>Foo</simpleValue>
  </value>
</material>
~~~

~~~lua
#1=IFCWALL('0BRc9rmaj4b8Rpv2AtUYeQ',$,$,$,$,$,$,$,$); /* Testcase */
#2=IFCMATERIAL('Bar',$,'Foo');
#3=IFCRELASSOCIATESMATERIAL('0J4ry8qxH87vhK1Vg7VgHg',$,$,$,(#1),#2);
~~~

[Sample IDS](pass-a_material_category_may_pass_the_value_check.ids) - [Sample IFC: 1](pass-a_material_category_may_pass_the_value_check.ifc)

## [FAIL] A material list with no data will fail a value check

~~~xml
<material minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>Foo</simpleValue>
  </value>
</material>
~~~

~~~lua
#1=IFCWALL('2wkcl770zD19WuAXtn7I5e',$,$,$,$,$,$,$,$); /* Testcase */
#2=IFCMATERIALLIST((#4));
#3=IFCRELASSOCIATESMATERIAL('2Xh8a8fo12LRJMfv4$ro6D',$,$,$,(#1),#2);
#4=IFCMATERIAL('Concrete',$,'CONCRETE');
~~~

[Sample IDS](fail-a_material_list_with_no_data_will_fail_a_value_check.ids) - [Sample IFC: 1](fail-a_material_list_with_no_data_will_fail_a_value_check.ifc)

## [PASS] Any material Name in a list will pass a value check

~~~xml
<material minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>Foo</simpleValue>
  </value>
</material>
~~~

~~~lua
#1=IFCWALL('2wkcl770zD19WuAXtn7I5e',$,$,$,$,$,$,$,$); /* Testcase */
#2=IFCMATERIALLIST((#4,#5));
#3=IFCRELASSOCIATESMATERIAL('2Xh8a8fo12LRJMfv4$ro6D',$,$,$,(#1),#2);
#4=IFCMATERIAL('Concrete',$,'CONCRETE');
#5=IFCMATERIAL('Foo',$,$);
~~~

[Sample IDS](pass-any_material_name_in_a_list_will_pass_a_value_check.ids) - [Sample IFC: 1](pass-any_material_name_in_a_list_will_pass_a_value_check.ifc)

## [PASS] Any material Category in a list will pass a value check

~~~xml
<material minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>Foo</simpleValue>
  </value>
</material>
~~~

~~~lua
#1=IFCWALL('2wkcl770zD19WuAXtn7I5e',$,$,$,$,$,$,$,$); /* Testcase */
#2=IFCMATERIALLIST((#4,#5));
#3=IFCRELASSOCIATESMATERIAL('2Xh8a8fo12LRJMfv4$ro6D',$,$,$,(#1),#2);
#4=IFCMATERIAL('Concrete',$,'CONCRETE');
#5=IFCMATERIAL('Bar',$,'Foo');
~~~

[Sample IDS](pass-any_material_category_in_a_list_will_pass_a_value_check.ids) - [Sample IFC: 1](pass-any_material_category_in_a_list_will_pass_a_value_check.ifc)

## [PASS] Any layer Name in a layer set will pass a value check

~~~xml
<material minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>Foo</simpleValue>
  </value>
</material>
~~~

~~~lua
#1=IFCWALL('02WPqwNff3PvOsDvPQ9aoT',$,$,$,$,$,$,$,$); /* Testcase */
#2=IFCMATERIALLAYERSET((#5),'Unnamed',$);
#3=IFCRELASSOCIATESMATERIAL('0IJElgCAH5QgUZYJCIpVdF',$,$,$,(#1),#2);
#4=IFCMATERIAL('Unnamed',$,$);
#5=IFCMATERIALLAYER(#4,1.,$,'Foo',$,$,$);
~~~

[Sample IDS](pass-any_layer_name_in_a_layer_set_will_pass_a_value_check.ids) - [Sample IFC: 1](pass-any_layer_name_in_a_layer_set_will_pass_a_value_check.ifc)

## [PASS] Any layer Category in a layer set will pass a value check

~~~xml
<material minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>Foo</simpleValue>
  </value>
</material>
~~~

~~~lua
#1=IFCWALL('02WPqwNff3PvOsDvPQ9aoT',$,$,$,$,$,$,$,$); /* Testcase */
#2=IFCMATERIALLAYERSET((#5),'Unnamed',$);
#3=IFCRELASSOCIATESMATERIAL('0IJElgCAH5QgUZYJCIpVdF',$,$,$,(#1),#2);
#4=IFCMATERIAL('Unnamed',$,$);
#5=IFCMATERIALLAYER(#4,1.,$,'Bar',$,'Foo',$);
~~~

[Sample IDS](pass-any_layer_category_in_a_layer_set_will_pass_a_value_check.ids) - [Sample IFC: 1](pass-any_layer_category_in_a_layer_set_will_pass_a_value_check.ifc)

## [PASS] Any material Name in a layer set will pass a value check

~~~xml
<material minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>Foo</simpleValue>
  </value>
</material>
~~~

~~~lua
#1=IFCWALL('02WPqwNff3PvOsDvPQ9aoT',$,$,$,$,$,$,$,$); /* Testcase */
#2=IFCMATERIALLAYERSET((#5),'Unnamed',$);
#3=IFCRELASSOCIATESMATERIAL('0IJElgCAH5QgUZYJCIpVdF',$,$,$,(#1),#2);
#4=IFCMATERIAL('Foo',$,$);
#5=IFCMATERIALLAYER(#4,1.,$,'Bar',$,'Bar',$);
~~~

[Sample IDS](pass-any_material_name_in_a_layer_set_will_pass_a_value_check.ids) - [Sample IFC: 1](pass-any_material_name_in_a_layer_set_will_pass_a_value_check.ifc)

## [PASS] Any material Category in a layer set will pass a value check

~~~xml
<material minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>Foo</simpleValue>
  </value>
</material>
~~~

~~~lua
#1=IFCWALL('02WPqwNff3PvOsDvPQ9aoT',$,$,$,$,$,$,$,$); /* Testcase */
#2=IFCMATERIALLAYERSET((#5),'Unnamed',$);
#3=IFCRELASSOCIATESMATERIAL('0IJElgCAH5QgUZYJCIpVdF',$,$,$,(#1),#2);
#4=IFCMATERIAL('Bar',$,'Foo');
#5=IFCMATERIALLAYER(#4,1.,$,'Bar',$,'Bar',$);
~~~

[Sample IDS](pass-any_material_category_in_a_layer_set_will_pass_a_value_check.ids) - [Sample IFC: 1](pass-any_material_category_in_a_layer_set_will_pass_a_value_check.ifc)

## [PASS] Any profile Name in a profile set will pass a value check

~~~xml
<material minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>Foo</simpleValue>
  </value>
</material>
~~~

~~~lua
#1=IFCWALL('0ikno0YNn5b94GQ2O92ciQ',$,$,$,$,$,$,$,$); /* Testcase */
#2=IFCMATERIALPROFILESET('Unnamed',$,(#5),$);
#3=IFCRELASSOCIATESMATERIAL('3PxleJXSj2NRcXuQJYL$_5',$,$,$,(#1),#2);
#4=IFCMATERIAL('Unnamed',$,$);
#5=IFCMATERIALPROFILE('Foo',$,#4,#6,$,$);
#6=IFCCIRCLEPROFILEDEF(.AREA.,$,$,1.);
~~~

[Sample IDS](pass-any_profile_name_in_a_profile_set_will_pass_a_value_check.ids) - [Sample IFC: 1](pass-any_profile_name_in_a_profile_set_will_pass_a_value_check.ifc)

## [PASS] Any profile Category in a profile set will pass a value check

~~~xml
<material minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>Foo</simpleValue>
  </value>
</material>
~~~

~~~lua
#1=IFCWALL('0ikno0YNn5b94GQ2O92ciQ',$,$,$,$,$,$,$,$); /* Testcase */
#2=IFCMATERIALPROFILESET('Unnamed',$,(#5),$);
#3=IFCRELASSOCIATESMATERIAL('3PxleJXSj2NRcXuQJYL$_5',$,$,$,(#1),#2);
#4=IFCMATERIAL('Unnamed',$,$);
#5=IFCMATERIALPROFILE('Bar',$,#4,#6,$,'Foo');
#6=IFCCIRCLEPROFILEDEF(.AREA.,$,$,1.);
~~~

[Sample IDS](pass-any_profile_category_in_a_profile_set_will_pass_a_value_check.ids) - [Sample IFC: 1](pass-any_profile_category_in_a_profile_set_will_pass_a_value_check.ifc)

## [PASS] Any material Name in a profile set will pass a value check

~~~xml
<material minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>Foo</simpleValue>
  </value>
</material>
~~~

~~~lua
#1=IFCWALL('0ikno0YNn5b94GQ2O92ciQ',$,$,$,$,$,$,$,$); /* Testcase */
#2=IFCMATERIALPROFILESET('Unnamed',$,(#5),$);
#3=IFCRELASSOCIATESMATERIAL('3PxleJXSj2NRcXuQJYL$_5',$,$,$,(#1),#2);
#4=IFCMATERIAL('Foo',$,$);
#5=IFCMATERIALPROFILE('Bar',$,#4,#6,$,'Bar');
#6=IFCCIRCLEPROFILEDEF(.AREA.,$,$,1.);
~~~

[Sample IDS](pass-any_material_name_in_a_profile_set_will_pass_a_value_check.ids) - [Sample IFC: 1](pass-any_material_name_in_a_profile_set_will_pass_a_value_check.ifc)

## [PASS] Any material category in a profile set will pass a value check

~~~xml
<material minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>Foo</simpleValue>
  </value>
</material>
~~~

~~~lua
#1=IFCWALL('0ikno0YNn5b94GQ2O92ciQ',$,$,$,$,$,$,$,$); /* Testcase */
#2=IFCMATERIALPROFILESET('Unnamed',$,(#5),$);
#3=IFCRELASSOCIATESMATERIAL('3PxleJXSj2NRcXuQJYL$_5',$,$,$,(#1),#2);
#4=IFCMATERIAL('Bar',$,'Foo');
#5=IFCMATERIALPROFILE('Bar',$,#4,#6,$,'Bar');
#6=IFCCIRCLEPROFILEDEF(.AREA.,$,$,1.);
~~~

[Sample IDS](pass-any_material_category_in_a_profile_set_will_pass_a_value_check.ids) - [Sample IFC: 1](pass-any_material_category_in_a_profile_set_will_pass_a_value_check.ifc)

## [FAIL] A constituent set with no data will fail a value check

~~~xml
<material minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>Foo</simpleValue>
  </value>
</material>
~~~

~~~lua
#1=IFCWALL('0$1VfYP5z0KBH2TJ5sSRrf',$,$,$,$,$,$,$,$); /* Testcase */
#2=IFCMATERIALCONSTITUENTSET('Unnamed',$,$);
#3=IFCRELASSOCIATESMATERIAL('2urDqpdqTEX8YbzokRx8Ic',$,$,$,(#1),#2);
~~~

[Sample IDS](fail-a_constituent_set_with_no_data_will_fail_a_value_check.ids) - [Sample IFC: 1](fail-a_constituent_set_with_no_data_will_fail_a_value_check.ifc)

## [PASS] Any constituent Name in a constituent set will pass a value check

~~~xml
<material minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>Foo</simpleValue>
  </value>
</material>
~~~

~~~lua
#1=IFCWALL('0$1VfYP5z0KBH2TJ5sSRrf',$,$,$,$,$,$,$,$); /* Testcase */
#2=IFCMATERIALCONSTITUENTSET('Unnamed',$,(#5));
#3=IFCRELASSOCIATESMATERIAL('2urDqpdqTEX8YbzokRx8Ic',$,$,$,(#1),#2);
#4=IFCMATERIAL('Unnamed',$,$);
#5=IFCMATERIALCONSTITUENT('Foo',$,#4,$,$);
~~~

[Sample IDS](pass-any_constituent_name_in_a_constituent_set_will_pass_a_value_check.ids) - [Sample IFC: 1](pass-any_constituent_name_in_a_constituent_set_will_pass_a_value_check.ifc)

## [PASS] Any constituent Category in a constituent set will pass a value check

~~~xml
<material minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>Foo</simpleValue>
  </value>
</material>
~~~

~~~lua
#1=IFCWALL('0$1VfYP5z0KBH2TJ5sSRrf',$,$,$,$,$,$,$,$); /* Testcase */
#2=IFCMATERIALCONSTITUENTSET('Unnamed',$,(#5));
#3=IFCRELASSOCIATESMATERIAL('2urDqpdqTEX8YbzokRx8Ic',$,$,$,(#1),#2);
#4=IFCMATERIAL('Unnamed',$,$);
#5=IFCMATERIALCONSTITUENT('Bar',$,#4,$,'Foo');
~~~

[Sample IDS](pass-any_constituent_category_in_a_constituent_set_will_pass_a_value_check.ids) - [Sample IFC: 1](pass-any_constituent_category_in_a_constituent_set_will_pass_a_value_check.ifc)

## [PASS] Any material Name in a constituent set will pass a value check

~~~xml
<material minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>Foo</simpleValue>
  </value>
</material>
~~~

~~~lua
#1=IFCWALL('0$1VfYP5z0KBH2TJ5sSRrf',$,$,$,$,$,$,$,$); /* Testcase */
#2=IFCMATERIALCONSTITUENTSET('Unnamed',$,(#5));
#3=IFCRELASSOCIATESMATERIAL('2urDqpdqTEX8YbzokRx8Ic',$,$,$,(#1),#2);
#4=IFCMATERIAL('Foo',$,$);
#5=IFCMATERIALCONSTITUENT('Bar',$,#4,$,'Bar');
~~~

[Sample IDS](pass-any_material_name_in_a_constituent_set_will_pass_a_value_check.ids) - [Sample IFC: 1](pass-any_material_name_in_a_constituent_set_will_pass_a_value_check.ifc)

## [PASS] Any material Category in a constituent set will pass a value check

~~~xml
<material minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>Foo</simpleValue>
  </value>
</material>
~~~

~~~lua
#1=IFCWALL('0$1VfYP5z0KBH2TJ5sSRrf',$,$,$,$,$,$,$,$); /* Testcase */
#2=IFCMATERIALCONSTITUENTSET('Unnamed',$,(#5));
#3=IFCRELASSOCIATESMATERIAL('2urDqpdqTEX8YbzokRx8Ic',$,$,$,(#1),#2);
#4=IFCMATERIAL('Bar',$,'Foo');
#5=IFCMATERIALCONSTITUENT('Bar',$,#4,$,'Bar');
~~~

[Sample IDS](pass-any_material_category_in_a_constituent_set_will_pass_a_value_check.ids) - [Sample IFC: 1](pass-any_material_category_in_a_constituent_set_will_pass_a_value_check.ifc)

## [PASS] Occurrences can inherit materials from their types

~~~xml
<material minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>Foo</simpleValue>
  </value>
</material>
~~~

~~~lua
#1=IFCWALL('1xV32aA6bB1QfmT1UYJ5M7',$,$,$,$,$,$,$,$); /* Testcase */
#2=IFCWALLTYPE('04g7LjBs55N8_ewCD0Wbrc',$,$,$,$,$,$,$,$,.ELEMENTEDWALL.);
#3=IFCRELDEFINESBYTYPE('0MmnMW2yzDrQBqAf_TIZx5',$,$,$,(#1),#2);
#4=IFCMATERIAL('Foo',$,$);
#5=IFCRELASSOCIATESMATERIAL('2P2pXIWmjAsvs_Rwg67q2S',$,$,$,(#2),#4);
~~~

[Sample IDS](pass-occurrences_can_inherit_materials_from_their_types.ids) - [Sample IFC: 1](pass-occurrences_can_inherit_materials_from_their_types.ifc)

## [PASS] Occurrences can override materials from their types

~~~xml
<material minOccurs="1" maxOccurs="1">
  <value>
    <simpleValue>Foo</simpleValue>
  </value>
</material>
~~~

~~~lua
#1=IFCWALL('32Dle6WzzFFhwvPjiS58DD',$,$,$,$,$,$,$,$); /* Testcase */
#2=IFCWALLTYPE('1qN2zbMzDCLeFthwWoeox5',$,$,$,$,$,$,$,$,.ELEMENTEDWALL.);
#3=IFCRELDEFINESBYTYPE('0kAZF6dv902etnJ_Y6rjg_',$,$,$,(#1),#2);
#4=IFCMATERIAL('Bar',$,$);
#5=IFCRELASSOCIATESMATERIAL('1ygeyuwcLE4gjQ9TcEGvU0',$,$,$,(#2),#4);
#6=IFCMATERIAL('Foo',$,$);
#7=IFCRELASSOCIATESMATERIAL('3Q9uFawKP4bxJudw3HPvir',$,$,$,(#1),#6);
~~~

[Sample IDS](pass-occurrences_can_override_materials_from_their_types.ids) - [Sample IFC: 1](pass-occurrences_can_override_materials_from_their_types.ifc)
