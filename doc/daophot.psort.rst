.. _psort:

psort — Sort a daophot database
===============================

**Package: daophot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  psort -- sort an APPHOT/DAOPHOT database file
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  psort infiles field
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>infiles</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='infiles' Line='infiles'>
  <DD>The input APPHOT/DAOPHOT databases to be sorted. The sort is performed in place.
  </DD>
  </DL>
  <DL>
  <DT><B>field</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='field' Line='field'>
  <DD>The field to be sorted on. If the input file is a text database,
  <I>field</I> may be any quantity defined by
  the APPHOT/DAOPHOT #K and #N keywords. If the input file is an STSDAS
  table database <I>field</I> may be any column name. <I>Field</I> may be
  of type integer or real, in which case a numeric sort is performed,
  boolean, in which case the boolean constant "<TT>no</TT>" is assumed to have a
  smaller value than "<TT>yes</TT>", or character in which case an alphabetic sort
  is performed.
  </DD>
  </DL>
  <DL>
  <DT><B>ascend = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ascend' Line='ascend = yes'>
  <DD>Sort in increasing value order.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  PSORT is a simple task which accepts an APPHOT/DAOPHOT database file
  and sorts it in place based on the value of the selected quantity
  <I>field</I>. By default the sort is in increasing order of the value
  of field, but a reverse sort can be performed by 
  setting <I>ascend</I> = no.
  <P>
  If <I>field</I> is a real or integer the sort is numeric, if boolean
  the constant "<TT>no</TT>" is assumed to have a smaller value than "<TT>yes</TT>", if
  character the sort is alphabetic.
  <P>
  PSORT is a simple CL script which call TXSORT if the input database is
  a text file and TSORT if the input database is a text file.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1.  Sort the output of the APPHOT task PHOT in increasing order of
  the y coordinate.
  <P>
  <PRE>
      pt&gt; psort m92.mag.1 YCENTER
  </PRE>
  <P>
  2. Sort the output of the DAOPHOT task ALLSTAR in increasing order of
  magnitude.
  <P>
  <PRE>
      pt&gt; psort m92.al.1 MAG
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ptools.txsort,tables.tsort,ptools.tbsort
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
