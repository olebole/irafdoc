slist — List spectrum header parameters
=======================================

**Package: onedspec**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>slist (Mar92)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.onedspec</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>slist (Mar92)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>slist</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  slist -- List spectral header information
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  slist images
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_images">images</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of images to be listed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_apertures">apertures = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apertures' Line='apertures = ""'>
  <DD>List of apertures to be selected from the images for listing.  A null
  list selects all apertures.  See <B>ranges</B> for the syntax of
  this list.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_long_header">long_header = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='long_header' Line='long_header = no'>
  <DD>If set to yes, then a multiline listing of the header elements is given.
  If set to no, then a single line per spectrum is given.  The contents
  of the listing depend on the format.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task lists header information from apertures in a list of input
  images.  There is a short one line per spectrum listing and a more
  extended listing selected by the <I>long_header</I> parameter.
  <P>
  In both short and long outputs the aperture information consists of
  lines with the following whitespace separated fields: the image line,
  the aperture number, the beam number, the dispersion type, the
  wavelength of the first pixel, the wavelength interval per pixel,
  the number of valid pixels, and the aperture title.  The dispersion
  type is an integer with a value of -1 if not dispersion corrected,
  0 if dispersion corrected to a linear wavelength sampling, 1 if
  dispersion corrected to a log wavelength sampling, and 2 if dispersion
  corrected to a nonlinear sampling.  The wavelength per pixel is
  an approximation based on the wavelength endpoints divided by the
  number of pixels in the case of a nonlinear dispersion function.
  Also the wavelengths refer to the actual pixels taking any image sections
  into account and so may differ from the coordinate system information in
  the header which is defined for the original physical coordinates.
  The aperture titles may be identical with the image title if individual
  aperture titles are not defined.
  <P>
  In the short output format the image title is given first followed
  by the above described information.  This format is compact and
  suitable for easy use in other programs (see the example below).
  The long output format is blocked by image and gives the image name
  and title on the first line, the exposure time, universal time,
  and siderial time on the second line, the right ascention, declination,
  hour angle, and airmass on the third line, and then the individual
  aperture information on the remaining lines.  If some of the header
  information is missing a value of INDEF is printed.  The keywords used
  are EXPTIME/ITIME/EXPOSURE (in that order) for the exposure time,
  and UT, ST, RA, DEC, HA, and AIRMASS for the remaining values.
  <P>
      demoobj.ms: Hydra artificial image
  	EXPTIME = 2133.33 UT = 9:10:09.0    ST = 20:09:34.0
  	RA = 1:34:02.00   DEC = 30:37:03.0  HA = INDEF    AIRMASS = 2.3
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  List short header for an object and arc from a Hydra multifiber reduction
  for fibers 36 to 39.
  <P>
  <PRE>
      cl&gt; slist demoobj.ms,demoarc1.ms ap=36-39
      demoobj.ms 1 37 0 0 5785.85 6.140271 256 Sky fiber
      demoobj.ms 2 38 1 0 5785.85 6.140271 256 SS313
      demoobj.ms 3 39 1 0 5785.85 6.140271 256 SS444
      demoarc1.ms 1 36 2 0 5785.85 6.140271 256 Arc fiber
      demoarc1.ms 2 37 0 0 5785.85 6.140271 256 Sky fiber
      demoarc1.ms 3 38 1 0 5785.85 6.140271 256 SS313
      demoarc1.ms 4 39 1 0 5785.85 6.140271 256 SS444
  </PRE>
  <P>
  Note that fiber 37 is the first image line in demoobj.ms and teh second image
  line in demoarc.ms.  The dispersion is the same in all fibers by design.
  <P>
  2.  List long headers for the two images of example 1 but restricted to
  apertures 38 and 39.
  <P>
  <PRE>
      cl&gt; slist demoobj.ms,demoarc1.ms ap=38,39 l+
      demoobj.ms: Hydra artificial image
  	EXPTIME = 2133.33 UT = 9:10:09.0    ST = 20:09:34.0
  	RA = 1:34:02.00   DEC = 30:37:03.0  HA = INDEF    AIRMASS = 2.3
          2 38 1 0 5785.85 6.140271 256 SS313
  	3 39 1 0 5785.85 6.140271 256 SS444
      demoarc1.ms: Hydra artificial image
  	EXPTIME = 2133.33 UT = 9:10:09.0    ST = 20:09:34.0
  	RA = 1:34:02.00   DEC = 30:37:03.0  HA = INDEF    AIRMASS = 2.3
          3 38 1 0 5785.85 6.140271 256 SS313
  	4 39 1 0 5785.85 6.140271 256 SS444
  </PRE>
  <P>
  The other header parameters are the same because this is artificial
  data using the same template header.
  <P>
  3.  Dump the set of image headers on a printer in long format.
  <P>
  <PRE>
      cl&gt; slist *.ms.imh l+ | lprint
  </PRE>
  <P>
  4.  The short form of SLIST may be used to get some of the aperture
  information for use in a script.  The following simply prints the
  image line corresponding to a specified aperture.  In a real application
  something more complex would be done.
  <P>
  <PRE>
  	procedure example (images, aperture)
  <P>
  	string	images		{prompt="List of images"}
  	int	aperture	{prompt="Aperture"}
  <P>
  	begin
  		string temp, image
  		int	line
  <P>
  		# Use SLIST to print to a temporary file.
  		temp = mktemp ("example")
  		slist (images, aperture=aperture, long=no, &gt; temp)
  <P>
  		# Scan each line and print the line number.
  		list = temp
  		while (fscan (list, image, line) != EOF)
  		    print (image, ": ", line)
  		list = ""
  		delete (temp, verify=no)
  	end
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_SLIST">SLIST V2.10</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='SLIST' Line='SLIST V2.10'>
  <DD>This task was revised to be relevant for the current spectral image
  formats.  The old version is still available in the IRS/IIDS package.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imheader, hselect
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>