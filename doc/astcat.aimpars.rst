.. _aimpars:

aimpars — Default image data parameters
=======================================

**Package: astcat**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  aimpars -- Edit the standard image header keyword set
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  aimpars
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>observat = "<TT>OBSERVAT</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='observat' Line='observat = "OBSERVAT"'>
  <DD>The image header keyword defining the observatory at which the data
  was taken or the name of the observatory. If the observatory is defined then
  the keyword "<TT>OBSERVAT</TT>" is written to the image header if it does not
  already exist. 
  </DD>
  </DL>
  <DL>
  <DT><B>esitelng = "<TT>INDEF</TT>", esitelat = "<TT>INDEF</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='esitelng' Line='esitelng = "INDEF", esitelat = "INDEF"'>
  <DD>The image header keywords defining the longitude and latitude of the
  observatory in degrees or the longitude and latitude values in degrees.
  If the longitude and latitude are defined the keywords "<TT>ESITELNG</TT>" and
  "<TT>ESITELAT</TT>" are written to the image header if they do not already exist.
  </DD>
  </DL>
  <DL>
  <DT><B>esitealt = "<TT>INDEF</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='esitealt' Line='esitealt = "INDEF"'>
  <DD>The image header keyword defining the altitude of the observatory in meters
  or the altitude itself in meters. If the altitude is defined the keyword
  "<TT>ESITEALT</TT>" is written to the image header if it does not already exist.
  </DD>
  </DL>
  <DL>
  <DT><B>esitetz = "<TT>INDEF</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='esitetz' Line='esitetz = "INDEF"'>
  <DD>The image header keyword defining the timezone of the observatory 
  in hours from the Greenwich meridian or the timezone value 
  in hours from the Greenwich meridian. Positive values correspond to time
  zones west of the meridian. If the time zone is defined the keyword
  "<TT>ESITETZ</TT>" is written to the image header if it does not already exist.
  </DD>
  </DL>
  <DL>
  <DT><B>emjdobs = "<TT>MJD-OBS</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='emjdobs' Line='emjdobs = "MJD-OBS"'>
  <DD>The image header keyword defining the effective MJD of the observation
  or the MJD. MJD-OBS normally defines the time of the beginning
  of the observation. Users may wish to change this value to represent
  the MJD at mid-exposure.  If the effective MJD is defined the keyword
  "<TT>EMJDOBS</TT>" is written to the image header if it does not already exist.
  </DD>
  </DL>
  <DL>
  <DT><B>edatamin = "<TT>INDEF</TT>", edatamax = "<TT>INDEF</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='edatamin' Line='edatamin = "INDEF", edatamax = "INDEF"'>
  <DD>The image header keywords defining the minimum and maximum good data
  limits in ADU or the minimum and maximum good data values in ADU.
  If these limits are defined the keywords "<TT>EDATAMIN</TT>" and "<TT>EDATAMAX</TT>" 
  are written to the image header if they do not already exist.
  </DD>
  </DL>
  <DL>
  <DT><B>egain = "<TT>GAIN</TT>", erdnoise = "<TT>RDNOISE</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='egain' Line='egain = "GAIN", erdnoise = "RDNOISE"'>
  <DD>The image header keywords defining the effective gain in electrons per ADU 
  and readout noise in electrons or the gain and readout noise values in 
  electrons per ADU and electrons. If the gain and readout noise are defined
  the keywords "<TT>EGAIN</TT>" and "<TT>ERDNOISE</TT>" are written to the image header if they do
  not already exist.
  </DD>
  </DL>
  <DL>
  <DT><B>ewavlen = "<TT>INDEF</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ewavlen' Line='ewavlen = "INDEF"'>
  <DD>The image header keyword defining the effective wavelength in microns or
  the effective wavelength value in microns. If the effective wavelength is
  defined the keyword "<TT>EWAVLEN</TT>" is written to the image header if it does
  not already exist.
  </DD>
  </DL>
  <DL>
  <DT><B>etemp = "<TT>INDEF</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='etemp' Line='etemp = "INDEF"'>
  <DD>The image header keyword defining the effective temperature in degrees
  or the effective temperature values in degrees. If the effective wavelength
  is defined the keyword "<TT>ETEMP</TT>" is written to the image header it does
  not already exist.
  </DD>
  </DL>
  <DL>
  <DT><B>epress = "<TT>INDEF</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='epress' Line='epress = "INDEF"'>
  <DD>The image header keyword defining the effective pressure in millibars or
  the effective pressure values in millibars. If the effective pressure is
  defined the keyword "<TT>EPRESS</TT>" is written to the image header if it does
  not already exist.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  The standard image parameter set is used to encode quantities in the image
  headers that may be required by the astrometric analysis tasks. The current
  parameter set divides into two parameter groups: parameters
  concerned with locating stars in an image and computing accurate pixel
  coordinates and instrumental magnitudes <I>edatamin</I>, <I>edatamax</I>,
  <I>egain</I>, and <I>erdnoise</I>, and parameters required to transform
  from mean to observed place <I>observat</I>, <I>esiteng</I>,
  <I>esitelat</I>, <I>esitealt</I>, <I>esitetz</I>, <I>ewavlen</I>,
  <I>etem</I>, <I>epress</I>. The latter group of parameter is required for
  astrometric analyses carried out in observed place rather than
  mean place.
  <P>
  If the quantity defined by the aimpars parameter is defined, i.e. the
  parameter value is an image header keyword which defines a valid value,
  or the parameter value is itself a valid value, then a keyword 
  with the same name as the parameter name is inserted into the image
  header, if one with that name does not already exist.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. List the default image header parameters.
  <P>
  <PRE>
  cl&gt; lpar aimpars
  </PRE>
  <P>
  2. Edit the default image header parameters.
  <P>
  <PRE>
  cl&gt; aimpars
  </PRE>
  <P>
  3. Edit the default image header parameters from the agetim task.
  <P>
  <PRE>
  cl&gt; epar agetim
  </PRE>
  <P>
  4. Save the current awcspars parameter values in a text file called
  aimhdr1.par.  Use the saved parameter set in the next call to the agetim
  task.
  <P>
  <PRE>
  cl&gt; epar aimpars
  cl&gt; agetim ... aimpars=aimhdr1.par ...
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
  agetim
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
