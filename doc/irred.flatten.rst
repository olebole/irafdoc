flatten — Flatten images using a flat field
===========================================

**Package: irred**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>flatten (Sep84)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.generic</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>flatten (Sep84)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>flatten</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  flatten -- Flatten images by dividing by a flat field
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage_">USAGE	</A></H2>
  <! BeginSection: 'USAGE	'>
  <UL>
  flatten images flatfield
  </UL>
  <! EndSection:   'USAGE	'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_images">images</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>Images to be flattened.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_flatfield">flatfield</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='flatfield' Line='flatfield'>
  <DD>Flat field image to be divided into the images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_minflat">minflat = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='minflat' Line='minflat = INDEF'>
  <DD>All flat field pixels less than or equal to this value are replaced by
  unit response.  If INDEF all the flat field pixels are used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_pixtype">pixtype = "<TT>real</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pixtype' Line='pixtype = "real"'>
  <DD>The pixel datatype of the flattened image.  The null string ("<TT></TT>") defaults
  the pixel datatype to that of the original image before flattening.
  The other choices are "<TT>short</TT>", "<TT>integer</TT>", "<TT>long</TT>", and "<TT>real</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Each of the <I>images</I> is flatten by dividing by the <I>flatfield</I>
  flat field image.  The flattened images replace the original images.
  The pixel datatype of the flattened images is specified by the
  <I>pixtype</I>.  The null string ("<TT></TT>") leaves the datatype of the images
  unchanged.  Low values in the flat field may be replaced by unit response
  by specifying a <I>minflat</I> value.  All pixels in the flat field less
  than or equal to <I>minflat</I> are given unit response.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  To flatten a set of two dimensional images excluding pixels below
  <P>
  <PRE>
  	cl&gt; flatten frame* flat minflat=0.2
  </PRE>
  </UL>
  <! EndSection:    'EXAMPLES'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES'  >
  
  </BODY>
  </HTML>