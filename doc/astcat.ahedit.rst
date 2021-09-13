.. _ahedit:

ahedit — Initialize the image wcs and set standard keywords
===========================================================

**Package: astcat**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  ahedit -- Add wcs and / or standard keywords to the image header
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  ahedit images imsurveys
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>The list of input images to be edited.
  </DD>
  </DL>
  <DL>
  <DT><B>imsurveys </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imsurveys' Line='imsurveys '>
  <DD>The input image survey that is the source of the input images. If imsurveys
  is defined then the wcs status and the wcs and standard keyword parameter names
  and values are read from the image survey configuration file <I>imdb</I>. If
  imsurveys is undefined these quantities are read from the <I>wcs</I> parameter
  and the default <I>awcspars</I> and <I>aimpars</I> parameter sets.
  </DD>
  </DL>
  <DL>
  <DT><B>hupdate = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='hupdate' Line='hupdate = yes'>
  <DD>Update the image headers ? If hupdate = no the image header edits are
  listed but the headers are not updated.
  </DD>
  </DL>
  <DL>
  <DT><B>wcsedit = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcsedit' Line='wcsedit = no'>
  <DD>Convert a DSS WCS to a FITS WCS or add an approximate FITS style WCS to the
  input image headers ?  If <I>imsurveys</I> is defined the WCS status of the
  survey images plus approximate image center coordinates, scale, orientation,
  and projection information are read from the image surveys configuration file
  <I>imdb</I>. If <I>imsurveys</I> is undefined these quantities are read
  from the <I>wcs</I> parameter and <I>awcspars</I> parameter set.
  </DD>
  </DL>
  <DL>
  <DT><B>wcs = "<TT>none</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcs' Line='wcs = "none"'>
  <DD>The default wcs status of the input images if <I>imsurveys</I> is undefined.
  The options are:
  <DL>
  <DT><B>fits</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='fits' Line='fits'>
  <DD>The input image is assumed to have a FITS WCS. No new FITS WCS is written.
  </DD>
  </DL>
  <DL>
  <DT><B>dss</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='dss' Line='dss'>
  <DD>The input image is assumed to have a DSS WCS. The equivalent FITS WCS
  is added, but the DSS WCS is left unchanged.
  </DD>
  </DL>
  <DL>
  <DT><B>none</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='none' Line='none'>
  <DD>The input image is assumed to have no WCS. The parameters in <I>awcspars</I>
  are used to create an approximate FITS WCS.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>awcspars = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='awcspars' Line='awcspars = ""'>
  <DD>The default WCS parameter set. If <I>wcsedit</I> = yes and <I>imsurveys</I>
  is undefined then the awcspars parameters are used to create an approximate
  FITS WCS. For more information about the awcspars parameters type
  "<TT>help awcspars</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>hdredit = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='hdredit' Line='hdredit = no'>
  <DD>Add a set of standard keywords to the image header which may be required or
  useful in the later astrometric analysis steps ?  These parameters divide
  into two groups, those concerned with locating objects in an image and
  those required to transform from mean place to observed coordinates.
  If <I>imsurveys</I> is undefined the standard keyword names and values
  are read from the images surveys configuration file <I>imdb</I>. If
  <I>imsurveys</I> is defined they are read from the <I>aimpars</I> parameter set.
  </DD>
  </DL>
  <DL>
  <DT><B>aimpars = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='aimpars' Line='aimpars = ""'>
  <DD>The default standard image header keywords parameter set. If <I>hdredit</I> =
  yes and <I>imsurveys</I> is undefined the parameter names and values
  in <I>aimpars</I> are used to write the standard image header keywords. For more
  information about these parameters type "<TT>help aimpars</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>update = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='update' Line='update = no'>
  <DD>Update the default values of the algorithm parameter sets, e.g. aregpars,
  <I>awcspars</I>, and <I>aimpars</I> on task termination ?
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print status messages on the terminal as the task proceeds ?
  </DD>
  </DL>
  <DL>
  <DT><B>imdb = "<TT>)_.imdb)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imdb' Line='imdb = ")_.imdb)'>
  <DD>The image surveys configuration file. Imdb defaults to the value of the
  package parameter imdb. The default image surveys configuration file is
  </TT>"astcat$lib/imdb.dat"<TT>.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  Ahedit adds an approximate FITS WCS and / or a standard set of keyword value
  pair to the list of images <I>images</I> extracted from the image survey
  <I>imsurveys</I>. If hupdate = no the image edits are listed but not
  implemented.
  <P>
  If <I>wcsedit</I> = yes then either an existing DSS WCS is converted to
  a FITS WCS or an approximate FITS WCS is added to the input image.  If
  <I>imsurveys</I> is undefined the current WCS status and WCS information
  is read from the image surveys configuration file <I>imdb</I>. If
  <I>imsurveys</I> is undefined the WCS status and coordinate information
  are read from <I>wcs</I> parameter and the default WCS  parameter set
  <I>awcspars</I>.  In both cases the quantities of interest are the values,
  units, and coordinates system of the reference point <I>wxref</I>, <I>wyref</I>,
  <I>wraref</I>, <I>wdecref</I>, <I>wraunits</I>, <I>wdecunits</I>, and
  <I>wsystem</I>, and the image scale, orientation, and projection information
  <I>wxmag</I>, <I>wymag</I>, <I>wxrot</I>, <I>wyrot</I>, and <I>wproj</I>. For
  more information on how these quantities are defined in the image surveys
  configuration file or the awcspars parameter set type "<TT>help imsurveys</TT>" and / or
  "<TT>help awcspars</TT>".
  <P>
  If <I>hdredit</I> = yes then a standard set of keyword equal value
  pairs are added to the image headers. If <I>imsurveys</I> is defined
  the standard keyword  name and value pairs are read from the image surveys
  configuration file. If <I>imsurveys</I> is undefined they are read from
  the standard image keywords  parameter set <I>aimpars</I>. In both cases the
  parameters divide into two groups,
  those concerned with locating stars in the image and computing accurate
  pixel centers <I>edatamin</I>, <I>edatamax</I>, <I>egain</I>, and <I>erdnoise</I>,
  and those required for transforming mean place coordinates to observed
  plate coordinates,
  <I>observat</I>, <I>esitelng</I>, <I>esitelat</I>, <I>esitealt</I>, <I>esitetz</I>,
  <I>emjdobs</I>, <I>ewavlen</I>, <I>etemp</I>, and <I>epress</I>. New keyword
  values are only added to the header if keywords of the same name do not
  already exist, and if appropriate values for the keywords exists, i.e.
  "<TT>INDEF</TT>" valued parameters will not be added to the header.
  <P>
  If <I>update</I> = yes then the fIawcspars,
  and <I>aimpars</I> parameter sets are updated at task termination. If
  <I>verbose</I> = yes then detailed status reports are issued as the task
  executes.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. List the header edits required to create a FITS WCS from a DSS WCS
  for a set of images extracted from the dss1@cadc.
  <P>
  <PRE>
  cl&gt; ahedit @imlist dss1@cadc hupdate- wcsedit+ hdredit-
  </PRE>
  <P>
  2. Repeat the previous example but actually do the edits.
  <P>
  <PRE>
  cl&gt; ahedit @imlist dss2@cadc hupdate+ wcsedit+ hdredit-
  </PRE>
  <P>
  3. Repeat the previous example but get the current WCS stats from the user
  rather than from the image survey configuration file.
  <P>
  <PRE>
  cl&gt; ahedit @imlist "" hupdate+ wcsedit+ wcs=dss hdredit-
  </PRE>
  <P>
  4. Add an approximate FITS WCS to an image for which the coordinates
  of the image center in hours and degrees are stored in the keywords
  RA and DEC, the epoch of the image center coordinates is stored in EQUINOX,
  the image scale is 0.261"<TT> per pixel and east is left and north is down.
  <P>
  <PRE>
  cl&gt; ahedit image "" wcsedit+ wcs="none" wraref="RA" wdecref="DEC" \<BR>
  wxmag=0.26 wymag=0.26 wxrot=270 wyrot=90 wsystem="EQUINOX" hdredit-
  <P>
  </PRE>
  <P>
  5. Add the standard keyword name and values pairs for a list
  of images extracted from the dss1@cadc.
  <P>
  <PRE>
  cl&gt; ahedit @imlist dss1@cadc hupdate+ wcsedit- hdredit+ 
  </PRE>
  <P>
  6. Store the CCD saturation limit in the image header in the EDATAMAX
  keyword. Set the minimum good data limit at the same time.
  <P>
  <PRE>
  cl&gt; ahedit image "" hupdate+ wcsedit- hdredit+ edatamin=-100.0 \<BR>
  edatamax=32000
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  aslist, adumpim, aregpars, awcspars, aimpars
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
