.. _extras:

extras — Information about the extra information in 3D images
=============================================================

**Package: apextract**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  extras -- Information about the extra bands in 3D output
  </UL>
  <! EndSection:   'NAME'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  When one dimensional spectra are extracted by the tasks in the
  <B>apextract</B> package the user may specify that additional
  extra associated information be extracted at the same time.  This
  information is produced when the <I>extras</I> parameter is "<TT>yes</TT>".
  <P>
  The associated information is recorded as additional "<TT>bands</TT>" (the IRAF term
  for the third dimension of a three dimensional image) of the output
  extracted spectral image.  Extracted spectra are currently stored as IRAF
  images with dispersion information given in the image header.  The
  image axes for such images are:
  <P>
  <PRE>
      1 (columns) - dispersion axis
      2 (lines)   - spectrum axis (each line is a separate spectrum)
      3 (bands)   - extras axis (each band is associated data)
  </PRE>
  <P>
  The lengths of the second and third axes, that is the number of
  lines and bands, may be one or more.  If there is only one band
  the image will be two dimensional and if there is only one line
  and one band the image will be one dimensional.  Note that the
  <I>format</I> parameter controls whether multiple apertures are
  written to separate images or to a single image.  Thus, if
  the format is "<TT>onedspec</TT>" this means that the second dimension
  will always be of length one and, if the <I>extras</I> parameter
  is no, the output images will be one dimensional.
  <P>
  The associated data in the image bands depends on which extraction
  options are performed.  The various types of data are:
  <P>
  <PRE>
      The primary spectrum flux values.
      Simple aperture sum if variance weighting or cleaning was done.
      Background spectrum if background subtraction was done.
      Sigma spectrum if variance weighting or cleaning was done.
  </PRE>
  <P>
  The primary spectrum is always the first band and will be the cleaned
  and/or variance weighted and/or background subtracted spectrum.  The
  simple aperture sum spectrum allows comparing against the results of the
  variance weighting or pixel rejection options.  When background
  subtraction is performed the subtracted background is recorded in
  one of the bands.  When variance weighting or pixel rejection is
  performed the software generates an estimate of the uncertainty
  in the extracted flux as a sigma.
  <P>
  The identity of the various bands is given by the image header
  keywords BANDIDn (where n is the band number).  This also serves
  to document which extraction options were used.
  <P>
  For more information get help under the topic "<TT>apextract.package</TT>".
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  apextract.package
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'DESCRIPTION' 'SEE ALSO'  >
  
