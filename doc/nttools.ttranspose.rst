.. _ttranspose:

ttranspose — Transpose or flip a table.
=======================================

**Package: nttools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  ttranspose -- Transpose or flip a table.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  ttranspose intable outtable action
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task can be used to transpose a table
  so that input rows become output columns
  and input columns become output rows.
  Another option is to flip the table horizontally,
  that is, the first input column is the last output column.
  Finally, the table can be flipped vertically,
  i.e., the first input row is the last output row.
  Any combination of these operations may be performed.
  <P>
  If the table is actually transposed
  (rather than just flipped horizontally and/or vertically),
  the data types of all input columns must be the same.
  In addition, if the columns contain arrays rather than scalars,
  all the array lengths must be the same.
  The data type and array size will be preserved in the output table,
  but the column names of the output table will be "<TT>c1</TT>", "<TT>c2</TT>", "<TT>c3</TT>", etc,
  with default print format and null units.
  Actually, some mixing of data types is permitted.
  If some columns are type real and others are double precision,
  the output data type will be double precision.
  Similarly, short integers will be promoted to integers.
  Boolean columns can be mixed with any other data type;
  for numeric columns, yes becomes 1 and no becomes 0.
  When the columns in the input table are character strings,
  different maximum string lengths are permitted,
  and the output length will be the maximum of the input lengths.
  The restrictions on data type are not imposed on text tables,
  which can contain mixed integer, double precision and text columns.
  <P>
  If the table is only flipped but not transposed,
  the above restrictions on data type do not apply,
  and the column names, units and print formats will be preserved.
  Note that an operation such as "<TT>tht</TT>"
  (which happens to be equivalent to "<TT>v</TT>")
  does not actually transpose the table,
  so the data types of the columns need not all be the same.
  <P>
  The 'tstat' task gives statistics for the values in a column,
  so one application of 'ttranspose' is to get statistics on
  the values in a row by first transposing the table and then running 'tstat'.
  <P>
  Text tables with too many rows cannot be transposed
  due to the limit of 1024 on the length of each row of a text table.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>intable [file name template]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name template]'>
  <DD>The list of input table names.
  </DD>
  </DL>
  <DL>
  <DT><B>outtable [file name template]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable [file name template]'>
  <DD>The list of output table names.
  There must be the same number of input and output names.
  If the output is to be written to the standard output, however,
  you can use outtable = "<TT>STDOUT</TT>" even if there several input tables.
  </DD>
  </DL>
  <DL>
  <DT><B>action = "<TT>t</TT>" [string]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='action' Line='action = "t" [string]'>
  <DD>This is a string made up of the letters "<TT>t</TT>", "<TT>h</TT>", and "<TT>v</TT>"
  which specify the operations to perform on the tables.
  "<TT>t</TT>" means transpose (input rows become output columns),
  "<TT>h</TT>" means flip horizontally (reverse the order of the columns),
  and "<TT>v</TT>" means flip vertically (reverse the order of the rows).
  The operations are performed in the order given from left to right.
  Any combination of "<TT>t</TT>", "<TT>h</TT>", and "<TT>v</TT>" may be used,
  in any order, and the letters may be repeated.
  <P>
  Operations such as "<TT>tt</TT>", "<TT>hh</TT>" or "<TT>vv</TT>" are valid,
  and they result in a simple copy of input to output.
  <P>
  The symbols "/"<TT>, </TT>"-"<TT> and </TT>"|"<TT> are equivalent to
  the letters </TT>"t"<TT>, </TT>"h"<TT> and </TT>"v"<TT> respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes [boolean]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes [boolean]'>
  <DD>Print the names of the tables as they are processed?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  The input is the text file </TT>"in"<TT>,
  and the output is to be displayed on the screen.
  Each of the three operations (</TT>"t"<TT>, </TT>"h"<TT>, </TT>"v"<TT>)
  and some combinations are illustrated.
  <P>
  <PRE>
  	tt&gt; type in
  	one     two     three
  	four    five    six
  	seven   eight   nine
  	ten     eleven  twelve
  <P>
  	tt&gt; ttranspose in STDOUT t
  	in --&gt; STDOUT
  	one    four   seven  ten   
  	two    five   eight  eleven
  	three  six    nine   twelve
  <P>
  	tt&gt; ttranspose in STDOUT h
  	in --&gt; STDOUT
  	three  two    one  
  	six    five   four 
  	nine   eight  seven
  	twelve eleven ten  
  <P>
  	tt&gt; ttranspose in STDOUT v
  	in --&gt; STDOUT
  	ten   eleven twelve
  	seven eight  nine  
  	four  five   six   
  	one   two    three 
  <P>
  	tt&gt; ttranspose in STDOUT hv
  	in --&gt; STDOUT
  	twelve eleven ten  
  	nine   eight  seven
  	six    five   four 
  	three  two    one  
  <P>
  	tt&gt; ttranspose in STDOUT th
  	in --&gt; STDOUT
  	ten    seven  four   one   
  	eleven eight  five   two   
  	twelve nine   six    three 
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>References</H3>
  <! BeginSection: 'REFERENCES'>
  <UL>
  This task was written by Phil Hodge.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  Type </TT>"help ttools opt=sys"<TT> for a description of the 'tables' package.
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
