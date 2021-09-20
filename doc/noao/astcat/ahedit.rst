.. _ahedit:

ahedit: Initialize the image wcs and set standard keywords
==========================================================

**Package: astcat**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  ahedit images imsurveys
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>images</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='images' Line='images' -->
  <dd>The list of input images to be edited.
  </dd>
  </dl>
  <dl>
  <dt><b>imsurveys </b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='imsurveys' Line='imsurveys ' -->
  <dd>The input image survey that is the source of the input images. If imsurveys
  is defined then the wcs status and the wcs and standard keyword parameter names
  and values are read from the image survey configuration file <i>imdb</i>. If
  imsurveys is undefined these quantities are read from the <i>wcs</i> parameter
  and the default <i>awcspars</i> and <i>aimpars</i> parameter sets.
  </dd>
  </dl>
  <dl>
  <dt><b>hupdate = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='hupdate' Line='hupdate = yes' -->
  <dd>Update the image headers ? If hupdate = no the image header edits are
  listed but the headers are not updated.
  </dd>
  </dl>
  <dl>
  <dt><b>wcsedit = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wcsedit' Line='wcsedit = no' -->
  <dd>Convert a DSS WCS to a FITS WCS or add an approximate FITS style WCS to the
  input image headers ?  If <i>imsurveys</i> is defined the WCS status of the
  survey images plus approximate image center coordinates, scale, orientation,
  and projection information are read from the image surveys configuration file
  <i>imdb</i>. If <i>imsurveys</i> is undefined these quantities are read
  from the <i>wcs</i> parameter and <i>awcspars</i> parameter set.
  </dd>
  </dl>
  <dl>
  <dt><b>wcs = <span style="font-family: monospace;">"none"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wcs' Line='wcs = "none"' -->
  <dd>The default wcs status of the input images if <i>imsurveys</i> is undefined.
  The options are:
  <dl>
  <dt><b>fits</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='fits' Line='fits' -->
  <dd>The input image is assumed to have a FITS WCS. No new FITS WCS is written.
  </dd>
  </dl>
  <dl>
  <dt><b>dss</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='dss' Line='dss' -->
  <dd>The input image is assumed to have a DSS WCS. The equivalent FITS WCS
  is added, but the DSS WCS is left unchanged.
  </dd>
  </dl>
  <dl>
  <dt><b>none</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='none' Line='none' -->
  <dd>The input image is assumed to have no WCS. The parameters in <i>awcspars</i>
  are used to create an approximate FITS WCS.
  </dd>
  </dl>
  </dd>
  </dl>
  <dl>
  <dt><b>awcspars = <span style="font-family: monospace;">""</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='awcspars' Line='awcspars = ""' -->
  <dd>The default WCS parameter set. If <i>wcsedit</i> = yes and <i>imsurveys</i>
  is undefined then the awcspars parameters are used to create an approximate
  FITS WCS. For more information about the awcspars parameters type
  <span style="font-family: monospace;">"help awcspars"</span>.
  </dd>
  </dl>
  <dl>
  <dt><b>hdredit = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='hdredit' Line='hdredit = no' -->
  <dd>Add a set of standard keywords to the image header which may be required or
  useful in the later astrometric analysis steps ?  These parameters divide
  into two groups, those concerned with locating objects in an image and
  those required to transform from mean place to observed coordinates.
  If <i>imsurveys</i> is undefined the standard keyword names and values
  are read from the images surveys configuration file <i>imdb</i>. If
  <i>imsurveys</i> is defined they are read from the <i>aimpars</i> parameter set.
  </dd>
  </dl>
  <dl>
  <dt><b>aimpars = <span style="font-family: monospace;">""</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='aimpars' Line='aimpars = ""' -->
  <dd>The default standard image header keywords parameter set. If <i>hdredit</i> =
  yes and <i>imsurveys</i> is undefined the parameter names and values
  in <i>aimpars</i> are used to write the standard image header keywords. For more
  information about these parameters type <span style="font-family: monospace;">"help aimpars"</span>.
  </dd>
  </dl>
  <dl>
  <dt><b>update = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='update' Line='update = no' -->
  <dd>Update the default values of the algorithm parameter sets, e.g. aregpars,
  <i>awcspars</i>, and <i>aimpars</i> on task termination ?
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes' -->
  <dd>Print status messages on the terminal as the task proceeds ?
  </dd>
  </dl>
  <dl>
  <dt><b>imdb = <span style="font-family: monospace;">"astcat$lib/imdb.dat"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='imdb' Line='imdb = "astcat$lib/imdb.dat"' -->
  <dd>The image surveys configuration file. Imdb defaults to the value of the
  package parameter imdb. The default image surveys configuration file is
  <span style="font-family: monospace;">"astcat$lib/imdb.dat"</span>.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Ahedit adds an approximate FITS WCS and / or a standard set of keyword value
  pair to the list of images <i>images</i> extracted from the image survey
  <i>imsurveys</i>. If hupdate = no the image edits are listed but not
  implemented.
  </p>
  <p>
  If <i>wcsedit</i> = yes then either an existing DSS WCS is converted to
  a FITS WCS or an approximate FITS WCS is added to the input image.  If
  <i>imsurveys</i> is undefined the current WCS status and WCS information
  is read from the image surveys configuration file <i>imdb</i>. If
  <i>imsurveys</i> is undefined the WCS status and coordinate information
  are read from <i>wcs</i> parameter and the default WCS  parameter set
  <i>awcspars</i>.  In both cases the quantities of interest are the values,
  units, and coordinates system of the reference point <i>wxref</i>, <i>wyref</i>,
  <i>wraref</i>, <i>wdecref</i>, <i>wraunits</i>, <i>wdecunits</i>, and
  <i>wsystem</i>, and the image scale, orientation, and projection information
  <i>wxmag</i>, <i>wymag</i>, <i>wxrot</i>, <i>wyrot</i>, and <i>wproj</i>. For
  more information on how these quantities are defined in the image surveys
  configuration file or the awcspars parameter set type <span style="font-family: monospace;">"help imsurveys"</span> and / or
  <span style="font-family: monospace;">"help awcspars"</span>.
  </p>
  <p>
  If <i>hdredit</i> = yes then a standard set of keyword equal value
  pairs are added to the image headers. If <i>imsurveys</i> is defined
  the standard keyword  name and value pairs are read from the image surveys
  configuration file. If <i>imsurveys</i> is undefined they are read from
  the standard image keywords  parameter set <i>aimpars</i>. In both cases the
  parameters divide into two groups,
  those concerned with locating stars in the image and computing accurate
  pixel centers <i>edatamin</i>, <i>edatamax</i>, <i>egain</i>, and <i>erdnoise</i>,
  and those required for transforming mean place coordinates to observed
  plate coordinates,
  <i>observat</i>, <i>esitelng</i>, <i>esitelat</i>, <i>esitealt</i>, <i>esitetz</i>,
  <i>emjdobs</i>, <i>ewavlen</i>, <i>etemp</i>, and <i>epress</i>. New keyword
  values are only added to the header if keywords of the same name do not
  already exist, and if appropriate values for the keywords exists, i.e.
  <span style="font-family: monospace;">"INDEF"</span> valued parameters will not be added to the header.
  </p>
  <p>
  If <i>update</i> = yes then the fIawcspars,
  and <i>aimpars</i> parameter sets are updated at task termination. If
  <i>verbose</i> = yes then detailed status reports are issued as the task
  executes.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. List the header edits required to create a FITS WCS from a DSS WCS
  for a set of images extracted from the dss1@cadc.
  </p>
  <pre>
  cl&gt; ahedit @imlist dss1@cadc hupdate- wcsedit+ hdredit-
  </pre>
  <p>
  2. Repeat the previous example but actually do the edits.
  </p>
  <pre>
  cl&gt; ahedit @imlist dss2@cadc hupdate+ wcsedit+ hdredit-
  </pre>
  <p>
  3. Repeat the previous example but get the current WCS stats from the user
  rather than from the image survey configuration file.
  </p>
  <pre>
  cl&gt; ahedit @imlist "" hupdate+ wcsedit+ wcs=dss hdredit-
  </pre>
  <p>
  4. Add an approximate FITS WCS to an image for which the coordinates
  of the image center in hours and degrees are stored in the keywords
  RA and DEC, the epoch of the image center coordinates is stored in EQUINOX,
  the image scale is 0.261 arcsec per pixel and east is left and north is down.
  </p>
  <pre>
  cl&gt; ahedit image "" wcsedit+ wcs="none" wraref="RA" wdecref="DEC" \<br>
  wxmag=0.26 wymag=0.26 wxrot=270 wyrot=90 wsystem="EQUINOX" hdredit-
  
  </pre>
  <p>
  5. Add the standard keyword name and values pairs for a list
  of images extracted from the dss1@cadc.
  </p>
  <pre>
  cl&gt; ahedit @imlist dss1@cadc hupdate+ wcsedit- hdredit+ 
  </pre>
  <p>
  6. Store the CCD saturation limit in the image header in the EDATAMAX
  keyword. Set the minimum good data limit at the same time.
  </p>
  <pre>
  cl&gt; ahedit image "" hupdate+ wcsedit- hdredit+ edatamin=-100.0 \<br>
  edatamax=32000
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  aslist, adumpim, aregpars, awcspars, aimpars
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
