gkiextract — Extract individual frames from metacode file
=========================================================

**Package: plot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>gkiextract (Jan86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>plot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>gkiextract (Jan86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>gkiextract</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  gkiextract -- extract individual frames from a GKI metacode file
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  gkiextract input frames
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The metacode source file or files.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_frames">frames</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='frames' Line='frames'>
  <DD>List of frames to be extracted from each metacode file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verify">verify = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verify' Line='verify = no'>
  <DD>Verify each frame before extraction?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Task <B>gkiextract</B> will extract individual frames from a metacode file, 
  writing a binary metacode output stream which can be piped to a kernel
  for plotting or redirected to produce a new metacode file.  
  Parameter <I>frames</I> specifies a list of frames to be
  extracted from each input file.  If <I>verify</I>  = yes,
  a <B>gkidir</B> style line will be printed for each specified frame 
  and the user will be queried whether or not to extract the frame.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Extract frames 1, 3 and 5 from metacode file "<TT>mc_file</TT>" and
  plot them on the device "<TT>vup</TT>":
  <P>
      cl&gt; gkiextract mc_file 1,3,5 | stdplot dev=vup
  <P>
  2. Print a directory of the first 99 frames in "<TT>mc_file</TT>", extract
  those files requested by the user and write them to file "<TT>new_mc_file</TT>".
  <P>
      cl&gt; gkiextract mc_file 1-99 ver+ &gt; new_mc_file
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  A maximum of 8192 plots in a single metacode file may be processed.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  gkidir
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>