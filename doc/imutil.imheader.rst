imheader — Print an image header
================================

**Package: imutil**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>imheader (Jun97)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.imutil</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>imheader (Jun97)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>imheader</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  imheader -- list header parameters for a list of images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  imheader [images]
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_images">images</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of IRAF images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_imlist">imlist = "<TT>*.imh,*.fits,*.pl,*.qp,*.hhh</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imlist' Line='imlist = "*.imh,*.fits,*.pl,*.qp,*.hhh"'>
  <DD>The default IRAF image name template.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_longheader">longheader = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='longheader' Line='longheader = no'>
  <DD>Print verbose image header.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_userfields">userfields = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='userfields' Line='userfields = yes'>
  <DD>If longheader is set print the information in the user area.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  IMHEADER prints header information in various formats for the list of IRAF
  images specified by <I>images</I>, or by the default image name template
  <I>imlist</I>. If <I>longheader</I> = no, the image name,
  dimensions, pixel type and title are printed. If <I>longheader</I> = yes,
  information on the create and modify dates, image statistics and so forth
  are printed. Non-standard IRAF header information can be printed by
  setting <I>userfields</I> = yes.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Print the header contents of a list of IRAF fits images.
  <P>
  <PRE>
  	cl&gt; imheader *.fits
  </PRE>
  <P>
  2. Print the header contents of a list of old IRAF format images in verbose
  mode.
  <P>
  <PRE>
  	cl&gt; imheader *.imh lo+
  </PRE>
  <P>
  3. Print short headers for all IRAF images of all types, e.g. imh, fits etc
  in the current directory.
  <P>
  <PRE>
  	cl&gt; imheader
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imgets, hedit, hselect
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>