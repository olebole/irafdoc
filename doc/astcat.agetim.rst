agetim — Extract FITS images from image surveys
===============================================

**Package: astcat**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>agetim (Mar00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>astcat</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>agetim (Mar00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>agetim</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  agetim -- extract fits images from image surveys
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  agetim regions output
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_regions">regions</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='regions' Line='regions'>
  <DD>The source  of the extraction region definitions. The options are:
  <DL>
  <DT><B><A NAME="l_">&lt;filename&gt;</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='&lt;filename&gt;'>
  <DD>The name of a text file containing a list of region definitions, one
  region definition per line. The format of the regions file is described
  in detail below.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">&lt;image list&gt;</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='&lt;image list&gt;'>
  <DD>The list of images containing the region definition. The input images
  must have a valid FITS world coordinate system in order to be used
  for region definition.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_pars">pars</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='pars' Line='pars'>
  <DD>If regions is set to the reserved keyword "<TT>pars</TT>" then a single region
  definition is read from the <I>aregpars</I> parameter set. By default a region
  ten arc minutes in size centered on coordinates ra = "<TT>00:00:00.0</TT>" and
  dec = "<TT>+00:00:00</TT>" in the query coordinate system is extracted.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_images">images</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>The list of output FITS image files. The number of output files must be equal
  to the number regions in the regions list times the number of astrometry
  catalogs in the catalog list. By default the output images are assigned names of
  the form "<TT>reg#[.sv#].#.fits</TT>" if the region definition source is "<TT>pars</TT>" or
  a file, e.g. "<TT>reg002.1.fits</TT>", or "<TT>image[.sv#].#.fits</TT>" if the region
  definition source is an image list, e.g. "<TT>image.1.fits</TT>". The image survey
  number is only inserted if there is more than one image survey
  in the image survey list.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_aregpars">aregpars = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='aregpars' Line='aregpars = ""'>
  <DD>The region definition parameter set. The aregpars parameters define the
  extraction region center, region width, region center units, and the region
  center coordinate system. The region definition parameters are used if
  <I>regions</I> = "<TT>pars</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_imsurveys">imsurveys = "<TT>)_.imsurveys</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imsurveys' Line='imsurveys = ")_.imsurveys"'>
  <DD>The list of input image surveys. By default the image survey name is set to the
  value of the package parameter imsurveys. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wcsedit">wcsedit = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcsedit' Line='wcsedit = no'>
  <DD>Convert a DSS WCS to a FITS WCS or add an approximate FITS style WCS to the
  output image headers if they don't already possess one ?  The WCS status
  of the survey images  plus approximate coordinate, scale, orientation, and
  projection information is stored in the image surveys configuration
  file <I>imdb</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_hdredit">hdredit = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='hdredit' Line='hdredit = no'>
  <DD>Add a set of standard keywords to the image header which may be required or
  useful in the later astrometric analysis steps ?  These parameters divide
  into two groups, those concerned with locating objects in an image and
  those required to transform from mean place to observed coordinates.
  Default settings for these parameters are stored in the images surveys
  configuration file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_update">update = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='update' Line='update = no'>
  <DD>Update the default values of the algorithm parameters, e.g. aregpars
  on task termination ?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print status messages on the terminal as the task proceeds ?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_imdb">imdb = "<TT>)_.imdb</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imdb' Line='imdb = ")_.imdb"'>
  <DD>The image surveys configuration file. Imdb defaults to the value of the
  package parameter imdb. The default image surveys configuration file is
  "<TT>astcat$lib/imdb.dat</TT>".
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  Agetim extracts fits images from local or remote image surveys
  <I>imsurveys</I> using a list of region definitions supplied by the user
  <I>regions</I> and writes the results of each image survey query to the output
  images <I>output</I>.
  <P>
  A regions definition consists of the coordinates of the field center,
  the field size, the units of the field center, and the coordinate system of
  the field center. If <I>regions</I> = "<TT>pars</TT>" these quantities are read
  from the <I>aregpars</I> parameters <I>rcra</I>, <I>rcdec</I>, <I>rcrawidth</I>,
  <I>rcdecwidth</I> <I>rcraunits</I>, <I>rcdecunits</I>., and <I>rcsystem</I>. 
  If <I>regions</I> is an input image
  list they are read from the FITS world coordinate system in the image header.
  If <I>regions</I> is a file name they are read from file whose format is
  the following.
  <P>
  <PRE>
  # Optional comment
  <P>
  ra1 dec1 xwidth1 ywidth1 [raunits1 [decunits1 [system1]]]
  ra2 dec2 xwidth2 ywidth2 [raunits2 [decunits2 [system2]]]
  raN decN xwidthN ywidthN [raunitsN [decunitsN [systemN]]]
  </PRE>
  <P>
  Quantities in square brackets are optional. If system is undefined the
  coordinate system defaults to the query coordinate system, i.e. if the
  catalog query expects coordinates in J2000.0 then ra and dec will be
  interpreted as though they were in the J2000.0 system. If undefined 
  the ra and dec units default to the preferred units of the coordinate
  system, i.e. hours and degrees for equatorial coordinate systems,
  and degrees and degrees for ecliptic, galactic, and supergalactic 
  coordinate systems.
  <P>
  A sample regions file  is shown below. If the image query system is
  J2000.0 then all four regions definitions are equivalent, since J2000.0
  is assumed in examples 1 and 2, is specified in example 3, and example
  is same target as example but expressed in the B1950.0 coordinate system.
  <P>
  <PRE>
  # List of targets
  <P>
  13:29:53.27 +47:11:48.4 10.0 10.0 
  13:29:53.27 +47:11:48.4 10.0 10.0 hours degrees 
  13:29:53.27 +47:11:48.4 10.0 10.0 hours degrees J2000.0
  13:27:46.90 +47:27:16.0 10.0 10.0 hours degrees B1950.0
  </PRE>
  <P>
  For each specified image survey in <I>imsurvey</I> agetim loops through the
  regions list, formats the image survey query, makes a local or remote
  connection to the image server using the image survey description in the
  image survey configuration file <I>imdb</I>, and captures the results.
  Image survey names must be of the form imsurvey@site, e.g. dss1@cadc.
  Image survey names without entries in the image survey configuration file
  are skipped.
  <P>
  If <I>wcsedit</I> = yes  then DSS coordinate systems are converted
  into FITS coordinate systems or an approximate FITS WCS is added
  to the image using information in the image surveys configuration file.
  The quantities of interest are the values, units, and coordinates
  system of the reference point <I>wxref</I>, <I>wyref</I>, <I>wraref</I>,
  <I>wdecref</I>, <I>wraunits</I>, <I>wdecunits</I>, and <I>wsystem</I>, and the
  scale, orientation, and projection information <I>wxmag</I>, <I>wymag</I>,
  <I>wxrot</I>, <I>wyrot</I>, and <I>wproj</I>. For more information on how these
  quantities are defined in the image surveys configuration file 
  type "<TT>help imsurveys</TT>".
  <P>
  If <I>hdredit</I> = yes then a standard set of keyword equal values
  pairs will be added to the image headers using information in the
  image surveys configuration file.  The parameters divide into two groups
  those concerned with locating stars in the image and computing accurate
  pixel centers: <I>edatamin</I>, <I>edatamax</I>, <I>egain</I>, and <I>erdnoise</I>,
  and those required for transforming mean place coordinates to observed
  plate coordinates as may be required to compute very accurate image scales,
  <I>observat</I>, <I>esitelng</I>, <I>esitelat</I>, <I>esitealt</I>, <I>esitetz</I>,
  <I>emjdobs</I>, <I>ewavlen</I>, <I>etemp</I>, and <I>epress</I>. New keyword
  values are only added to the header if keywords of the same name do not
  already exist and if appropriate values for the keywords exists, i.e.
  "<TT>INDEF</TT>" valued parameters will not be added to the header.
  <P>
  If <I>update</I> = yes the values of the <I>aregpars</I> parameters will be
  updated at task termination. If <I>verbose</I> = yes then detailed status
  reports are issued as the task executes.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Extract data from the default image survey using the default region
  definition, display the resulting image,  and examine its header.
  <P>
  <PRE>
  cl&gt; agetim pars default
  cl&gt; display reg001.1.fits 1 fi+
  cl&gt; imheader reg001.1.fits lo+ | page
  </PRE>
  <P>
  2. Repeat the previous example but convert the DSS WCS to a FITS WCS.
  The DSS WCS is unaltered.
  <P>
  <PRE>
  cl&gt; agetim pars default wcsedit+ 
  cl&gt; display reg001.2.fits 1 fi+
  cl&gt; imheader reg001.2.fits
  </PRE>
  <P>
  <P>
  3. Repeat example 2 but extract data for two surveys.
  <P>
  <PRE>
  cl&gt; agetim pars default wcsedit+ imsurveys="dss1@cadc,dss2@cadc"
  cl&gt; display reg001.3.fits 1 fi+
  cl&gt; imheader reg001.3.fits
  cl&gt; display reg002.1.fits 2 fi+
  cl&gt; imheader reg002.1.fits
  </PRE>
  <P>
  4. Repeat example 2 but add the values of the standard astrometry image
  keywords if these do not already exist in the image header and are defined.
  <P>
  <PRE>
  cl&gt; agetim pars default wcsedit+ hdredit+
  cl&gt; display reg001.4.fits 1 fi+
  cl&gt; imheader reg001.4.fits
  </PRE>
  <P>
  5. Extract images for a list of regions in a text file.  Note that the
  coordinate system and coordinate units are not specified in this regions
  list and default to those expected by the image survey query.
  <P>
  <PRE>
  page regions
  00:00:00.0 -90:00:00 10.0 10.0 
  00:00:00.0 -60:00:00 10.0 10.0 
  00:00:00.0 -30:00:00 10.0 10.0 
  00:00:00.0 +00:00:00 10.0 10.0 
  00:00:00.0 +30:00:00 10.0 10.0 
  00:00:00.0 +60:00:00 10.0 10.0 
  00:00:00.0 +90:00:00 10.0 10.0 
  cl&gt; agetim regions default
  </PRE>
  <P>
  6. Run agetim on a list of images containing valid FITS WCS information.
  Note that in the following example the test image dev$pix does not
  have a FITS WCS so no data is extracted for it.
  <P>
  <PRE>
  cl&gt; page imlist
  dev$pix
  dev$ypix
  cl&gt; agetim @imlist default
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  If output file is not a fits file, as may be the case if an error occurred
  in the network transfer, and header editing is enabled agetim will
  crash with a file seek error. The bug is due to missing error check 
  statements in the FITS kernel and will be fixed for the next release.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  aslist, adumpim, aregpars
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>