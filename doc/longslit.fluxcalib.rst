.. _fluxcalib:

fluxcalib — Apply flux calibration to images (obsolete)
=======================================================

**Package: longslit**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  fluxcalib -- Apply flux calibration
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  fluxcalib images fluxfile
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images to be flux calibrated.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output flux calibrated images.  The output images may be the same
  as the input images.  The output image will be of type real regardless
  of the input pixel type.
  </DD>
  </DL>
  <DL>
  <DT><B>fluxfile</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fluxfile' Line='fluxfile'>
  <DD>Flux calibration file from <B>onedspec.sensfunc</B>.
  </DD>
  </DL>
  <DL>
  <DT><B>fnu = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fnu' Line='fnu = no'>
  <DD>Convert the flux calibration to flux per unit frequency (F-nu)?
  </DD>
  </DL>
  <DL>
  <DT><B>exposure = "<TT>otime</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='exposure' Line='exposure = "otime"'>
  <DD>Exposure time keyword in image headers.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The specified images are flux calibrated using a flux calibration image
  file derived from the <B>onedspec</B> package using standard stars.
  The flux calibration pixel values are in magnitudes and the pixel coordinates
  are in wavelength.  The multiplicative calibration factor is given by the
  formula
  <P>
      factor = 10 ** (-0.4 * calibration) / exposure / dispersion.
  <P>
  Since the calibration data has units of (instrumental intensity) /
  (ergs/cm**2), the exposure time for the image must be in seconds and the
  pixel dispersion in wavelength/pixel to yield units of
  ergs/cm**2/sec/wavelength.
  <P>
  The calibration wavelengths are interpolated to the wavelengths
  of the image pixels and the correction applied to the pixel values.
  Note that the image pixel values are modified.
  <P>
  If flux per unit frequency is requested then the flux values are multiplied
  by
  <P>
  	wavelength ** 2 / velocity of light (in Angstroms/sec)
  <P>
  to yield units of ergs/cm**2/Hz/sec/(wavelength/Angstrom).  Note that normally
  the wavelength units should be Angstroms.
  <P>
  It is possible to flux calibrate images which are binned in logarithmic
  wavelength intervals.  The point to note is that the units of the flux
  calibrated image will be the same.  Therefore, rebinning to linear
  wavelength coordinates requires only interpolation and not flux conservation.
  When extracting standard stars from logarithmicaly bin spectra for determination
  of a flux calibration it is necessary to rebin the extracted one dimensional
  spectra to linear wavelength (required by <B>onedspec</B>) conserving
  flux so that the instrumental counts are preserved.
  <P>
  The image header keyword DISPAXIS must be present with a value of 1 for
  dispersion parallel to the lines (varying with the column coordinate) or 2
  for dispersion parallel to the columns (varying with line coordinate).
  This parameter may be added using <B>hedit</B>.  Note that if the image has
  been transposed (<B>imtranspose</B>) the dispersion axis should still refer
  to the original dispersion axis unless the physical world coordinate system
  is first reset (see <B>wcsreset\R).  This is done in order to allow images
  which have DISPAXIS defined prior to transposing to still work correctly
  without requiring this keyword to be changed.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  Standard stars were observed and extracted to one dimensional spectra.
  The standard stars are then used to determine a flux calibration using
  the fBonedspec</B> package.  A set of dispersion and extinction corrected
  images is flux calibrated in-place with the command
  <P>
  <PRE>
  	cl&gt; fluxcalib img* img* sens.0000
  </PRE>
  <P>
  where "<TT>sens.0000</TT>" is the calibration file produced by the task
  <B>onedspec.sensfunc</B>.
  <P>
  To keep the uncalibrated image:
  <P>
  <PRE>
  	cl&gt; fluxcalib n1ext.004 n1extf.004 sens.0000
  </PRE>
  <P>
  3.  If the DISPAXIS keyword is missing and the dispersion is running
  vertically (varying with the image lines):
  <P>
  <PRE>
  	cl&gt; hedit *.imh dispaxis 2 add+
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>FLUXCALIB V2.10</B></DT>
  <! Sec='REVISIONS' Level=0 Label='FLUXCALIB' Line='FLUXCALIB V2.10'>
  <DD>The output pixel type is now forced to be real.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  onedspec.standard onedspec.sensfunc
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
