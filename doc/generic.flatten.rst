.. _flatten:

flatten — Flatten images using a flat field
===========================================

**Package: generic**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  flatten -- Flatten images by dividing by a flat field
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  flatten images flatfield
  </UL>
  <! EndSection:   'USAGE	'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>Images to be flattened.
  </DD>
  </DL>
  <DL>
  <DT><B>flatfield</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='flatfield' Line='flatfield'>
  <DD>Flat field image to be divided into the images.
  </DD>
  </DL>
  <DL>
  <DT><B>minflat = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='minflat' Line='minflat = INDEF'>
  <DD>All flat field pixels less than or equal to this value are replaced by
  unit response.  If INDEF all the flat field pixels are used.
  </DD>
  </DL>
  <DL>
  <DT><B>pixtype = "<TT>real</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pixtype' Line='pixtype = "real"'>
  <DD>The pixel datatype of the flattened image.  The null string ("<TT></TT>") defaults
  the pixel datatype to that of the original image before flattening.
  The other choices are "<TT>short</TT>", "<TT>integer</TT>", "<TT>long</TT>", and "<TT>real</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
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
  <H3>Examples</H3>
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
  
