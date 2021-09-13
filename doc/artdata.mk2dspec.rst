.. _mk2dspec:

mk2dspec — Make/add artificial 2D spectra using 1D spectra templates
====================================================================

**Package: artdata**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  mk2dspec -- Make/add 2D spectra using 1D spectra templates
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  mk2dspec input
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Spectra to create or modify.
  </DD>
  </DL>
  <DL>
  <DT><B>output = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = ""'>
  <DD>Output spectra when modifying input spectra.  If no output spectra are
  given then existing spectra in the input list are modified directly.
  If an output list is given then it must match in number the input list.
  </DD>
  </DL>
  <DL>
  <DT><B>models = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='models' Line='models = ""'>
  <DD>List of model parameter files.  If the list of model files is shorter than the
  list of input images then the last model file is reused.  The model
  parameter files contain lines giving one dimensional spectrum template
  name, intensity scale, type of cross dispersion profile, profile
  width in the center line, change of width per line, profile position
  in the center line, and change of position per line (see the DESCRIPTION
  section).
  </DD>
  </DL>
  <DL>
  <DT><B>comments = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='comments' Line='comments = yes'>
  <DD>Include comments recording task parameters in the image header?
  </DD>
  </DL>
  <P>
  WHEN CREATING NEW SPECTRA
  <DL>
  <DT><B>title = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='title' Line='title = ""'>
  <DD>Image title to be given to the spectra.  Maximum of 79 characters.
  </DD>
  </DL>
  <DL>
  <DT><B>ncols = 100, nlines = 512</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols = 100, nlines = 512'>
  <DD>Number of columns and lines.
  </DD>
  </DL>
  <DL>
  <DT><B>header = "<TT>artdata$stdheader.dat</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='header' Line='header = "artdata$stdheader.dat"'>
  <DD>Image or header keyword data file.  If an image is given then the image header
  is copied.  If a file is given then the FITS format cards are copied.
  This only applies to new images.   The data file consists of lines
  in FITS format with leading whitespace ignored.  A FITS card must begin
  with an uppercase/numeric keyword.  Lines not beginning with a FITS
  keyword such as comments or lower case are ignored.  The user keyword
  output of <B>imheader</B> is an acceptable data file.  See <B>mkheader</B>
  for further information.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task creates or modifies two dimensional spectra by taking one
  dimensional spectra, convolving them with a spatial profile across the
  dispersion, and adding them into two dimensional images.  The one
  dimensional spectra may be real data or artificial data created with
  the task <B>mk1dspec</B>.  No noise is included but may be added with
  the task <B>mknoise</B>.  The spatial profile is fully subsampled and
  may vary in width and position along the dispersion axis.  The spatial
  axis is along the first dimension and the dispersion is along the
  second dimension.
  <P>
  For new images a set of header keywords may be added by specifying an
  image or data file with the <I>header</I> parameter (see also <B>mkheader</B>).
  If a data file is specified lines beginning with FITS keywords are
  entered in the image header.  Leading whitespace is ignored and any
  lines beginning with words having lowercase and nonvalid FITS keyword
  characters are ignored.  In addition, comments may be added to
  the image header recording the model file name and the contents of the
  model file.
  <P>
  The spatial profile models are specified in one or more model parameter
  files.  These files contain lines giving a one dimensional spectrum template
  name, intensity scale, type of cross dispersion profile, profile
  width in the center line, change of width per line, profile position
  in the center line, and change of position per line.  More specifically:
  <P>
  <DL>
  <DT><B>&lt;template name&gt;</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='&lt;template name&gt;'>
  <DD>The one dimensional spectrum template is any one dimensional IRAF image.
  If the spectrum template length is less than the two dimensional spectrum,
  the profile extends only over that number of lines and, if it is longer,
  then only the first part of the spectrum is used.
  </DD>
  </DL>
  <DL>
  <DT><B>scale</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='scale' Line='scale'>
  <DD>The template spectrum is scaled by this parameter to define the
  total flux for the two dimensional profile.
  </DD>
  </DL>
  <DL>
  <DT><B>&lt;profile type&gt;</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='&lt;profile type&gt;'>
  <DD>The spatial profiles are identified by two keywords, "<TT>gaussian</TT>"
  or "<TT>slit</TT>".  The profiles are defined by the following formulae,
  <P>
  <PRE>
      gaussian:   I(x) = exp (-ln(2) * (2*(x-xc)/fwhm)**2)
          slit:   I(x) = exp (-ln(2) * (2*(x-xc)/fwhm)**10)
  </PRE>
  <P>
  where x is the column coordinate, xc is the profile center, and
  fwhm is the full width at half maximum.  The "<TT>gaussian</TT>" profile
  is the usual gaussian specified in terms of a FWHM.  The "<TT>slit</TT>"
  profile is one which is relatively flat and then rapidly drops
  to zero.  The profile is normalized to unit integral so that
  the total flux across the profile is given by the scaled
  1D spectrum flux.
  </DD>
  </DL>
  <DL>
  <DT><B>fwhm, dfwhm</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='fwhm' Line='fwhm, dfwhm'>
  <DD>The full width at half maximum and derivative with line number.  The fwhm is
  defined for the middle of the image.  The FWHM as a function
  of line, l, is,
  <P>
  	fwhm + (l - nlines/2) * dfwhm
  </DD>
  </DL>
  <DL>
  <DT><B>center, dcenter</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='center' Line='center, dcenter'>
  <DD>The profile center and derivative with line number.  The center is
  defined for the middle of the image.  The center as a function
  of line, l, is,
  <P>
  	center + (l - nlines/2) * dcenter
  </DD>
  </DL>
  <P>
  The provision for having the spectra tilted relative to the columns is
  useful for understanding undersampling effects.  However, note that the
  spectral lines are not perpendicular to the dispersion but are always
  aligned with the image lines.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Create an artificial multifiber spectrum:
  <P>
  <PRE>
  	cl&gt; type multifiber.dat
  	arc 4 gauss 3 0 20 .01
  	spec1 .5 gauss 3 0 30 .01
  	spec2 .4 gauss 3 0 40 .01
  	spec3 .9 gauss 3 0 50 .01
  	spec4 .2 gauss 3 0 60 .01
  	spec5 .6 gauss 3 0 70 .01
  	spec6 1 gauss 3 0 80 .01
  	spec7 1 gauss 3 0 90 .01
  	cl&gt; mk1dspec arc cont=0 peak=500 nl=30
  	cl&gt; mk1dspec spec1 nlines=99 seed=1
  	cl&gt; mk1dspec spec2 nlines=80 seed=2
  	cl&gt; mk1dspec spec3 nlines=45 seed=3
  	cl&gt; mk1dspec spec4 nlines=95 seed=4
  	cl&gt; mk1dspec spec5 nlines=66 seed=5
  	cl&gt; mk1dspec spec6 nlines=90 seed=6
  	cl&gt; mk1dspec spec7 nlines=85 seed=7
  	cl&gt; mk2dspec multifiber model=multifiber.dat
  </PRE>
  <P>
  In this example artificial one dimensional spectra are generated with
  <B>mk1dspec</B>.
  <P>
  2. Create an artificial multislit spectrum:
  <P>
  <PRE>
  	cl&gt; type multislit.dat
  	arc 10 slit 18 0 120 .01
  	sky 2.5 slit 18 0 140 .01
  	sky 2.5 slit 18 0 160 .01
  	sky 2.5 slit 18 0 180 .01
  	sky 2.5 slit 18 0 200 .01
  	sky 2.5 slit 18 0 220 .01
  <P>
  	spec1 .05 gauss 3 0 140 .01
  	spec2 .2 gauss 4 0 161 .01
  	spec3 .1 gauss 3 0 179 .01
  	spec4 .1 gauss 3 0 200 .01
  	spec5 .15 gauss 4 0 220 .01
  	cl&gt; mk1dspec sky peak=1 nl=100
  	cl&gt; mk2dspec multislit model=multislit.dat nc=400
  </PRE>
  <P>
  Note how two spectra are overlaid to provide a sky spectrum with a
  narrower object spectrum.
  <P>
  3. Create an artificial long slit spectrum:
  <P>
  <PRE>
  	cl&gt; type longslit.dat
  	sky 22 slit 160 0 220 .01 
  	spec5 .05 gauss 3 0 140 .01
  	spec1 .05 gauss 3 0 190 .01
  	spec4 .5 gauss 3 0 220 .01
  	spec2 2 gauss 40 0 220 .01
  	spec5 .1 gauss 3 0 240 .01
  	spec1 .02 gauss 3 0 290 .01
  	cl&gt; mk2dspec longslit model=longslit.dat nc=400
  </PRE>
  <P>
  Note how objects are overlaid on a long slit sky spectrum.  The width
  of the spec2 spectrum is wider simulating a galaxy spectrum.
  <P>
  4. To include noise use the task <B>mknoise</B>:
  <P>
  <PRE>
  	cl&gt; mk2dspec longslit model=longslit.dat nc=400
  	cl&gt; mknoise longslit rdnoise=10 gain=2 poisson+ ncos=100
  </PRE>
  <P>
  5. Use a real long slit spectrum and add an object with an artificial spectrum:
  <P>
  <PRE>
  	cl&gt; mk1dspec artspec1d nlines=50
  	cl&gt; mk2dspec ls005 out=ls005new model=STDIN
  	artspec1d 1 gauss 5 0 125 0
  	[EOF]
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  mk1dspec, mknoise, mkheader
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
