chkconfig — Check the configuration file for grammar and syntax errors
======================================================================

**Package: photcal**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>chkconfig (Aug91)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.photcal</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>chkconfig (Aug91)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>chkconfig</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  chkconfig -- Check the grammar and syntax of the configuration file
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  chkconfig config
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_config">config</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='config' Line='config'>
  <DD>The name of the configuration file to be checked. <I>Config</I> is the
  text file specifying both the format of the input files, and the form of
  transformation equations.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print detailed diagnostic information on the standard output ?
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  CHKCONFIG parses the configuration file <I>config</I> line by line,
  searching for syntax and/or semantic errors.  Its primary function is to aid
  the user in setting up a complete and correct set of transformation
  equations to be fit.  CHKCONFIG is run automatically by the task MKCONFIG,
  but can also be run stand-alone at any time.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  Check the configuration file for grammar and syntax errors.
  <P>
  <PRE>
  ph&gt; chk config
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  mkconfig,fitparams
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>