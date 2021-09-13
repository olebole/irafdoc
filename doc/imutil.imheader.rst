.. _imheader:

imheader — Print an image header
================================

**Package: imutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  imheader -- list header parameters for a list of images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  imheader [images]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of IRAF images.
  </DD>
  </DL>
  <DL>
  <DT><B>imlist = "<TT>*.imh,*.fits,*.pl,*.qp,*.hhh</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imlist' Line='imlist = "*.imh,*.fits,*.pl,*.qp,*.hhh"'>
  <DD>The default IRAF image name template.
  </DD>
  </DL>
  <DL>
  <DT><B>longheader = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='longheader' Line='longheader = no'>
  <DD>Print verbose image header.
  </DD>
  </DL>
  <DL>
  <DT><B>userfields = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='userfields' Line='userfields = yes'>
  <DD>If longheader is set print the information in the user area.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
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
  <H3>Examples</H3>
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
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imgets, hedit, hselect
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
