.. _gkidir:

gkidir — Directory listing of metacode file
===========================================

**Package: plot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  gkidir -- print directory of plots within the named metacode file
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  gkidir input
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The metacode file or files to be examined.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Task <B>gkidir</B> examines GKI metacode files, and prints a directory of
  the plots contained in each input file.  Each plot is listed with its
  size and an identifying title string.  The title string is the MFTITLE
  string if given, or else the longest GTEXT string found (hopefully the
  plot title), or else the string "<TT>(no title)</TT>".  The output format is as
  follows:
  <PRE>
  <P>
  	file1: 
  	    [1] (1234 words)	title_string
  	    [2] (78364 words)	title_string
  <P>
  	file2:
  	    [1] (874 words)	title_string
  		.
  		.
  		.
  <P>
  </PRE>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. List the plots in the GKI metacode file "<TT>file</TT>":
  <P>
      cl&gt; gkidir file
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  gkiextract
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
