.. _tunits:

tunits — Convert table column from one set of units to another
==============================================================

**Package: nttools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tunits -- Convert a table column from one set of units to another
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tunits table column newunits
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Tunits converts a column in a table from one set of units to
  another. It supports both scalar and array columns. You supply the
  table and column name and the new units you want the column to be
  in. Optionally, you can apply the current column units if the units
  string stored in the table is missing or incorrect. Tunits only
  supports multiplicative conversions, conversions that involve additive
  changes, like Kelvin to Celsius, are not supported. Unit names and
  conversions are read from two tables. You can copy these tables and
  edit them if you want to add new conversions.
  <P>
  You can find out the current units for a table column by running
  tlcol. If a units conversion is not supported by this task and you
  know the conversion formula, you can run tcalc.
  <P>
  Tunits must parse the unit strings you pass it, which requires that
  they follow a certain set of rules. Units can be a simple units name,
  such as ergs, or a units name raised to a power, such as meters^2, or
  the product or quotient of units names raised to a power, such as
  feet/sec or gm*cm/s^2. If two units names are next to each other
  without any operator between them, a multiplication is assumed. If a
  units name is followed by a number, the units name is assumed to be
  raised to that power.
  <P>
  Powers can also be specified by preceding the unit name with the
  string "<TT>square</TT>", "<TT>sq</TT>", "<TT>cubic</TT>", or "<TT>cu</TT>". For example, "<TT>square meter</TT>"
  is equivalent to "<TT>meter^2</TT>".
  <P>
  The operators recognized are:
  <P>
  <PRE>
  division	/ or per
  multiplication	*
  exponentiation	^ or **
  </PRE>
  <P>
  Division has the lowest priority and exponentiation the highest. This
  means ergs/sec*angstrom is interpreted as ergs/(sec*angstrom) and not
  (ergs/sec)*angstrom, as it would be in most computer languages. The
  default priority can be changed by changed by grouping terms with
  parentheses. 
  <P>
  Each set of units can have several synonymous names. These names are
  listed in the abbreviations table. Case is not significant in names
  and regular plurals (made by adding an "<TT>s</TT>") are converted to the
  singular. Names should contain only alphabetic characters.  Blanks,
  underscores and digits are not allowed.
  <P>
  The conversions supported by this task are read from the units
  conversion table. The table lists the old and new units and a
  conversion factor. Only one conversion is allowed for each set of
  units. 
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>table [file]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='table' Line='table [file]'>
  <DD>The name of the table the conversion is applied to.
  </DD>
  </DL>
  <DL>
  <DT><B>column [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='column' Line='column [string]'>
  <DD>The column to be converted. Both scalar and array columns are
  supported.
  </DD>
  </DL>
  <DL>
  <DT><B>newunits [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='newunits' Line='newunits [string]'>
  <DD>The new set of units for the column. The format of this parameter is
  described above. This task writes the new units to the units field in
  the table column.
  </DD>
  </DL>
  <DL>
  <DT><B>(oldunits = "<TT> </TT>") [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(oldunits = " ") [string]'>
  <DD>The units that the table column is currently in. If the value of this
  parameter is blank, the units will be read from the table.
  </DD>
  </DL>
  <DL>
  <DT><B>(abrevtab = "<TT>ttools$tunits/abrev.tab</TT>") [file]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(abrevtab = "ttools$tunits/abrev.tab") [file]'>
  <DD>A table of alternate names for each unit. This table contains two
  columns. The first column is the name of the units and the second
  column is the standard abbreviation. Because the default table is an
  ascii file, columns are read positionally and not by column names
  <P>
  Many units have more than one name or abbreviation. Using a standard
  abbreviation allows units to be converted to a standard form, which
  simplifies calculations. The standard abbreviation is used internally
  when computing the conversion factor. Case is not significant in names
  and regular plurals (made by adding an "<TT>s</TT>") are converted to the
  singular before looking them up in the table. Names should contain
  only alphabetic characters.  Blanks, underscores and digits are not
  allowed.
  <P>
  The name of this table is a parameter to allow you to create your own
  table of standard abbreviations, with additional units.
  </DD>
  </DL>
  <DL>
  <DT><B>(unittab = "<TT>ttools$tunits/units.tab</TT>") [file]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(unittab = "ttools$tunits/units.tab") [file]'>
  <DD>A table of conversion factors from one set of units into another.
  This table contains four columns. The first is the conversion factor,
  a double precision number. The second is the units the task tries to
  convert from. The third column is the units the task tries to convert
  to. The fourth column is contains the boolean variable swap, explained
  a little later. 
  <P>
  The table is interpreted as "<TT>There are &lt;factor&gt; &lt;from&gt; in a &lt;to&gt;.</TT>"
  For example, "<TT>There are 100 centimeters in a meter.</TT>"  The last column,
  swap, does not change the sense of the sentence but does change the
  direction that the conversion is applied, For example, "<TT>60 seconds in
  a minute</TT>" is actually a conversion from minutes to seconds because
  swap is yes. Unit conversions should set swap to yes when the desired
  conversion is not an exact value, but its inverse is. Only one
  conversion is allowed per unit, which simplifies the program logic
  considerably. Conversions should be chosen so that they ultimately
  resolve to MKS units. To prevent endless loops conversions from the
  fundamental units of MKS are checked for and forbidden. However, the
  program does not check for other loops, so be careful when adding new
  conversions!
  <P>
  As in the case of the abbreviation table, the table name is a
  parameter to allow you to create your own table with additional unit
  conversions. 
  </DD>
  </DL>
  <DL>
  <DT><B>(verbose = no) [bool]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(verbose = no) [bool]'>
  <DD>If you set this parameter to yes, the task will print a message to
  STDERR for each units conversion utilized in computing the conversion
  factor.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  Convert watts to ergs per second. Print the diagnostic messages:
  <P>
  <PRE>
  tt&gt; tunits source.tab power "ergs/sec" old=watts verb+
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>References</H3>
  <! BeginSection: 'REFERENCES'>
  <UL>
  This task was written by Bernie Simon
  </UL>
  <! EndSection:   'REFERENCES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  tlcol, tcalc
  <P>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'REFERENCES' 'SEE ALSO'  >
  
