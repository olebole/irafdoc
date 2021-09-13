bases — Convert an integer to hex, octal, and binary
====================================================

**Package: utilities**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>bases (Jan85)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>utilities</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>bases (Jan85)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>bases</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  bases -- Convert an integer to hex, octal, and binary
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  bases i
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_i">i</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='i' Line='i'>
  <DD>Integer for base conversion.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nbyte">nbyte = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nbyte' Line='nbyte = 0'>
  <DD>Number of bytes of precision.  Allowed values are "<TT>0</TT>", "<TT>1</TT>", "<TT>2</TT>", or "<TT>4</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print labels for columns?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The BASES task converts an input integer value to equivalent values in
  other base systems.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Convert the number 256 (in various bases).  Note the <TT>'x'</TT> and <TT>'b'</TT> suffix
  appended to the value to change the input base value:
  <P>
  <PRE>
  	ecl&gt; bases 256					# decimal input
  	  dec    hex    octal   7654 3210 7654 3210
  	  256   0100x  000400b  0000 0001 0000 0000
  	ecl&gt; bases 256x					# hex input
  	  dec    hex    octal   7654 3210 7654 3210
  	  598   0256x  001126b  0000 0010 0101 0110
  	ecl&gt; bases 256b					# octal input
  	  dec  hex  oct   7654 3210
  	  174  AEx  256b  1010 1110
  <P>
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>