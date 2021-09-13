badpiximage — Create a bad pixel mask image from a bad pixel file
=================================================================

**Package: quadred**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>badpiximage (Jun87)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.ccdred</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>badpiximage (Jun87)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>badpiximage</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  badpiximage -- Create a bad pixel mask image from a bad pixel file
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  badpiximage fixfile template image
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_fixfile">fixfile</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fixfile' Line='fixfile'>
  <DD>Bad pixel file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_template">template</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='template' Line='template'>
  <DD>Template image used to define the size of the bad pixel mask image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_image">image</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>Bad pixel mask image to be created.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_goodvalue">goodvalue = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='goodvalue' Line='goodvalue = 1'>
  <DD>Integer value assigned to the good pixels.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_badvalue">badvalue = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='badvalue' Line='badvalue = 0'>
  <DD>Integer value assigned to the bad pixels.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  A bad pixel mask image is created from the specified bad pixel file.
  The format of the bad pixel file is that used by <B>ccdproc</B> to
  correct CCD defects (see instruments).  The bad pixel image is of pixel type short and
  has the value given by the parameter <B>goodvalue</B> for the good
  pixels and the value given by the parameter <B>badvalue</B> for the bad pixels.
  The image size and header parameters are taken from the specified
  template image.  The bad pixel mask image may be used to view the
  location of the bad pixels and blink against an data image using an
  image display, to mask or flag bad pixels later by image arithmetic,
  and to propagate the positions of the bad pixels through the
  reductions.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To make a bad pixel mask image from the bad pixel file "<TT>cryocambp.dat</TT>"
  using the image "<TT>ccd005</TT>" as the template:
  <P>
  	cl&gt; badpiximage cryocambp.dat ccd005 cryocambp
  <P>
  2. To make the bad pixel mask image with good values of 0 and bad values of 1:
  <P>
  	cl&gt; badpixim cryomapbp.dat ccd005 cryocambp good=0 bad=1
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ccdproc, instruments
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>