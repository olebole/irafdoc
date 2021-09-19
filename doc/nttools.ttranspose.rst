.. _ttranspose:

ttranspose: Transpose or flip a table.
======================================

**Package: nttools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  ttranspose -- Transpose or flip a table.
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  ttranspose intable outtable action
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This task can be used to transpose a table
  so that input rows become output columns
  and input columns become output rows.
  Another option is to flip the table horizontally,
  that is, the first input column is the last output column.
  Finally, the table can be flipped vertically,
  i.e., the first input row is the last output row.
  Any combination of these operations may be performed.
  </p>
  <p>
  If the table is actually transposed
  (rather than just flipped horizontally and/or vertically),
  the data types of all input columns must be the same.
  In addition, if the columns contain arrays rather than scalars,
  all the array lengths must be the same.
  The data type and array size will be preserved in the output table,
  but the column names of the output table will be <tt>"c1"</tt>, <tt>"c2"</tt>, <tt>"c3"</tt>, etc,
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
  </p>
  <p>
  If the table is only flipped but not transposed,
  the above restrictions on data type do not apply,
  and the column names, units and print formats will be preserved.
  Note that an operation such as <tt>"tht"</tt>
  (which happens to be equivalent to <tt>"v"</tt>)
  does not actually transpose the table,
  so the data types of the columns need not all be the same.
  </p>
  <p>
  The 'tstat' task gives statistics for the values in a column,
  so one application of 'ttranspose' is to get statistics on
  the values in a row by first transposing the table and then running 'tstat'.
  </p>
  <p>
  Text tables with too many rows cannot be transposed
  due to the limit of 1024 on the length of each row of a text table.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>intable [file name template]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name template]' -->
  <dd>The list of input table names.
  </dd>
  </dl>
  <dl>
  <dt><b>outtable [file name template]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable [file name template]' -->
  <dd>The list of output table names.
  There must be the same number of input and output names.
  If the output is to be written to the standard output, however,
  you can use outtable = <tt>"STDOUT"</tt> even if there several input tables.
  </dd>
  </dl>
  <dl>
  <dt><b>action = <tt>"t"</tt> [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='action' Line='action = "t" [string]' -->
  <dd>This is a string made up of the letters <tt>"t"</tt>, <tt>"h"</tt>, and <tt>"v"</tt>
  which specify the operations to perform on the tables.
  <tt>"t"</tt> means transpose (input rows become output columns),
  <tt>"h"</tt> means flip horizontally (reverse the order of the columns),
  and <tt>"v"</tt> means flip vertically (reverse the order of the rows).
  The operations are performed in the order given from left to right.
  Any combination of <tt>"t"</tt>, <tt>"h"</tt>, and <tt>"v"</tt> may be used,
  in any order, and the letters may be repeated.
  Operations such as <tt>"tt"</tt>, <tt>"hh"</tt> or <tt>"vv"</tt> are valid,
  and they result in a simple copy of input to output.
  The symbols <tt>"/"</tt>, <tt>"-"</tt> and <tt>"|"</tt> are equivalent to
  the letters <tt>"t"</tt>, <tt>"h"</tt> and <tt>"v"</tt> respectively.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = yes [boolean]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes [boolean]' -->
  <dd>Print the names of the tables as they are processed?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1.  The input is the text file <tt>"in"</tt>,
  and the output is to be displayed on the screen.
  Each of the three operations (<tt>"t"</tt>, <tt>"h"</tt>, <tt>"v"</tt>)
  and some combinations are illustrated.
  </p>
  <pre>
  	tt&gt; type in
  	one     two     three
  	four    five    six
  	seven   eight   nine
  	ten     eleven  twelve
  
  	tt&gt; ttranspose in STDOUT t
  	in --&gt; STDOUT
  	one    four   seven  ten   
  	two    five   eight  eleven
  	three  six    nine   twelve
  
  	tt&gt; ttranspose in STDOUT h
  	in --&gt; STDOUT
  	three  two    one  
  	six    five   four 
  	nine   eight  seven
  	twelve eleven ten  
  
  	tt&gt; ttranspose in STDOUT v
  	in --&gt; STDOUT
  	ten   eleven twelve
  	seven eight  nine  
  	four  five   six   
  	one   two    three 
  
  	tt&gt; ttranspose in STDOUT hv
  	in --&gt; STDOUT
  	twelve eleven ten  
  	nine   eight  seven
  	six    five   four 
  	three  two    one  
  
  	tt&gt; ttranspose in STDOUT th
  	in --&gt; STDOUT
  	ten    seven  four   one   
  	eleven eight  five   two   
  	twelve nine   six    three 
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>References</h3>
  <!-- BeginSection: 'REFERENCES' -->
  <p>
  This task was written by Phil Hodge.
  </p>
  <!-- EndSection:   'REFERENCES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  Type <tt>"help ttools opt=sys"</tt> for a description of the 'tables' package.
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  -->
  
