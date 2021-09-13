.. _txsort:

txsort — Sort a list of apphot/daophot text databases
=====================================================

**Package: ptools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  txsort -- sort a list of APPHOT/DAOPHOT text database file(s)
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  txsort textfile field
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>textfiles </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='textfiles' Line='textfiles '>
  <DD>The input APPHOT/DAOPHOT text database(s) to be sorted.
  The sort is performed in place.
  </DD>
  </DL>
  <DL>
  <DT><B>field</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='field' Line='field'>
  <DD>The field to be sorted on. <I>Field</I> may be any quantity defined by
  the APPHOT/DAOPHOT #K and #N keywords. The keywords may be
  of type integer or real, in which case a numeric sort is performed,
  boolean, in which case the boolean constant "<TT>no</TT>" has a smaller value
  than "<TT>yes</TT>", or character in which case an alphabetic sort is performed.
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
  TXSORT is a simple task which accepts a list of APPHOT/DAOPHOT text
  database files
  and sorts them in place based on the value of the selected field
  specifier <I>field</I>. By default the sort is performed in increasing order
  of the value
  of <I>field</I>, but a reverse sort can be performed by 
  setting <I>ascend</I> = "<TT>no</TT>".
  <P>
  If <I>field</I> is a real or integer quantity the sort is numeric; if boolean
  the boolean constant "<TT>no</TT>" is assumed to have a smaller value than "<TT>yes</TT>"; if
  character the sort is alphabetic.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1.  Sort the output of the APPHOT task PHOT in increasing order of
  the y position.
  <P>
  <PRE>
      pt&gt; txsort m92.mag.1 YCENTER
  </PRE>
  <P>
  2. Sort the output of the DAOPHOT task ALLSTAR in increasing order of
     magnitude.
  <P>
  <PRE>
      pt&gt; txsort m92.al.1 MAG
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
  ptools.tbsort,tables.tsort,ptools.psort,sort
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
