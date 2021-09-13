.. _tbsort:

tbsort — Sort a list of apphot/daophot tables databases
=======================================================

**Package: ptools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tbsort -- sort an APPHOT/DAOPHOT STSDAS table database on one or more columns
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tbsort table columns
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>table</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='table' Line='table'>
  <DD>The list of APPHOT/DAOPHOT table databases to be sorted in-place.
  All tables are sorted on the same column or columns.
  </DD>
  </DL>
  <DL>
  <DT><B>columns</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='columns' Line='columns'>
  <DD>The list of columns to sort on.  A column template consists of a list of
  either column names, or column patterns containing the usual pattern matching
  meta-characters.  The names or patterns are separated by commas or white space.
  The list can be placed in a file and the name of the file preceeded by a
  <TT>'@'</TT> can be given in place of the column template.
  </DD>
  </DL>
  <DL>
  <DT><B>ascend = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ascend' Line='ascend = yes'>
  <DD>If <I>ascend</I> = yes, the table is sorted in ascending value order, with the
  first
  row containing the smallest value of the sorted column.  Otherwise, the table
  is sorted in descending order, with the largest value first.
  </DD>
  </DL>
  <DL>
  <DT><B>casesens = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='casesens' Line='casesens = yes'>
  <DD>If <I>casesens</I> = yes, sorts on character columns are case sensitive,
  with upper case letters preceding lower case in the sort.
  Otherwise, the sort is case insensitive.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  TBSORT sorts an APPHOT/DAOPHOT STSDAS table database.
  TBSORT operates in place so
  a copy of the unsorted table must be made with the TABLES
  package TCOPY task in order to preserve the original table.
  The column or columns to sort on are specified by the parameter
  <I>columns</I>, which is a list of column names or column name patterns
  separated by
  commas.  The most significant column name is the first in the list. Subsequent
  columns are used to break ties.  There are two flags, <I>ascend</I>
  and <I>casesens</I>.  If <I>ascend</I> is yes,
  the first row in the output table holds the smallest value if
  the sorted column is numeric or the first string in alphabetic order if the
  sorted column is a character string.  If <I>casesens</I> is yes,
  upper case characters
  precede lower case characters in sort order.  Otherwise, case is not significant
  in determining the sort order.  No precedes yes when sorting a boolean column
  in ascending order.  Null table elements always are last in the sort, regardless
  of whether <I>ascend</I> is yes or no. 
  <P>
  TBSORT is identical  to the TABLES package sort with the exception that
  it has its own copy of the default parameter set so that users
  can modify the parameters independently of the TBSORT task in TABLES.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Sort the output of the DAOPHOT ALLSTAR task in increasing order of
  magnitude.
  <P>
  <PRE>
     pt&gt; tbsort m92.al.1 MAG
  </PRE>
  <P>
  2. Sort the output of the DAOPHOT task NSTAR in increasing order of
  the y position.
  <P>
  <PRE>
     pt&gt; tbsort m92.nst.1 YCENTER
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ptools.txsort,ptools.psort,tables.tbsort
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
