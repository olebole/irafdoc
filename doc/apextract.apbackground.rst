.. _apbackground:

apbackground — Background subtraction algorithms
================================================

**Package: apextract**

.. raw:: html

  
  </CENTER><BR>
  <P>
  <P>
  Data from slit spectra allow the determination and subtraction
  of the background sky using information from regions near the object
  of interest.  Background subtraction may also apply to cases of
  scattered light though other techniques for scattered light removal
  may be more appropriate.  The APEXTRACT package provides for determining
  the background level at each wavelength (line or column along the dispersion
  axis) from a set of regions and extrapolating and subtracting the
  background at each pixel extracted from the object profile.  The
  type of background used during extraction is specified by the parameter
  <I>background</I>.  If the value "<TT>none</TT>" is used then no background is
  subtracted and any background parameters defined for an aperture are
  ignored.  If the value is "<TT>average</TT>", "<TT>median</TT>", "<TT>minimum</TT>" or "<TT>fit</TT>" then a
  background is determined, including a variance estimate when using variance
  weighted extraction (see <I>apvariance</I>), and the subtracted background
  spectrum may be output if the <I>extras</I> parameter is set.
  <P>
  The basic aperture definition structure used in the APEXTRACT package
  includes associated background regions and fitting parameters.  The
  background regions are specified by a list of colon delimited ranges
  defined relative to the center of the aperture.  There are generally
  two ranges, one on each side of the object, though one sided or more
  complex sets may be used to avoid contaminated or missing parts
  of the slit.  The default ranges are defined by the parameter
  <I>b_sample</I>.  Often the ranges are better set graphically using a
  cursor by invoking the <TT>'b'</TT> option of the aperture editor.
  <P>
  If the background type is "<TT>average</TT>", "<TT>median</TT>", or "<TT>minimum</TT>" then pixels
  occupying these regions are averaged, medianed, or the minimum found to
  produce a single background level for all object pixels at each wavelength.  
  Note that the "<TT>average</TT>" choice does not exclude any pixels which may
  yield a background contaminated by cosmic rays.  The "<TT>median</TT>" or "<TT>minimum</TT>"
  is recommended instead.
  <P>
  If the background type is "<TT>fit</TT>" then a function is fit to the pixels in the
  background regions using the ICFIT options (see <B>icfit</B>).  The
  parameter <I>b_naverage</I> may be used to compute averages or medians of
  groups or all of the points within each sample region.  The fit is defined
  by a function type <I>b_function</I>; one of legendre polynomial, chebyshev
  polynomial, linear spline, or cubic spline, and function order
  <I>b_order</I> (number of polynomial terms or spline pieces).  An
  interactive rejection of grossly deviant points from the fit may also be
  used.  The fitted function can define a constant, sloped, or higher order
  background for the object pixels.
  <P>
  Note that the background setting function, the <TT>'b'</TT> key in <B>apedit</B>,
  may be used to set the background regions for all the background options
  but it will always show the result of a fit regardless of the background
  type.
  <P>
  After determining a background by averaging, medianing, minimizing, or
  fitting, a box car smoothing step may be applied.  The box car size is
  given by the parameter <I>skybox</I>.  When the number of available
  background pixels is small, due to a small slit for instance, the noise
  introduced to the extracted object spectrum may be unsatisfactorily large.
  By smoothing the background one can reduce the noise when the background
  consists of a smooth continuum.  The trade-off, however, is that near sharp
  features the smoothing will smear the features out and give a poorer
  subtraction of these features.  One could extract both the object and
  background separately and apply a background smoothing separately using
  other image processing tools.  However, this is not possible for variance
  weighted extraction because of the intimate connection between the
  background levels, the profile determination, and the variance estimates
  based on both.  Thus, this smoothing feature is included.
  <P>
  The background determined by the methods outlined above is actually
  subtracted as a separate step during extraction.  The background
  is also used during profile fitting when cleaning or using variance
  weighted extraction.  See <B>apvariance</B> and <B>approfile</B> for
  further discussion.
  </UL>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  approfile apvariance apdefault icfit apall apsum
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'SEE ALSO'  >
  
