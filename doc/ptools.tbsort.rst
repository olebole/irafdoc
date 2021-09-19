.. _tbsort:

tbsort: Sort a list of apphot/daophot tables databases
======================================================

**Package: ptools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  tbsort -- sort an APPHOT/DAOPHOT STSDAS table database on one or more columns
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  tbsort table columns
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>table</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='table' Line='table' -->
  <dd>The list of APPHOT/DAOPHOT table databases to be sorted in-place.
  All tables are sorted on the same column or columns.
  </dd>
  </dl>
  <dl>
  <dt><b>columns</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='columns' Line='columns' -->
  <dd>The list of columns to sort on.  A column template consists of a list of
  either column names, or column patterns containing the usual pattern matching
  meta-characters.  The names or patterns are separated by commas or white space.
  The list can be placed in a file and the name of the file preceeded by a
  <tt>'@'</tt> can be given in place of the column template.
  </dd>
  </dl>
  <dl>
  <dt><b>ascend = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ascend' Line='ascend = yes' -->
  <dd>If <i>ascend</i> = yes, the table is sorted in ascending value order, with the
  first
  row containing the smallest value of the sorted column.  Otherwise, the table
  is sorted in descending order, with the largest value first.
  </dd>
  </dl>
  <dl>
  <dt><b>casesens = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='casesens' Line='casesens = yes' -->
  <dd>If <i>casesens</i> = yes, sorts on character columns are case sensitive,
  with upper case letters preceding lower case in the sort.
  Otherwise, the sort is case insensitive.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  TBSORT sorts an APPHOT/DAOPHOT STSDAS table database.
  TBSORT operates in place so
  a copy of the unsorted table must be made with the TABLES
  package TCOPY task in order to preserve the original table.
  The column or columns to sort on are specified by the parameter
  <i>columns</i>, which is a list of column names or column name patterns
  separated by
  commas.  The most significant column name is the first in the list. Subsequent
  columns are used to break ties.  There are two flags, <i>ascend</i>
  and <i>casesens</i>.  If <i>ascend</i> is yes,
  the first row in the output table holds the smallest value if
  the sorted column is numeric or the first string in alphabetic order if the
  sorted column is a character string.  If <i>casesens</i> is yes,
  upper case characters
  precede lower case characters in sort order.  Otherwise, case is not significant
  in determining the sort order.  No precedes yes when sorting a boolean column
  in ascending order.  Null table elements always are last in the sort, regardless
  of whether <i>ascend</i> is yes or no. 
  </p>
  <p>
  TBSORT is identical  to the TABLES package sort with the exception that
  it has its own copy of the default parameter set so that users
  can modify the parameters independently of the TBSORT task in TABLES.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Sort the output of the DAOPHOT ALLSTAR task in increasing order of
  magnitude.
  </p>
  <pre>
     pt&gt; tbsort m92.al.1 MAG
  </pre>
  <p>
  2. Sort the output of the DAOPHOT task NSTAR in increasing order of
  the y position.
  </p>
  <pre>
     pt&gt; tbsort m92.nst.1 YCENTER
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  ptools.txsort,ptools.psort,tables.tbsort
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
