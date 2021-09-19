.. _addstar:

addstar: Add artificial stars to an image using the computed psf
================================================================

**Package: daophot**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  addstar -- add artificial stars to images
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  addstar image photfile psfimage addimage
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>image</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='image' Line='image' -->
  <dd>The list of images to which artificial stars are to be added.
  </dd>
  </dl>
  <dl>
  <dt><b>photfile</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='photfile' Line='photfile' -->
  <dd>The list of photometry files containing the x and y coordinates and magnitudes
  of the artificial stars to be added to <i>image</i>. If photfile is undefined,
  then <i>nstar</i> artificial stars uniformly distributed in position, and  in
  magnitude between <i>minmag</i> and <i>maxmag</i> are added to <i>image</i>. If
  photfile is defined, there must be one photometry file for every input image.
  Photfile may be a simple text file containing x, y, magnitude, and id number in
  columns 1, 2, 3, and 4 respectively (<i>simple_text</i> = yes), an APPHOT/DAOPHOT
  text database file (<i>simple_text</i> = no), or an STSDAS binary table file.
  </dd>
  </dl>
  <dl>
  <dt><b>psfimage</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='psfimage' Line='psfimage' -->
  <dd>The list of images containing the PSF models computed by the DAOPHOT PSF task.
  The number of PSF images must be equal to the number of input images. If
  psfimage is <tt>"default"</tt>, <tt>"dir$default"</tt>, or a directory specification, then PEAK
  will look for an image with the name image.psf.?, where ? is the highest
  existing version number.
  </dd>
  </dl>
  <dl>
  <dt><b>addimage</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='addimage' Line='addimage' -->
  <dd>The root name of the output images. There must be one output root image name
   for every input image. If addimage is <tt>"default"</tt>, <tt>"dir$default"</tt> or a directory
  specification, then an output artificial image and artificial star list called
  image.add.? and image.art.? respectively are created, where ? is the next
  available version number. If the DAOPHOT  package parameter <i>text</i> is <tt>"yes"</tt>,
  then an APPHOT/DAOPHOT text database file is written, otherwise an STSDAS binary
  table is written.
  </dd>
  </dl>
  <dl>
  <dt><b>minmag</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='minmag' Line='minmag' -->
  <dd>The minimum magnitude of the computer generated artificial stars to be
  added to the image. The actual intensities of the pixels in the artificial
  stars are computed with respect to the magnitude of the PSF stored in
  <i>psfimage</i>.
  </dd>
  </dl>
  <dl>
  <dt><b>maxmag</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='maxmag' Line='maxmag' -->
  <dd>The maximum magnitude of the computer generated artificial stars to be
  added to the image. The actual intensities of the pixels in the artificial
  stars are computed with respect to the magnitude of the PSF stored in
  <i>psfimage</i>.
  </dd>
  </dl>
  <dl>
  <dt><b>nstar</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='nstar' Line='nstar' -->
  <dd>The number of computer generated artificial stars to be added to the input
  image.
  </dd>
  </dl>
  <dl>
  <dt><b>datapars = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='datapars' Line='datapars = ""' -->
  <dd>The text file in which the data dependent parameters are stored. The gain
  parameter <i>epadu</i> in electrons per ADU is stored here.  If datapars is
  undefined then the default parameter set in the user's uparm directory is used.
  </dd>
  </dl>
  <dl>
  <dt><b>daopars = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='daopars' Line='daopars = ""' -->
  <dd>The text file in which the daophot fitting parameters are stored. The PSF
  radius parameter <i>psfrad</i> in scale units is stored here. If daopars is
  undefined then the default parameter set in the user's uparm directory is used.
  </dd>
  </dl>
  <dl>
  <dt><b>simple_text = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='simple_text' Line='simple_text = no' -->
  <dd>If <i>photfile</i> is a text file and <i>simple_text</i> = <tt>"no"</tt>, then ADDSTAR
  expects an APPHOT/DAOPHOT database. Otherwise ADDSTAR expects a simple list
  format with x, y, magnitude, and id in columns 1, 2,3, and 4 respectively.
  </dd>
  </dl>
  <dl>
  <dt><b>seed = 0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='seed' Line='seed = 0' -->
  <dd>The seed for the random number generator used to generate the positions
  and magnitudes of the artificial stars.
  </dd>
  </dl>
  <dl>
  <dt><b>nimage = 1</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='nimage' Line='nimage = 1' -->
  <dd>The number of output images to be created per input image.
  </dd>
  </dl>
  <dl>
  <dt><b>idoffset = 0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='idoffset' Line='idoffset = 0' -->
  <dd>The integer offset to be added to the id numbers of stars in the output
  artificial photometry file. By default the artificial stars are numbered from 1
  to N where N is the number of artificial stars added to the input frame.
  </dd>
  </dl>
  <dl>
  <dt><b>wcsin = <tt>")_.wcsin"</tt>, wcsout = <tt>")_.wcsout"</tt>, wcspsf = <tt>")_.wcspsf"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='wcsin' Line='wcsin = ")_.wcsin", wcsout = ")_.wcsout", wcspsf = ")_.wcspsf"' -->
  <dd>The coordinate system of the input coordinates read from <i>photfile</i>, of the
  psf model <i>psfimage</i>, and of the output coordinates written to
  <i>addimage</i> respectively. The image header coordinate system is used to
  transform from the input coordinate system to the <tt>"logical"</tt> pixel coordinate
  system used internally, from the internal logical system to the PSF model
  system, and from the internal <tt>"logical"</tt> pixel coordinate system to the output
  coordinate system. The input coordinate system options are <tt>"logical"</tt>, <tt>"tv"</tt>,
  <tt>"physical"</tt>, and <tt>"world"</tt>. The PSF model and output coordinate system options
  are <tt>"logical"</tt>, <tt>"tv"</tt>, and <tt>"physical"</tt>. The image cursor coordinate system is
  assumed to be the <tt>"tv"</tt> system.
  <dl>
  <dt><b>logical</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='logical' Line='logical' -->
  <dd>Logical coordinates are pixel coordinates relative to the current image.
  The  logical coordinate system is the coordinate system used by the image
  input/output routines to access the image data on disk. In the logical
  coordinate system the coordinates of the first pixel of a  2D image, e.g.
  dev$ypix  and a 2D image section, e.g. dev$ypix[200:300,200:300] are
  always (1,1).
  </dd>
  </dl>
  <dl>
  <dt><b>tv</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='tv' Line='tv' -->
  <dd>Tv coordinates are the pixel coordinates used by the display servers. Tv
  coordinates  include  the effects of any input image section, but do not
  include the effects of previous linear transformations. If the input
  image name does not include an image section, then tv coordinates are
  identical to logical coordinates.  If the input image name does include a
  section, and the input image has not been linearly transformed or copied from
  a parent image, tv coordinates are identical to physical coordinates.
  In the tv coordinate system the coordinates of the first pixel of a
  2D image, e.g. dev$ypix and a 2D image section, e.g. dev$ypix[200:300,200:300]
  are (1,1) and (200,200) respectively.
  </dd>
  </dl>
  <dl>
  <dt><b>physical</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='physical' Line='physical' -->
  <dd>Physical coordinates are pixel coordinates invariant  with respect to linear
  transformations of the physical image data.  For example, if the current image
  was created by extracting a section of another image,  the  physical
  coordinates of an object in the current image will be equal to the physical
  coordinates of the same object in the parent image,  although the logical
  coordinates will be different.  In the physical coordinate system the
  coordinates of the first pixel of a 2D image, e.g. dev$ypix and a 2D
  image section, e.g. dev$ypix[200:300,200:300] are (1,1) and (200,200)
  respectively.
  </dd>
  </dl>
  <dl>
  <dt><b>world</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='world' Line='world' -->
  <dd>World coordinates are image coordinates in any units which are invariant
  with respect to linear transformations of the physical image data. For
  example, the ra and dec of an object will always be the same no matter
  how the image is linearly transformed. The units of input world coordinates
  must be the same as those expected by the image header wcs, e. g.
  degrees and degrees for celestial coordinate systems.
  </dd>
  </dl>
  The wcsin, wcspsf, and wcsout parameters default to the values of the package
  parameters of the same name. The default values of the package parameters
  wcsin, wcspsf,  and wcsout are <tt>"logical"</tt>, <tt>"physical"</tt> and <tt>"logical"</tt> respectively.
  </dd>
  </dl>
  <dl>
  <dt><b>cache = <tt>")_.cache"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='cache' Line='cache = ")_.cache"' -->
  <dd>Cache the image pixels in memory. Cache may be set to the value of the apphot
  package parameter (the default), <tt>"yes"</tt>, or <tt>"no"</tt>. By default caching is
  disabled.
  </dd>
  </dl>
  <dl>
  <dt><b>verify = <tt>")_.verify"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verify' Line='verify = ")_.verify"' -->
  <dd>Verify the critical ADDSTAR task parameters? Verify may be set to the
  daophot package parameter value (the default), <tt>"yes"</tt>, or <tt>"no"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>update = <tt>")_.update"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='update' Line='update = ")_.update"' -->
  <dd>Update the critical ADDSTAR task parameters if <i>verify</i> = <tt>"yes"</tt>?
  Update may be set to the daophot package parameter value (the default),
  <tt>"yes"</tt>, or <tt>"no"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = <tt>")_.verbose"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = ")_.verbose"' -->
  <dd>Print messages about the progress of ADDSTAR? Verbose may be set to the
  daophot package parameter value (the default), <tt>"yes"</tt>, or <tt>"no"</tt>.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  ADDSTAR adds artificial stars, whose positions and magnitudes are listed in
  <i>photfile</i> or generated at random by the computer, to the input image
  <i>image</i> using the PSF in <i>psfimage</i>, and writes the result to the
  output image and output photometry file <i>addimage</i>. If <i>photfile</i> is
  undefined then ADDSTAR generates an artificial photometry list containing
  <i>nstar</i> stars uniformly distributed in position over the image and in
  magnitude between <i>minmag</i> and <i>maxmag</i>. The input photometry file
  may be an STSDAS binary table or an APPHOT/DAOPHOT text database file (the
  output of the PHOT, PSF, PEAK, NSTAR, or ALLSTAR tasks) or a simple text file
  with the x and y positions, magnitude, and id in columns 1, 2, 3 and 4
  respectively. The ids of stars in the output photometry file may be set to
  numbers outside the range of the real data by setting the parameter
  <i>offset</i>. Several output images may be written for each input image by
  setting the parameter <i>nimage</i> greater than 1.
  </p>
  <p>
  The coordinates read from <i>photfile</i> are assumed to be in coordinate
  system defined by <i>wcsin</i>. If photfile is undefined the input coordinate
  system is logical. The options are <tt>"logical"</tt>, <tt>"tv"</tt>, <tt>"physical"</tt>, and <tt>"world"</tt>
  and the transformation from the input coordinate system to the internal
  <tt>"logical"</tt> system is defined by the image coordinate system. The simplest
  default is the <tt>"logical"</tt> pixel system. Users working on with image sections but
   importing pixel coordinate lists generated from the parent image must use the
  <tt>"tv"</tt> or <tt>"physical"</tt> input coordinate systems.
  </p>
  <p>
  The coordinate system of the PSF model is the coordinate system defined by the
  <i>wcspsf</i> parameter. Normally the PSF model was derived from the input image
  and this parameter default to <tt>"logical"</tt>. However if the PSF model was derived
  from a larger image which is a <tt>"parent"</tt> of the input image, then wcspsf should
  be set to <tt>"tv"</tt> or <tt>"physical"</tt> depending on the circumstances.
  </p>
  <p>
  The coordinates written to <i>addimage</i> are in the coordinate system defined
  by <i>wcsout</i>.  The options are <tt>"logical"</tt>, <tt>"tv"</tt>, and <tt>"physical"</tt>. The simplest
  default is the <tt>"logical"</tt> system.  Users wishing to correlate the output
  coordinates of objects measured in image sections or mosaic pieces with
  coordinates in the parent image must use the <tt>"tv"</tt> or <tt>"physical"</tt> coordinate
  systems.
  </p>
  <p>
  If <i>cache</i> is yes and the host machine physical memory and working set size
  are large enough, the output image pixels are cached in memory. If caching
  is enabled and the first artificial star addition will appear
  to take a long time as the entire input image must be read into the output
  image before the first artificial star addition is actually made. All
  subsequent measurements will be very fast because ADDSTAR is accessing memory
  not disk. The point of caching is to speed up random image access by making
  the internal image i/o buffers the same size as the image itself. However if
  the input object lists are sorted in row order and sparse caching may actually
  worsen not improve the execution time. Also at present there is no point in
  enabling caching for images that are less than or equal to 524288 bytes, i.e.
  the size of the test image dev$ypix, as the default image i/o buffer is exactly
  that size. However if the size of dev$ypix is doubled by converting it to a
  real image with the chpixtype task then the effect of caching in interactive
  is can be quite noticeable if measurements of objects in the top and bottom
  halves of the image are alternated.
  </p>
  <p>
  The intensities in the artificial stellar images are computed relative to the
  intensities in the PSF image, by scaling the magnitudes of the artificial stars
  to the magnitude of the PSF in <i>psfimage</i>. Poisson noise is added to the
  artificial stars using the value of the gain stored in the image header keyword
  specified by the DATAPARS parameter <i>gain</i> if present, or the value of the
  DATAPARS parameter <i>epadu</i>.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Output</h3>
  <!-- BeginSection: 'OUTPUT' -->
  <p>
  If <i>verbose</i> = yes, a line of output is written to the terminal for each
  artificial star added to the input image.
  </p>
  <p>
  Full output is written to the output photometry file <i>addimage</i>. At the
  beginning of each file is a header listing the current values of all the
  parameters. For each artificial star added to the input image the following
  record is written.
  </p>
  <pre>
  	id  xcenter  ycenter  mag
  </pre>
  <p>
  Id is the id number of the star, xcenter and ycenter are its coordinates, and
  mag is its magnitude.
  </p>
  <!-- EndSection:   'OUTPUT' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Add 30 stars uniformly distributed between 17 and 20th magnitude and in
  position to the input image m92. Display the new image and mark the
  artificial stars. Good stars for making the PSF model can be found at
  (442,410), (348,189), and (379,67).
  </p>
  <pre>
      da&gt; daofind dev$ypix default fwhmpsf=2.5 sigma=5.0 threshold=20.0
  
          ... answer verify prompts
  
          ... find stars in the image
  
          ... answer will appear in ypix.coo.1
  
      da&gt; phot dev$ypix default default annulus=10. dannulus=5.       \<br>
          apertures = 5.0
  
          ... answer verify prompts
  
          ... do aperture photometry on the detected stars
  
          ... answer will appear in ypix.mag.1
  
      da&gt; display dev$ypix 1
  
  	... display the image
  
      da&gt; psf dev$ypix default "" default default default psfrad=9.0 \<br>
          fitrad=3.0 mkstars=yes display=imdr
  
          ... verify the critical parameters
  
          ... move the image cursor to a candidate star and hit the a key,
              a plot of the stellar data appears
  
          ... type ? for a listing of the graphics cursor menu
  
          ... type a to accept the star, d to reject it
  
          ... move to the next candidate stars and repeat the previous
              steps
  
          ... type l to list all the psf stars
  
          ... type f to fit the psf
  
          ... move cursor to first psf star and type s to see residuals,
              repeat for all the psf stars
  
          ... type w to save the PSF model
  
          ... type q to quit, and q again to confirm
  
          ... the output will appear in ypix.psf.1.imh, ypix.pst.1 and
              ypix.psg.1
  
      da&gt; addstar dev$ypix "" default default 12.0 17.0 30 epadu=14.0
  
  	... verify the critical parameters
  
      da&gt; display ypix.add.1 2
  
  	... display the artificial image
  
      da&gt; pdump ypix.art.1 xcenter,ycenter yes | tvmark 2 STDIN col=204
  
  	... mark the stars on the artificial image
  </pre>
  <p>
  2. Repeat example 1 using the output starlist as input.
  </p>
  <pre>
      da&gt; addstar dev$ypix ypix.art.1  default default simple- epadu=14.0
  
      ... the answers will appear in ypix.add.2 and ypix.art.2
  </pre>
  <p>
  3. Repeat example 1 using a simple text file as input.
  </p>
  <pre>
      da&gt; pdump ypix.art.1 xc,yc,mag yes &gt; artdata
  
      ... create a simple text file from the addstar output
  
      da&gt; addstar dev$ypix artdata default default simple+ epadu=14.0
  
      ... the answers will appear in ypix.add.3 and ypix.art.3
  </pre>
  <p>
  4. Run addstar on a section of the input image using the PSF model derived in
  example 1 for the parent image, the artificial star list from examples 2 and
  3, and write the results in the coordinate system of the image section
  not the parent image.
  </p>
  <pre>
     da&gt; addstar dev$ypix[150:450,150:450] artdata default default simple+ \<br>
         epadu=14.0 wcsin=tv wcspsf=tv wcsout=logical
  
          ... answer the verify prompts
  
          ... fit the stars
  
          ... the results will appear in ypix.add.4 and ypix.art.4
  
      da&gt; display ypix.add.4 1
  
          ... display the image
  
      da&gt; pdump ypix.art.4 xc,yc yes | tvmark 1 STDIN col=204
  
          ... mark the stars
  
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
  datapars,daopars
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'OUTPUT' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
