.. _skyxymatch:

skyxymatch: Generate matched pixel lists using the image celestial wcs
======================================================================

**Package: immatch**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  skyxymatch -- match input and reference image x-y coordinates using the
  celestial coordinate WCS
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  skyxymatch input reference output
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>The list of input images containing the input celestial coordinate wcs.
  </dd>
  </dl>
  <dl>
  <dt><b>reference</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='reference' Line='reference' -->
  <dd>The list of reference images containing the reference celestial coordinate
  wcs. The number of reference images must be one or equal to the number
  of input images.
  </dd>
  </dl>
  <dl>
  <dt><b>output</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output' -->
  <dd>The output matched coordinate lists containing:
  1) the logical x-y pixel coordinates of a point
  in the reference image in columns 1 and 2, 2) the logical x-y pixel
  coordinates of the same point in the input image in columns 3 and 4,
  3) the world coordinates of the point in the reference image in columns
  5 and 6, and 4) the world coordinate of the point in the input image in
  columns 7 and 8. The output coordinate list can be
  input directly to the geomap task. The number of output files must be 
  equal to the number of input images or be the standard output STDOUT.
  </dd>
  </dl>
  <dl>
  <dt><b>coords = <tt>"grid"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='coords' Line='coords = "grid"' -->
  <dd>The source of the coordinate list. The options are:
  <dl>
  <dt><b>grid    </b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='grid' Line='grid    ' -->
  <dd>Generate a list of <i>nx * ny</i> coordinates evenly spaced over
  the reference image, and beginning and ending at logical coordinates
  <i>xmin</i> and <i>xmax</i> in x and <i>ymin</i> and <i>ymax</i> in y.
  </dd>
  </dl>
  <dl>
  <dt><b>&lt;filename&gt;</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='' Line='&lt;filename&gt;' -->
  <dd>The name of the text file containing the world coordinates of a set of
  points in the reference image.
  </dd>
  </dl>
  </dd>
  </dl>
  <dl>
  <dt><b>xmin = INDEF, xmax = INDEF, ymin = INDEF, ymax = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='xmin' Line='xmin = INDEF, xmax = INDEF, ymin = INDEF, ymax = INDEF' -->
  <dd>The minimum and maximum logical x and logical y coordinates used to generate
  the grid of control points if <i>coords</i> = <tt>"grid"</tt>. Xmin, xmax, ymin, and
  ymax default to 1, the number of columns in the reference image, 1, and the
  number of lines in the reference image, respectively.
  </dd>
  </dl>
  <dl>
  <dt><b>nx = 10, ny = 10</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='nx' Line='nx = 10, ny = 10' -->
  <dd>The number of points in x and y used to generate the coordinate grid
  if <i>coords</i> = <tt>"grid"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>wcs = <tt>"world"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wcs' Line='wcs = "world"' -->
  <dd>The world coordinate system of the coordinates.  The options are:
  <dl>
  <dt><b>physical</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='physical' Line='physical' -->
  <dd>Physical coordinates are pixel coordinates which are invariant with
  respect to linear transformations of the physical image data.  For example,
  if the reference 
  image is a rotated section of a larger input image, the physical
  coordinates of an object in the reference image are equal to the physical
  coordinates of the same object in the input image, although the logical
  pixel coordinates are different.
  </dd>
  </dl>
  <dl>
  <dt><b>world</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='world' Line='world' -->
  <dd>World coordinates are image coordinates which are invariant with
  respect to linear transformations of the physical image data and which
  are in decimal degrees for the celestial coordinate systems. Obviously if the
  wcs is correct the ra and dec of an object
  should remain the same no matter how the image
  is linearly transformed. The default world coordinate
  system is either 1) the value of the environment variable <tt>"defwcs"</tt> if
  set in the user's IRAF environment (normally it is undefined) and present
  in the image header, 2) the value of the <tt>"system"</tt>
  attribute in the image header keyword WAT0_001 if present in the
  image header or, 3) the <tt>"physical"</tt> coordinate system.
  Care must be taken that the wcs of the input and
  reference images are compatible, e.g. it makes no sense to
  match the coordinates of a 2D sky projection and a 2D spectral wcs.
  </dd>
  </dl>
  </dd>
  </dl>
  <dl>
  <dt><b>xcolumn = 1, ycolumn = 2</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='xcolumn' Line='xcolumn = 1, ycolumn = 2' -->
  <dd>The columns in the input coordinate list containing the x and y coordinate
  values if <i>coords</i> = &lt;filename&gt;.
  </dd>
  </dl>
  <dl>
  <dt><b>xunits = <tt>""</tt>, ls yunits = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='xunits' Line='xunits = "", ls yunits = ""' -->
  <dd>The units of the x and y coordinates in the input coordinate list 
  if <i>coords</i> = &lt;filename&gt;, by default decimal degrees for celestial
  coordinate systems, otherwise any units.
  The options are:
  <dl>
  <dt><b>hours</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='hours' Line='hours' -->
  <dd>Input coordinates specified in hours are converted to decimal degrees by
  multiplying by 15.0.
  </dd>
  </dl>
  <dl>
  <dt><b>native</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='native' Line='native' -->
  <dd>The internal units of the wcs. No conversions on the input coordinates
  are performed.
  </dd>
  </dl>
  If the units are not specified the default is <tt>"native"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>xformat = <tt>"%10.3f"</tt>, yformat = <tt>"%10.3f"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='xformat' Line='xformat = "%10.3f", yformat = "%10.3f"' -->
  <dd>The format of the output logical x and y reference and input pixel
  coordinates in columns 1 and 2 and 3 and 4 respectively. By default the
  coordinates are output right justified in a field of ten spaces with
  3 digits following the decimal point. 
  </dd>
  </dl>
  <dl>
  <dt><b>rwxformat = <tt>""</tt>, rwyformat = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='rwxformat' Line='rwxformat = "", rwyformat = ""' -->
  <dd>The format of the output world x and y reference image coordinates
  in columns 5 and 6 respectively. The internal default formats will give
  reasonable output formats and precision for sky projection coordinates.
  </dd>
  </dl>
  <dl>
  <dt><b>wxformat = <tt>""</tt>, wyformat = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wxformat' Line='wxformat = "", wyformat = ""' -->
  <dd>The format of the output world x and y input image coordinates
  in columns 7 and 8 respectively. The internal default formats will give
  reasonable output formats and precision for sky projection coordinates.
  </dd>
  </dl>
  <dl>
  <dt><b>min_sigdigits = 7</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='min_sigdigits' Line='min_sigdigits = 7' -->
  <dd>The minimum precision of the output coordinates if, the formatting parameters
  are undefined, or the output world coordinate system is <tt>"world"</tt> and the wcs
  cannot be decoded.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes' -->
  <dd>Print messages about the progress of the task?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  SKYXYMATCH matches the logical x and y pixel coordinates of a set of points 
  in the input image <i>input</i> with the logical x and y pixels coordinates
  of the same points in the reference image <i>reference</i>
  using world celestial coordinate information
  in the image headers. SKYXYMATCH writes its results to the
  coordinate file <i>output</i>  which is suitable for input to the GEOMAP task.
  The input and reference images may be 1D or 2D but must both have
  the same dimensionality.
  </p>
  <p>
  If <i>coords</i> = <tt>"grid"</tt>, SKYXYMATCH computes a grid of <i>nx * ny</i> 
  logical x and y pixel coordinates evenly distributed over the 
  logical pixel space of the reference image defined by the
  <i>xmin</i>, <i>xmax</i>, <i>ymin</i>, <i>ymax</i> parameters.
  The logical x and y reference image pixel coordinates are transformed to
  reference image celestial coordinates using
  world coordinate information stored in the reference image header.
  The reference image celestial coordinates are transformed to 
  input image celestial coordinates using world coordinate
  system information in both the reference and the input image headers.
  Finally the input image celestial coordinates are transformed to logical x and y
  input image pixel coordinates using world coordinate system information
  stored in the input image header. The transformation sequence looks
  like the following for an equatorial celestial coordinate system:
  </p>
  <pre>
     (x,y) reference -&gt; (ra,dec) reference  (reference image wcs)
  (ra,dec) reference -&gt; (ra,dec) input      (reference and input image wcs)
      (ra,dec) input -&gt; (x,y) input         (input image wcs)
  </pre>
  <p>
  The reference and input image celestial coordinate systems
  may be equatorial, ecliptic, galactic, or supergalactic. The equatorial systems
  may be one of: 1) the  mean place pre-IAU 1976 (FK4) system, 2) 
  the same as FK4 but without the E-terms (FK4-NO-E) system, 3) the mean
  place post-IAU
  1976 (FK5) system, 4) or the geocentric apparent place in the post-IAU 1976
  (GAPPT) system.
  </p>
  <p>
  SKYXYMATCH assumes that the celestial coordinate system is specified by the FITS
  keywords CTYPE, CRPIX, CRVAL, CD (or alternatively CDELT / CROTA), RADECSYS,
  EQUINOX (or EPOCH), MJD-WCS (or MJD-OBS, or DATE-OBS). USERS SHOULD TAKE NOTE
  THAT MJD-WCS IS CURRENTLY NEITHER A STANDARD OR A PROPOSED STANDARD FITS
  KEYWORD. HOWEVER IT OR SOMETHING SIMILAR, IS REQUIRED TO SPECIFY THE EPOCH OF
  THE COORDINATE SYSTEM WHICH MAY BE DIFFERENT FROM THE EPOCH OF THE OBSERVATION.
  </p>
  <p>
  The first four characters of the values of the ra / longitude and dec / latitude
  axis CTYPE keywords specify the celestial coordinate system.  The currently
  permitted values of CTYPE[1:4] are RA-- / DEC- for equatorial coordinate
  systems, ELON / ELAT for the ecliptic coordinate system, GLON / GLAT for the
  galactic coordinate system, and SLON / SLAT for the supergalactic coordinate
  system.
  </p>
  <p>
  The second four characters of the values of the ra / longitude and dec /
  latitude axis CTYPE keywords specify the sky projection geometry. IRAF
  currently supports the TAN, SIN, ARC, and GLS geometries, and consequently the
  currently permitted values of CTYPE[5:8] are -TAN, -ARC, -SIN, and -GLS.
  SKYXYMATCH fully supports the TAN, SIN, and ARC projections, but does not fully
  support the GLS projection.
  </p>
  <p>
  If the image celestial coordinate systems are equatorial, the value of the
  RADECSYS keyword specifies which fundamental equatorial system is to be
  considered. The permitted values of RADECSYS are FK4, FK4-NO-E, FK5, and GAPPT.
  If the RADECSYS keyword is not present in the image header, the values of the
  EQUINOX / EPOCH keywords (in that order of precedence) are used to determine
  the fundamental equatorial coordinate system. EQUINOX or EPOCH contain the
  epoch of the mean place and equinox for the FK4, FK4-NO-E, and FK5 systems
  (e.g 1950.0 or 2000.0). The default equatorial system is FK4 if EQUINOX or
  EPOCH &lt; 1984.0, FK5 if EQUINOX or EPOCH &gt;= 1984.0, and FK5 if RADECSYS, EQUINOX,
  and EPOCH are undefined. If RADECSYS is defined but EQUINOX and EPOCH are not,
  the equinox defaults to 1950.0 for the FK4 and FK4-NO-E systems, and 2000.0 for
  the FK5 system. The equinox value is interpreted as a Besselian epoch for the
  FK4 and FK4-NO-E systems, and as a Julian epoch for the FK5 system. Users are
  strongly urged to use the EQUINOX keyword in preference to the EPOCH keyword,
  if they must enter their own equinox values into the image header. The FK4 and
  FK4-NO-E systems are not inertial and therefore also require the epoch of the
  observation (the time when the mean place was correct), in addition to the
  equinox. The epoch is specified, in order of precedence, by the values of the
  keywords MJD-WCS or MJD-OBS (which contain the modified Julian date, JD -
  2400000.5, of the coordinate system), or the DATE-OBS keyword (which contains
  the date of the observation in the form DD/MM/YY, CCYY-MM-DD,
  CCYY-MM-DDTHH:MM:SS.S). As the latter quantity is
  only accurate to a day, the MJD-WCS or MJD-OBS specification is preferred.
  If all 3 keywords are absent the epoch defaults to the value of equinox.
  Equatorial coordinates in the GAPPT system require only the specification
  of the epoch of observation which is supplied via the MJD-WCS, MJD-OBS,
  or DATE-OBS keywords (in that order of precedence) as for the FK4 and
  FK4-NO-E system.
  </p>
  <p>
  If the image celestial coordinate systems are ecliptic the mean ecliptic
  and equinox of date are required. These are read from the MJD-WCS, MJD-OBS,
  or DATE-OBS keywords (in that order or precedence) as for the equatorial FK4,
  FK4-NO-E, and GAPPT systems.
  </p>
  <p>
  USERS NEED TO BE AWARE THAT THE IRAF IMAGE WORLD COORDINATE SYSTEM
  CURRENTLY (IRAF VERSIONS 2.10.4 PATCH 2 AND EARLIER) SUPPORTS ONLY THE
  EQUATORIAL SYSTEM (CTYPE&lt;lngax&gt; = <tt>"RA--XXXX"</tt> CTYPE&lt;latax&gt; = <tt>"DEC-XXXX"</tt>)
  WHERE XXXX IS THE PROJECTION TYPE, EVEN THOUGH THE SKYXYMATCH TASK
  SUPPORTS GALACTIC, SUPERGALACTIC, AND ECLIPTIC coordinate systems.
  </p>
  <p>
  If <i>coords</i> is a file name, SKYXYMATCH reads a list of x and y 
  reference image world coordinates from columns <i>xcolumn</i> and <i>ycolumn</i>
  in the input coordinates file  and transforms these coordinates to
  <tt>"native"</tt> coordinate units using the <i>xunits</i> and <i>yunits</i> parameters.
  The reference image world coordinates are
  transformed to logical reference and input image coordinates
  using the value of the <i>wcs</i> parameter and world coordinate
  information in the reference and input image headers.
  </p>
  <p>
  SKYXYMATCH will terminate with an error if the reference and input images
  are not both either 1D or 2D.
  If the world coordinate system information cannot be read from either
  the reference or input image header, the requested transformations
  from the world &lt;-&gt; logical coordinate systems cannot be compiled for either
  or both images, or the world coordinate systems of the reference and input
  images are fundamentally incompatible in some way, the output logical
  reference and input image coordinates are both set to a grid of points
  spanning the logical pixel space of the input, not the reference image,
  and defining an identify transformation, is written to the output file.
  </p>
  <p>
  The computed reference and input logical and world coordinates
  are written to the output file using
  the <i>xformat</i> and <i>yformat</i>, <i>rwxformat, fIrwyformat</i>,
  and the <i>wxformat</i> and <i>wxformat</i>
  parameters respectively. If these formats are undefined and, in the
  case of the world coordinates, a format attribute cannot be
  read from either the reference or the input images reasonable defaults are
  chosen.
  </p>
  <p>
  If the reference and input images are 1D then the 
  output logical and world y coordinates are
  set to 1.
  </p>
  <p>
  If <i>verbose</i> is <tt>"yes"</tt> then a title section is written to the output
  file for each set of computed coordinates, along with messages about
  what if anything went wrong with the computation.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Formats</h3>
  <!-- BeginSection: 'FORMATS' -->
  <p>
  A  format  specification has the form <tt>"%w.dCn"</tt>, where w is the field
  width, d is the number of decimal places or the number of digits  of
  precision,  C  is  the  format  code,  and  n is radix character for
  format code <tt>"r"</tt> only.  The w and d fields are optional.  The  format
  codes C are as follows:
   
  </p>
  <pre>
  b       boolean (YES or NO)
  c       single character (c or '\c' or '\0nnn')
  d       decimal integer
  e       exponential format (D specifies the precision)
  f       fixed format (D specifies the number of decimal places)
  g       general format (D specifies the precision)
  h       hms format (hh:mm:ss.ss, D = no. decimal places)
  m       minutes, seconds (or hours, minutes) (mm:ss.ss)
  o       octal integer
  rN      convert integer in any radix N
  s       string (D field specifies max chars to print)
  t       advance To column given as field W
  u       unsigned decimal integer
  w       output the number of spaces given by field W
  x       hexadecimal integer
  z       complex format (r,r) (D = precision)
   
  
  
  Conventions for w (field width) specification:
   
      W =  n      right justify in field of N characters, blank fill
          -n      left justify in field of N characters, blank fill
          0n      zero fill at left (only if right justified)
  absent, 0       use as much space as needed (D field sets precision)
   
  Escape sequences (e.g. "\n" for newline):
   
  \b      backspace   (not implemented)
       formfeed
  \n      newline (crlf)
  \r      carriage return
  \t      tab
  \"      string delimiter character
  \'      character constant delimiter character
  \\      backslash character
  \nnn    octal value of character
   
  Examples
   
  %s          format a string using as much space as required
  %-10s       left justify a string in a field of 10 characters
  %-10.10s    left justify and truncate a string in a field of 10 characters
  %10s        right justify a string in a field of 10 characters
  %10.10s     right justify and truncate a string in a field of 10 characters
   
  %7.3f       print a real number right justified in floating point format
  %-7.3f      same as above but left justified
  %15.7e      print a real number right justified in exponential format
  %-15.7e     same as above but left justified
  %12.5g      print a real number right justified in general format
  %-12.5g     same as above but left justified
  
  %h          format as nn:nn:nn.n
  %15h        right justify nn:nn:nn.n in field of 15 characters
  %-15h       left justify nn:nn:nn.n in a field of 15 characters
  %12.2h      right justify nn:nn:nn.nn
  %-12.2h     left justify nn:nn:nn.nn
   
  %H          / by 15 and format as nn:nn:nn.n
  %15H        / by 15 and right justify nn:nn:nn.n in field of 15 characters
  %-15H       / by 15 and left justify nn:nn:nn.n in field of 15 characters
  %12.2H      / by 15 and right justify nn:nn:nn.nn
  %-12.2H     / by 15 and left justify nn:nn:nn.nn
  
  \n          insert a newline
  </pre>
  <!-- EndSection:   'FORMATS' -->
  <h3>References</h3>
  <!-- BeginSection: 'REFERENCES' -->
  <p>
  Additional  information  on  IRAF  world  coordinate  systems including
  more detailed descriptions of the <tt>"logical"</tt>, <tt>"physical"</tt>, and <tt>"world"</tt>
  coordinate systems can be found  in  the  help  pages  for  the  WCSEDIT
  and  WCRESET  tasks. Detailed   documentation   for  the  IRAF  world 
  coordinate  system interface MWCS can be found in  the  file
  <tt>"iraf$sys/mwcs/MWCS.hlp"</tt>.  This  file  can  be  formatted  and  printed
  with the command <tt>"help iraf$sys/mwcs/MWCS.hlp fi+ | lprint"</tt>.
  </p>
  <p>
  Details of the FITS header world coordinate system interface can
  be found in the draft paper <tt>"World Coordinate Systems Representations Within the
  FITS Format"</tt> by Hanisch and Wells, available from the iraf anonymous ftp
  archive and the draft paper which supersedes it <tt>"Representations of Celestial
  Coordinates in FITS"</tt> by Greisen and Calabretta available from the NRAO
  anonymous ftp archives.
  </p>
  <p>
  The spherical astronomy routines employed here are derived from the Starlink
  SLALIB library provided courtesy of Patrick Wallace. These routines
  are very well documented internally with extensive references provided
  where appropriate. Interested users are encouraged to examine the routines
  for this information. Type <tt>"help slalib"</tt> to get a listing of the SLALIB
  routines, <tt>"help slalib opt=sys"</tt> to get a concise summary of the library,
  and <tt>"help &lt;routine&gt;"</tt> to get a description of each routine's calling sequence,
  required input and output, etc. An overview of the library can be found in the
  paper <tt>"SLALIB - A Library of Subprograms"</tt>, Starlink User Note 67.7
  by P.T. Wallace, available from the Starlink archives.
  </p>
  <!-- EndSection:   'REFERENCES' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Compute a matched list of 100 logical x and y coordinates for an X-ray 
  and radio image of the same field, both of which have accurate sky
  projection world coordinate systems with different equinoxes. Print the
  output world coordinates in hh:mm:ss.ss and dd:mm:ss.s format
  </p>
  <pre>
  	cl&gt; skyxymatch image refimage coords rwxformat=%12.2H \<br>
  	    rwyformat=%12.1h wxformat=%12.2H wyformat=%12.1h
  </pre>
  <p>
  2. Given a list of ras and decs of objects in the reference image,
  compute a list of matched logical x and y coordinates for the two images,
  both of which have a accurate sky projection wcss, although the reference
  wcs is in equatorial coordinates and the input wcs is in galactic
  coordinates.  The ras and decs are in
  columns 3 and 4 of the input coordinate file and are in hh:mm:ss.ss and
  dd:mm:ss.s format respectively. Print the output world coordinates
  in the same units as the input.
  </p>
  <pre>
  	cl&gt; skyxymatch image refimage coords coords=radecs \<br>
  	    xcolumn=3 ycolumn=4 xunits=hours rwxformat=%12.2H \<br>
  	    rwyformat=%12.1h wxformat=%12.2H wyformat=%12.1h
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
  skyctran,wcsctran,geomap,geotran,skymap,sregister
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'FORMATS' 'REFERENCES' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
