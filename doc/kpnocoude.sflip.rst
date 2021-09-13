sflip — Flip data and/or dispersion coordinates in spectra
==========================================================

**Package: kpnocoude**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>sflip (Jul94)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.onedspec</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>sflip (Jul94)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>sflip</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  sflip -- Flip data and/or dispersion coordinates in spectra
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  sflip input output
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images containing spectra to be flipped.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Matching list of output image names for flipped spectra.
  If no list is specified then the flipped spectra will replace the input
  spectra.  If the output image name matching an input image name is the
  same then the flipped spectrum will replace the original spectrum.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_coord_flip">coord_flip = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coord_flip' Line='coord_flip = no'>
  <DD>Flip the dispersion coordinates?  If yes then the relationship between the
  logical pixel coordinates and the dispersion coordinates will be reversed so
  that the dispersion coordinate of the first pixel of the output image will
  correspond to the coordinate of the last pixel in the input image and
  vice-versa for the other endpoint pixel.  The physical coordinates
  will also be flipped.  Only the coordinate system along the dispersion
  axis is flipped.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_data_flip">data_flip = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='data_flip' Line='data_flip = yes'>
  <DD>Flip the order of the data pixels as they are stored in the image along
  the dispersion axis?  If yes then the first pixel in the input spectrum
  becomes the last pixel in the output spectrum along the dispersion
  axis of the image.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The dispersion coordinate system and/or the data in the spectra specified
  by the input list of images are flipped and stored in the matching output
  image given in the output list of images.  If the output image list is left
  blank or an output image name is the same as an input image name then the
  operation is done so that the flipped spectra in the image replace the
  original spectra.  All of the supported spectrum types are allowed; one
  dimensional images, collections of spectra in multispec format, and two and
  three dimensional spatial spectra in which one axis is dispersion.  In all
  cases the flipping affects only the dispersion axis of the image as
  specified by the DISPAXIS header keyword or the "<TT>dispaxis</TT>" parameter.  The
  parameters <I>coord_flip</I> and <I>data_flip</I> select whether the
  coordinate system and data are flipped.  If neither operation is selected
  then the output spectra will simply be copies of the input spectra.
  <P>
  Flipping of the coordinate system means that the relation between
  "<TT>logical</TT>" pixel coordinates (the index system of the image array)
  and the dispersion and physical coordinate systems is reversed.
  The dispersion coordinate of the first pixel in the flipped spectrum
  will be the same as the dispersion coordinate of the last pixel
  in the original spectrum and vice-versa for the other endpoint.
  <P>
  Flipping of the data means that the order in which the pixels are stored
  in the image file is reversed along the image axis corresponding to
  the dispersion.
  <P>
  While flipping spectra seems simple there are some subtleties.  If
  both the coordinate system and the data are flipped then plots of
  the spectra in which the dispersion coordinates are shown will appear
  the same as in the original spectra.  In particular the coordinate
  of a feature in the spectrum will remain unchanged.  In contrast
  flipping either the coordinate system or the data will cause features
  in the spectrum to move to opposite ends of the spectrum relative
  to the dispersion coordinates.
  <P>
  Since plotting programs often plot the dispersion axis in some standard way
  such as increasing from left to right, flipping both the dispersion
  coordinates and the data will produce plots that look identical even though
  the order of the points plotted will be reversed.  Only if the spectra are
  plotted against logical pixel coordinates will a change be evident.  Note
  also that the plotting programs themselves have options to reverse the
  displayed graph.  So if all one wants is to reverse the direction of
  increasing dispersion in a plot then physically flipping of the spectra is
  not generally necessary.
  <P>
  Flipping of both the coordinate system and the data is also equivalent
  to using an image section with a reversed axis.  For example
  a one dimensional spectrum can be flipped in both dispersion coordinates
  and data pixel order by
  <P>
  <PRE>
      cl&gt; imcopy spec1[-*] spec2
  </PRE>
  <P>
  Higher dimensional spectra need appropriate dimensions in the image
  sections.  One advantage of <B>sflip</B> is that it will determine the
  appropriate dispersion axis itself.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  In the following the spectra can be one dimensional, multispec,
  long slit, or spectral data cubes.
  <P>
  <PRE>
      cl&gt; sflip spec1 spec1f		# Flip data to new image
      cl&gt; sflip spec1 spec1		# Flip data to same image
      cl&gt; sflip spec1 spec1f coord+ data-	# Flip coordinates and not data
      cl&gt; sflip spec1 spec1f coord+ 	# Flip both coordinates and data
      cl&gt; sflip spec* f//spec*		# Flip a list of images
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_SFLIP">SFLIP V2.10.4</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='SFLIP' Line='SFLIP V2.10.4'>
  <DD>New in this release.  Note that the V2.9 SFLIP was different in that
  it was script which simply flipped the data.  Coordinate systems were
  not handled in the same way.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imcopy, scopy, dispcor, sapertures
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>