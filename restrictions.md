# Complex restrictions

When specifying a **Facet Parameter**, you may either specify a **Simple Value** or a **Complex Restriction**. A **Simple Value** may be text, a number, or a boolean (TRUE / FALSE). In contrast, a **Complex Restriction** may represent pick lists of valid values, naming schemes and conventions, numeric ranges, or more. A restriction may be specified in six different ways:

 - Enumeration
 - Pattern
 - Bounds
 - Length
 - Total digits
 - Decimal places

## Enumeration

An **Enumeration** restriction means that the value must be one of a list of allowed values. For example, you might want to specify that a material may be either "concrete" or "steel". You may also specify numbers in a list, such as specifying that a concrete strength grade may be either "25", "30", "35, or "40".

## Pattern

A **Pattern** restriction represents a naming convention or naming scheme. For example, if you want to specify that door types must be named using the convention DT01, DT02, DT03, etc, you can create a pattern defining that the letters "DT" should be first, followed by two numbers.

Computers have a special way of defining patterns of text called **Regex**. It uses special symbols to tell the computer to expect numbers, letters, or any character. You may already be familiar with computer patterns using the "`*`" character as a wildcard. For example, you might say that the pattern "`DT*`" can be satisfied by the values "`DTA`", "`DTB`", or even "`DT01`". **Regex** is a bit more complex, but in exchange, you can be more specific about the rules in your pattern. Here are some common examples you can use:

Pattern | Description | Example values that meet the pattern criteria | Example values that fail the pattern
--- | --- | --- | ---
`DT01` | When only letters and numbers are used with no symbols, then the pattern is equivalent to an exact match | "`DT01`" | Anything other than "`DT01`" will fail.
`DT_ABC-01` | Apart from letters and numbers, the "`_`" and "`-`" symbols have no special meaning, so this pattern is also equivalent to an exact match. | "`DT_ABC-01`" | Anything other than "`DT_ABC-01`" will fail.
`DT.` | The "`.`" symbol is a wildcard for any _single_ character. | "`DT1`", "`DT2`", "`DTA`", "`DTX`", "`DT+`", etc | "`DT01`" will not match because it has multiple characters after "`DT`". "`ADT1`" will not match because it starts with "`A`", not "`DT`".
`DT..` | When the "`.`" wildcard symbol is used multiple times, each time represents another _single_ character. | "`DT01`", "`DT02`", "`DTAB`", "`DTXY`", "`DT++`", etc | "`DT1`" will not match because it doesn't have two characters after "`DT`".
`DT.*` | When the "`*`" symbol is used after the "`.`" symbol to create "`.*`", it is a wildcard for any number of characters, not just a single character. So anything starting with `DT` will match, regardless of what characters are after it. | "`DT1`", "`DT02`", "`DTA`", "`DTXYZ`", "`DT+1-BC=123`", etc | Anything that doesn't start with "`DT`" will fail, such as "`ADT`", "`ABC-DT01`", etc.
`.*DT.*` | This time, the "`.*`" symbol combination is used both before and after the text "`DT`", meaning that any number of characters (including zero characters) can occur before or after the text "`DT`". | "`DT`" matches because it technically has zero characters before and after it (tricky, isn't it?). "`DT1`", "`ADT`", "`ADT1`", "`ABCDT01`", and "`ABC-DT-01`" all match. | Anything which doesn't contain "`DT`" will fail, such as "`ADIT`", "`TD`", or "`D-T`".
`DT[0-9]` | The "`[0-9]`" symbol combination means that any _single_ digit between 0 and 9 is allowed after the text "`DT`". | "`DT0`", "`DT1`", "`DT2`" up to "`DT9`" will all match | Anything which doesn't have _only_ a single digit after "`DT`" will fail, like "`DT`", "`DTA`", and "`DT123`"
`DT[0-9]*` | When the "`*`" symbol is used after the "`[0-9]`" symbol to create "`[0-9]*`", it means that you can have any number of digits (including zero!) after the text "`DT`". | "`DT`", "`DT1`", "`DT12`", "`DT012345`", etc will match | Any value which has a non-digit after "`DT`" will fail, like "`DTABC`", "`DT01A`", "DTA1B2", etc.
`DT[0-9]{2}` | This time, instead of adding the "`*`" symbol, we add the "`{2}`" symbol, which means that you want exactly two digits after "`DT`". | "`DT01`", "`DT24`", "`DT99`", etc all match | Anything other than 2 digits will fail, like "`DTA`", "`DT0`", or "`DT123`".

**Regex** is a well-established methodology and can achieve very advanced pattern matching, but can take a while to fully learn its capabilities. As a result, only a few basic examples are shown here. Teaching the full capabilities is outside the scope of the IDS documentation. To make full use of it, there are plenty of online tutorials and resources:

 - [Beginners Regex tutorial](https://regexone.com/)
 - [Online Regex testing website](https://regex101.com/)
