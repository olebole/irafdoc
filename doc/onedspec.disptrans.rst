disptrans — Transform dispersion units and apply air correction
===============================================================

**Package: onedspec**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>disptrans (Aug94)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.onedspec</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>disptrans (Aug94)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>disptrans</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  disptrans -- Transform dispersion units and apply air correction
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  disptrans input output units
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of dispersion calibrated input spectra to be dispersion transformed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output dispersion transformed spectra.  If given the input names
  (or a null list), each input spectrum will be replaced by the transformed
  output spectrum.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_units">units</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='units' Line='units'>
  <DD>Output dispersion units.  A wide range of dispersion units may be
  specified and they are described in the UNITS section.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_error">error = 0.01</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='error' Line='error = 0.01'>
  <DD>Maximum error allowed in the output dispersion transformation expressed
  as a pixel error; that is, the equivalent pixel shift in the output
  dispersion function corresponding to the maximum difference between
  the exact transformation and the dispersion function approximation.
  The smaller the allowed error the higher the order of dispersion
  function used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_linearize">linearize = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='linearize' Line='linearize = no'>
  <DD>Resample the spectrum data to linear increments in the output dispersion
  system?  If no then the output dispersion function is stored in the
  spectrum header and if yes the spectrum is resampled into the same
  number of pixels over the same dispersion range but in even steps
  of the output dispersion units.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print a log of each spectrum transformed to the standard output?
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_air">air = "<TT>none</TT>" (none|air2vac|vac2air)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='air' Line='air = "none" (none|air2vac|vac2air)'>
  <DD>Apply an air to vacuum or vacuum to air conversion?  It is the
  responsibility of the user to know whether the input dispersion
  is in air or vacuum units and to select the appropriate conversion.
  The conversion types are "<TT>none</TT>" for no conversion, "<TT>air2vac</TT>" to
  convert from air to vacuum, and "<TT>vac2air</TT>" to convert from vacuum
  to air.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_t">t = 15, p = 760, f = 4</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='t' Line='t = 15, p = 760, f = 4'>
  <DD>Temperature t in degrees C, pressure p in mmHg, and water vapour pressure f
  in mmHg for the air index of refraction.
  </DD>
  </DL>
  <P>
  OTHER PARAMETERS
  <P>
  <DL>
  <DT><B><A NAME="l_interp">interp = "<TT>poly5</TT>" (nearest|linear|poly3|poly5|spline3|sinc)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interp' Line='interp = "poly5" (nearest|linear|poly3|poly5|spline3|sinc)'>
  <DD>Spectrum interpolation type used when spectra are resampled.  The choices are:
  <P>
  <PRE>
  	nearest - nearest neighbor
  	 linear - linear
  	  poly3 - 3rd order polynomial
  	  poly5 - 5th order polynomial
  	spline3 - cubic spline
  	   sinc - sinc function
  </PRE>
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The dispersion function in the input spectra, y = f(x) where x is the
  pixel coordinate and y is the input dispersion coordinate, is
  transformed to y' = g(x) where y' is in the new dispersion units.  This is done
  by evaluating the input dispersion coordinate y at each pixel, applying an
  air to vacuum or vacuum to air conversion if desired, and applying the
  specified unit transformation y' = h(y).  Since the transformations are
  nonlinear functions and the output dispersion function must be expressed in
  polynomial form, the function g(x) is determined by fitting a cubic spline
  to the set of x and y' values.  The lowest number of spline pieces is used
  which satisfies the specified error.  Note that this error is not a random
  error but difference between the smooth fitted function and the smooth
  dispersion function in the header.  As a special case, the first
  fit tried is a linear function.  If this satisfies the error condition
  then a simpler dispersion description is possible.  Also this is
  appropriate for dispersion units which are simply related by a
  scale change such as Angstroms to nanometers or Hertz to Mev.
  <P>
  The error condition is that the maximum difference between the exact or
  analytic (the air/vacuum conversion is never exact) transformation and the
  fitted function value at any pixel be less than the equivalent shift in
  pixel coordinate evaluated at that point.  The reason for using an error
  condition in terms of pixels is that it is independent of the dispersion of
  the spectra and the resolution of spectra is ultimately limited by the
  pixel sampling.
  <P>
  After the new dispersion function is determined the function is either
  stored in the coordinate system description for the spectrum or used to
  resample the pixels to linear increments in the output dispersion units.
  The resampling is not done if the new dispersion function is already linear
  as noted above.  The sampling uses the mean value over the input spectrum
  covered by an output spectrum pixel (it is flux per unit dispersion element
  preserving as opposed to flux/counts preserving).  The linear sampling
  parameters are limited to producing the same number of output pixels as
  input pixels over the same range of dispersion.  If one wants to have more
  control over the resampling then the <I>linearize</I> parameter should be
  set to no and the task <B>dispcor</B> used on the output spectrum.
  <P>
  Note that an alternative to using this task is to do the original
  dispersion calibration (based on calibration spectra) with IDENTIFY
  and DISPCOR in the desired units.  However, currently the standard
  lines lists are in Angstroms.  There are, however, linelists for
  He-Ne-Ar, Th-Ar, and Th in vacuum wavelengths.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_units">UNITS</A></H2>
  <! BeginSection: 'UNITS'>
  <UL>
  The dispersion units are specified by strings having a unit type from the
  list below along with the possible preceding modifiers, "<TT>inverse</TT>", to
  select the inverse of the unit and "<TT>log</TT>" to select logarithmic units. For
  example "<TT>log angstroms</TT>" to select the logarithm of wavelength in Angstroms
  and "<TT>inv microns</TT>" to select inverse microns.  The various identifiers may
  be abbreviated as words but the syntax is not sophisticated enough to
  recognized standard scientific abbreviations except for those given
  explicitly below.
  <P>
  <PRE>
  	   angstroms - Wavelength in Angstroms
  	  nanometers - Wavelength in nanometers
  	millimicrons - Wavelength in millimicrons
  	     microns - Wavelength in microns
  	 millimeters - Wavelength in millimeters
  	  centimeter - Wavelength in centimeters
  	      meters - Wavelength in meters
  	       hertz - Frequency in hertz (cycles per second)
  	   kilohertz - Frequency in kilohertz
  	   megahertz - Frequency in megahertz
  	    gigahertz - Frequency in gigahertz
  	         m/s - Velocity in meters per second
  	        km/s - Velocity in kilometers per second
  	          ev - Energy in electron volts
  	         kev - Energy in kilo electron volts
  	         mev - Energy in mega electron volts
  <P>
  	          nm - Wavelength in nanometers
  	          mm - Wavelength in millimeters
  	          cm - Wavelength in centimeters
  	           m - Wavelength in meters
  	          Hz - Frequency in hertz (cycles per second)
  	         KHz - Frequency in kilohertz
  	         MHz - Frequency in megahertz
  	         GHz - Frequency in gigahertz
  		  wn - Wave number (inverse centimeters)
  </PRE>
  <P>
  The velocity units require a trailing value and unit defining the
  velocity zero point.  For example to transform to velocity relative to
  a wavelength of 1 micron the unit string would be:
  <P>
  <PRE>
  	km/s 1 micron
  </PRE>
  </UL>
  <! EndSection:   'UNITS'>
  <H2><A NAME="s_air_vacuum_conversion">AIR/VACUUM CONVERSION</A></H2>
  <! BeginSection: 'AIR/VACUUM CONVERSION'>
  <UL>
  The air to vacuum and vacuum to air conversions are obtained by multiplying
  or dividing by the air index of refraction as computed from the
  formulas in Allen's Astrophysical Quantities (p. 124 in 1973 edition).
  These formulas include temperature, pressure, and water vapour terms
  with the default values being the standard ones.
  </UL>
  <! EndSection:   'AIR/VACUUM CONVERSION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Convert a spectrum dispersion calibrated in Angstroms to electron
  volts and resample to a linear sampling.
  <P>
  <PRE>
      cl&gt; disptrans spec1 evspec1 ev linear+
      evspec1: Dispersion transformed to ev.
  </PRE>
  <P>
  2. Apply an air to vacuum correction to an echelle spectrum using the
  default standard temperature and pressure.  Don't resample but rather use
  a nonlinear dispersion function.
  <P>
  <PRE>
      cl&gt; disptrans highres.ec vac.ec angs air=air2vac
      vac.ec: Dispersion transformed to angstroms in vacuum with
        t = 15. C, p = 760. mmHg, f = 4. mmHg.
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_DISPTRANS">DISPTRANS V2.10.4</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='DISPTRANS' Line='DISPTRANS V2.10.4'>
  <DD>New task with this release.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  dispcor, identify, scopy, dopcor
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'UNITS' 'AIR/VACUUM CONVERSION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>