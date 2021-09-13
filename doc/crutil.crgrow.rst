crgrow — Grow cosmic rays in cosmic ray masks
=============================================

**Package: crutil**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>crgrow (Apr98)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.crutil</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>crgrow (Apr98)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>crgrow</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  crgrow -- grow cosmic rays in cosmic ray masks
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage_">USAGE	</A></H2>
  <! BeginSection: 'USAGE	'>
  <UL>
  crgrow input output radius
  </UL>
  <! EndSection:   'USAGE	'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of cosmic ray masks to be modified.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output modified cosmic ray masks.  The input and output lists must
  match.  If the input and output cosmic ray masks are specified as the same
  then the input mask will be modified in place.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_radius">radius = 1.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='radius' Line='radius = 1.'>
  <DD>Replacement radius around cosmic rays.
  If a pixel is within this distance of a cosmic ray pixel
  it is identified by a value of 1 in the output cosmic ray mask.  Distances are
  measured between pixel centers which are have integer coordinates.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_inval">inval = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='inval' Line='inval = INDEF'>
  <DD>Mask value to be grown.  A value of INDEF will grow all non-zero values.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_outval">outval = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outval' Line='outval = INDEF'>
  <DD>Mask value for grown pixels.  A value of INDEF will use the value of the
  pixel being grown for the grown pixel value.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The cosmic ray pixels, identified by the "<TT>inval</TT>" parameter, in the input
  mask are located and all unmasked (zero valued) pixels within the specified
  grow radius are set to a value given by the "<TT>outval</TT>" parameter. The
  distance between pixels is measured as a cartisian logical pixel coordinate
  distance.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  A radius of 1 will grow cosmic rays in a "<TT>plus</TT>" pattern.
  <P>
  <PRE>
      cl&gt; crgrow crmask1 crmask2 1
  </PRE>
  <P>
  2.  A radius of 1.5 will grow cosmic rays in a box pattern.  The following
  will modify the input mask.
  <P>
  <PRE>
      cl&gt; crgrow crmask crmask 1.5
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imreplace
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>