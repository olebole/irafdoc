.. _package:

package — Discussion and overview of package including sections on:
===================================================================

**Package: onedspec**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  onedspec -- generic 1D spectral reduction and analysis package
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  onedspec
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>observatory = "<TT>observatory</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='observatory' Line='observatory = "observatory"'>
  <DD>Observatory at which the spectra were obtained if not specified in the
  image header by the keyword OBSERVAT.  This parameter is used by several
  tasks in the package through parameter redirection so this parameter may be
  used to affect all these tasks at the same time.  The observatory may be
  one of the observatories in the observatory database, "<TT>observatory</TT>" to
  select the observatory defined by the environment variable "<TT>observatory</TT>" or
  the parameter <B>observatory.observatory</B>, or "<TT>obspars</TT>" to select the
  current parameters set in the <B>observatory</B> task.  See help for
  <B>observatory</B> for additional information.
  </DD>
  </DL>
  <DL>
  <DT><B>caldir = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='caldir' Line='caldir = ""'>
  <DD>Calibration directory containing standard star data.  This parameter
  is used by several tasks in the package through redirection.  A list of
  standard calibration directories may be obtained by listing the file
  "<TT>onedstds$README</TT>"; for example:
  <P>
  	cl&gt; page onedstds$README
  <P>
  The user may copy or create their own calibration files and specify
  the directory.  The directory "<TT></TT>" refers to the current working directory.
  </DD>
  </DL>
  <DL>
  <DT><B>interp = "<TT>poly5</TT>" (nearest|linear|poly3|poly5|spline3|sinc)</B></DT>
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
  <P>
  The following parameters apply to two and three dimensional images
  such as long slit or Fabry-Perot spectra.  They allow selection of
  a line or column as the spectrum "<TT>aperture</TT>" and summing of neighboring
  elements to form a one dimensional spectrum as the tasks in the
  ONEDSPEC package expect.
  <P>
  <DL>
  <DT><B>dispaxis = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dispaxis' Line='dispaxis = 1'>
  <DD>The image axis corresponding to the dispersion.  If there is an image
  header keyword DISPAXIS then the value of the keyword will be used
  otherwise this package parameter is used.  The dispersion coordinates
  are a function of column, line, or band when this parameter is 1, 2
  or 3.
  </DD>
  </DL>
  <DL>
  <DT><B>nsum = "<TT>1</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nsum' Line='nsum = "1"'>
  <DD>The number of neighboring elements to sum.  This is a string parameter
  that can have one or two numbers.  For two dimensional images only
  one number is needed and specifies the number of lines or columns
  to sum depending on the dispersion axis.  For three dimensional
  images two numbers may be given (if only one is given it defaults
  to the same value for both spatial axes) to specify the summing of
  the two spatial axes.  The order is the lower dimensional spatial
  axis first.
  <P>
  For an even value the elements summed are the central specified
  "<TT>aperture</TT>", nsum / 2 - 1 below, and nsum /2 above; i.e the
  central value is closer to the lower element than the upper.
  For example, for nsum=4 and an aperture of 10 for a dispersion
  axis of 1 in a two dimensional image the spectrum used will be
  the sum of lines 9 to 12.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>records = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='records' Line='records = ""'>
  <DD>This is a dummy parameter.  It is applicable only in the <B>imred.irs</B>
  and <B>imred.iids</B> packages.
  </DD>
  </DL>
  <DL>
  <DT><B>version = "<TT>ONEDSPEC V3: November 1991</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='version' Line='version = "ONEDSPEC V3: November 1991"'>
  <DD>Package version identification.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <B>onedspec</B> package contains generic tasks for the reduction,
  analysis, and display of one dimensional spectra.  The specifics of
  individual tasks may be found in their IRAF "<TT>help</TT>" pages.  This document
  describes the general and common features of the tasks.
  <P>
  The functions provided in the <B>onedspec</B> package with applicable tasks
  are summarized in Table 1.
  <P>
  <CENTER>Table 1:  Functions provided in the <B>onedspec</B> package
  
  </CENTER><BR>
  <P>
  <PRE>
  1.  Graphical display of spectra
            bplot - Batch plots of spectra
         identify - Identify features and fit dispersion functions
         specplot - Stack and plot multiple spectra
            splot - Interactive spectral plot/analysis
  <P>
  2.  Determining and applying dispersion calibrations
          dispcor - Dispersion correct spectra
           dopcor - Apply doppler corrections
         identify - Identify features and fit dispersion functions
       refspectra - Assign reference spectra to other spectra
       reidentify - Automatically identify features in spectra
        specshift - Shift spectral dispersion coordinate system
  <P>
  3.  Determining and applying flux calibrations
        calibrate - Apply extinction and flux calibrations to spectra
         deredden - Apply interstellar extinction correction
           dopcor - Apply doppler corrections
           lcalib - List calibration file data
         sensfunc - Create sensitivity function
         standard - Tabulate standard star data
  <P>
  4.  Fitting spectral features and continua
        continuum - Fit the continuum in spectra
         fitprofs - Fit gaussian profiles
             sfit - Fit spectra and output fit, ratio, or difference
            splot - Interactive spectral plot/analysis
  <P>
  5.  Arithmetic and combining of spectra
           sarith - Spectrum arithmetic
         scombine - Combine spectra
            splot - Interactive spectral plot/analysis
  <P>
  6.  Miscellaneous functions
           mkspec - Generate an artificial spectrum
            names - Generate a list of image names from a string
       sapertures - Set or change aperture header information
            scopy - Select and copy spectra
          sinterp - Interpolate a table of x,y to create a spectrum
            slist - List spectrum header parameters
            splot - Interactive spectral plot/analysis
  </PRE>
  <P>
  There are other packages which provide additional functions or specialized
  tasks for spectra.  Radial velocity measurements are available in the
  <B>noao.rv</B> package.  The <B>noao.imred</B> package contains a number
  of packages for specific types of data or instruments.  These packages
  are listed in Table 2.
  <P>
  <CENTER>Table 2:  <B>Imred</B> spectroscopy packages
  
  </CENTER><BR>
  <P>
  <PRE>
   	  argus - CTIO ARGUS reduction package
         ctioslit - CTIO spectrophotometric reduction package
  	echelle - Echelle spectral reductions (slit and FOE)
   	  hydra - KPNO HYDRA (and NESSIE) reduction package
  	   iids - KPNO IIDS spectral reductions
  	    irs - KPNO IRS spectral reductions
        kpnocoude - KPNO coude reduction package (slit and 3 fiber)
         kpnoslit - KPNO low/moderate dispersion slits (Goldcam, RCspec, Whitecam)
          specred - Generic slit and fiber spectral reduction package
  </PRE>
  <P>
  Finally, there are non-NOAO packages which may contain generally useful
  software for spectra.  Currently available packages are <B>stsdas</B>
  and <B>xray</B>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Spectrum image formats and coordinate systems</H3>
  <! BeginSection: 'SPECTRUM IMAGE FORMATS AND COORDINATE SYSTEMS'>
  <UL>
  See the separate help topic <I>specwcs</I>.
  </UL>
  <! EndSection:   'SPECTRUM IMAGE FORMATS AND COORDINATE SYSTEMS'>
  <H3>Interpolation</H3>
  <! BeginSection: 'INTERPOLATION'>
  <UL>
  Changing the dispersion sampling of spectra, such as when converting to a
  constant sampling interval per pixel or a common sampling for combining or
  doing arithmetic on spectra, requires interpolation.  The tasks which
  reinterpolate spectra, if needed, are <B>dispcor, sarith, scombine,</B> and
  <B>splot</B>.
  <P>
  The interpolation type is set by the package parameter <I>interp</I>.
  The available interpolation types are:
  <P>
  <PRE>
  	nearest - nearest neighbor
  	 linear - linear
  	  poly3 - 3rd order polynomial
  	  poly5 - 5th order polynomial
  	spline3 - cubic spline
  	   sinc - sinc function
  </PRE>
  <P>
  The default interpolation type is a 5th order polynomial.
  <P>
  The choice of interpolation type depends on the type of data, smooth
  verses strong, sharp, undersampled features, and the requirements of
  the user.  The "<TT>nearest</TT>" and "<TT>linear</TT>" interpolation are somewhat
  crude and simple but they avoid "<TT>ringing</TT>" near sharp features.  The
  polynomial interpolations are smoother but have noticible ringing
  near sharp features.  They are, unlike the sinc function described
  below, localized.
  <P>
  In V2.10 a "<TT>sinc</TT>" interpolation option is available.  This function
  has advantages and disadvantages.  It is important to realize that
  there are disadvantages!  Sinc interpolation approximates applying a phase
  shift to the fourier transform of the spectrum.  Thus, repeated
  interpolations do not accumulate errors (or nearly so) and, in particular,
  a forward and reverse interpolation will recover the original spectrum
  much more closely than other interpolation types.  However, for
  undersampled, strong features, such as cosmic rays or narrow emission or
  absorption lines, the ringing can be more severe than the polynomial
  interpolations.  The ringing is especially a concern because it extends
  a long way from the feature causing the ringing; 30 pixels with the
  truncated algorithm used.  Note that it is not the truncation of the
  interpolation function which is at fault!
  <P>
  Because of the problems seen with sinc interpolation it should be used with
  care.  Specifically, if there are no undersampled, narrow features it is a
  good choice but when there are such features the contamination of the
  spectrum by ringing is much more severe than with other interpolation
  types.
  </UL>
  <! EndSection:   'INTERPOLATION'>
  <H3>Units</H3>
  <! BeginSection: 'UNITS'>
  <UL>
  In versions of the NOAO spectroscopy packages prior to V2.10 the dispersion
  units used were restricted to Angstroms.  In V2.10 the first,
  experimental, step of generalizing to other units was taken by
  allowing the two principle spectral plotting tasks, <B>splot</B> and
  <B>specplot</B>, to plot in various units.  Dispersion functions are still
  assumed to be in Angstroms but in the future the generalization will be
  completed to all the NOAO spectroscopy tasks.
  <P>
  The dispersion units capability of the plotting tasks allows specifying
  the units with the "<TT>units</TT>" task parameter and interactively changing the
  units with the "<TT>:units</TT>" command.  In addition the <TT>'v'</TT> key allows plotting
  in velocity units with the zero point velocity defined by the cursor
  position.
  <P>
  The units are specified by strings having a unit type from the list below
  along with the possible preceding modifiers, "<TT>inverse</TT>", to select the
  inverse of the unit and "<TT>log</TT>" to select logarithmic units. For example "<TT>log
  angstroms</TT>" to plot the logarithm of wavelength in Angstroms and "<TT>inv
  microns</TT>" to plot inverse microns.  The various identifiers may be
  abbreviated as words but the syntax is not sophisticated enough to
  recognized standard scientific abbreviations except as noted below.
  <P>
  <PRE>
  		Table 1:  Unit Types
  <P>
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
  		   z - Redshift
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
  The velocity and redshift units require a trailing value and unit defining the
  velocity zero point.  For example to plot velocity relative to
  a wavelength of 1 micron the unit string would be:
  <P>
  <PRE>
  	km/s 1 micron
  </PRE>
  <P>
  Some additional examples of units strings are:
  <P>
  <PRE>
  	milliang
  	megahertz
  	inv mic
  	log hertz
  	m/s 3 inv mic
  	z 5015 ang
  </PRE>
  </UL>
  <! EndSection:   'UNITS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  apextract, longslit, rv, imred, specwcs
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'SPECTRUM IMAGE FORMATS AND COORDINATE SYSTEMS' 'INTERPOLATION' 'UNITS' 'SEE ALSO'  >
  
