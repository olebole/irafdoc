.. _istable:

istable — Is a file a table or text database file ?
===================================================

**Package: ptools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  istable --  determine the status of a file
  <P>
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  istable infile
  <P>
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <P>
  <DL>
  <DT><B>infile</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='infile' Line='infile'>
  <DD>The name of the input file whose status is to be determined.
  </DD>
  </DL>
  <DL>
  <DT><B>table = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='table' Line='table = no'>
  <DD>An output variable which is "<TT>yes</TT>" if <I>infile</I> is an STSDAS table
  and "<TT>no</TT>" otherwise.
  </DD>
  </DL>
  <DL>
  <DT><B>text = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='text' Line='text = no'>
  <DD>An output variable which is "<TT>yes</TT>" if <I>infile</I> is an APPHOT/DAOPHOT
  text database and "<TT>no</TT>" otherwise.
  </DD>
  </DL>
  <DL>
  <DT><B>other = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='other' Line='other = no'>
  <DD>An output variable which is "<TT>yes</TT>" if <I>infile</I> is neither of the
  above and "<TT>no</TT>" otherwise.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  ISTABLE is a very simple task which determines whether a specified
  input file is an STSDAS table, an APPHOT/DAOPHOT text database file or 
  neither of the above. ISTABLE first tries to open the input file as an 
  STSDAS table. If successful ISTABLE returns "<TT>yes</TT>" in the
  variable <I>table</I> and "<TT>no</TT>" in <I>text</I> and <I>other</I>. Otherwise
  ISTABLE  tries to open the input file as an APPHOT/DAOPHOT text database
  file by checking for the "<TT>#K IRAF</TT>" keyword.
  If the check is positive ISTABLE return "<TT>yes</TT>" in
  the variable <I>text</I> and "<TT>no</TT>" in <I>table</I> and <I>other</I>. If the input
  file is neither an STSDAS table or an APPHOT/DAOPHOT text database
  ISTABLE returns "<TT>yes</TT>" in the variable <I>other</I> and "<TT>no</TT>" in <I>text</I>
  and <I>table</I>.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Determine whether the file n4147.mag.1 is an STSDAS table.
  <P>
  <PRE>
     pt&gt; istable n4147.mag
     pt&gt; =istable.table
  <P>
         ... answer will appear on the screen
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
  Users should be wary of running ISTABLE in background as the output
  CL parameters may not be properly updated. 
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
