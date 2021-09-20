.. _fluxcalib:

fluxcalib: Apply flux calibration to images (obsolete)
======================================================

**Package: longslit**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  fluxcalib -- Apply flux calibration
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  fluxcalib images fluxfile
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>List of input images to be flux calibrated.
  </dd>
  </dl>
  <dl>
  <dt><b>output</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output' -->
  <dd>List of output flux calibrated images.  The output images may be the same
  as the input images.  The output image will be of type real regardless
  of the input pixel type.
  </dd>
  </dl>
  <dl>
  <dt><b>fluxfile</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fluxfile' Line='fluxfile' -->
  <dd>Flux calibration file from <b>onedspec.sensfunc</b>.
  </dd>
  </dl>
  <dl>
  <dt><b>fnu = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fnu' Line='fnu = no' -->
  <dd>Convert the flux calibration to flux per unit frequency (F-nu)?
  </dd>
  </dl>
  <dl>
  <dt><b>exposure = <span style="font-family: monospace;">"otime"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='exposure' Line='exposure = "otime"' -->
  <dd>Exposure time keyword in image headers.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The specified images are flux calibrated using a flux calibration image
  file derived from the <b>onedspec</b> package using standard stars.
  The flux calibration pixel values are in magnitudes and the pixel coordinates
  are in wavelength.  The multiplicative calibration factor is given by the
  formula
  </p>
  <p>
      factor = 10 ** (-0.4 * calibration) / exposure / dispersion.
  </p>
  <p>
  Since the calibration data has units of (instrumental intensity) /
  (ergs/cm**2), the exposure time for the image must be in seconds and the
  pixel dispersion in wavelength/pixel to yield units of
  ergs/cm**2/sec/wavelength.
  </p>
  <p>
  The calibration wavelengths are interpolated to the wavelengths
  of the image pixels and the correction applied to the pixel values.
  Note that the image pixel values are modified.
  </p>
  <p>
  If flux per unit frequency is requested then the flux values are multiplied
  by
  </p>
  <p>
  	wavelength ** 2 / velocity of light (in Angstroms/sec)
  </p>
  <p>
  to yield units of ergs/cm**2/Hz/sec/(wavelength/Angstrom).  Note that normally
  the wavelength units should be Angstroms.
  </p>
  <p>
  It is possible to flux calibrate images which are binned in logarithmic
  wavelength intervals.  The point to note is that the units of the flux
  calibrated image will be the same.  Therefore, rebinning to linear
  wavelength coordinates requires only interpolation and not flux conservation.
  When extracting standard stars from logarithmicaly bin spectra for determination
  of a flux calibration it is necessary to rebin the extracted one dimensional
  spectra to linear wavelength (required by <b>onedspec</b>) conserving
  flux so that the instrumental counts are preserved.
  </p>
  <p>
  The image header keyword DISPAXIS must be present with a value of 1 for
  dispersion parallel to the lines (varying with the column coordinate) or 2
  for dispersion parallel to the columns (varying with line coordinate).
  This parameter may be added using <b>hedit</b>.  Note that if the image has
  been transposed (<b>imtranspose</b>) the dispersion axis should still refer
  to the original dispersion axis unless the physical world coordinate system
  is first reset (see <b>wcsreset</b>).  This is done in order to allow images
  which have DISPAXIS defined prior to transposing to still work correctly
  without requiring this keyword to be changed.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  Standard stars were observed and extracted to one dimensional spectra.
  The standard stars are then used to determine a flux calibration using
  the <b>onedspec</b> package.  A set of dispersion and extinction corrected
  images is flux calibrated in-place with the command
  </p>
  <pre>
  	cl&gt; fluxcalib img* img* sens.0000
  </pre>
  <p>
  where <span style="font-family: monospace;">"sens.0000"</span> is the calibration file produced by the task
  <b>onedspec.sensfunc</b>.
  </p>
  <p>
  To keep the uncalibrated image:
  </p>
  <pre>
  	cl&gt; fluxcalib n1ext.004 n1extf.004 sens.0000
  </pre>
  <p>
  3.  If the DISPAXIS keyword is missing and the dispersion is running
  vertically (varying with the image lines):
  </p>
  <pre>
  	cl&gt; hedit *.imh dispaxis 2 add+
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Revisions</h3>
  <!-- BeginSection: 'REVISIONS' -->
  <dl>
  <dt><b>FLUXCALIB V2.10</b></dt>
  <!-- Sec='REVISIONS' Level=0 Label='FLUXCALIB' Line='FLUXCALIB V2.10' -->
  <dd>The output pixel type is now forced to be real.
  </dd>
  </dl>
  <!-- EndSection:   'REVISIONS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  onedspec.standard onedspec.sensfunc
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  -->
  
