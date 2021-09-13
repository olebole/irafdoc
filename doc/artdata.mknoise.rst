.. _mknoise:

mknoise — Make/add noise and cosmic rays to 1D/2D images
========================================================

**Package: artdata**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  mknoise - Make/add noise and cosmic rays to 1D/2D images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Images to create or modify.
  </DD>
  </DL>
  <DL>
  <DT><B>output = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = ""'>
  <DD>Output images when modifying input images.  If no output images are
  given then existing images in the input list are modified directly.
  If an output image list is given then it must match in number the
  input list.
  </DD>
  </DL>
  <P>
  WHEN CREATING NEW IMAGES
  <DL>
  <DT><B>title = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='title' Line='title = ""'>
  <DD>Image title to be given to the images.  Maximum of 79 characters.
  </DD>
  </DL>
  <DL>
  <DT><B>ncols = 512, nlines = 512</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols = 512, nlines = 512'>
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
  <P>
  NOISE PARAMETERS
  <DL>
  <DT><B>background = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='background' Line='background = 0.'>
  <DD>Background to add to images before computing Poisson noise.
  </DD>
  </DL>
  <DL>
  <DT><B>gain = 1.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gain' Line='gain = 1.'>
  <DD>Gain in electrons per data number.  The gain is used for scaling the
  read noise parameter and in computing poisson noise.
  </DD>
  </DL>
  <DL>
  <DT><B>rdnoise = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rdnoise' Line='rdnoise = 0.'>
  <DD>Gaussian read noise in electrons.
  </DD>
  </DL>
  <DL>
  <DT><B>poisson = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='poisson' Line='poisson = no'>
  <DD>Add poisson noise?  Note that any specified background is added to new
  or existing images before computing the Poisson noise.
  </DD>
  </DL>
  <DL>
  <DT><B>seed = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='seed' Line='seed = 1'>
  <DD>Random number seed.  If a value of "<TT>INDEF</TT>" is given then the clock
  time (integer seconds since 1980) is used as the seed yielding
  different random numbers for each execution.
  </DD>
  </DL>
  <P>
  COSMIC RAYS
  <DL>
  <DT><B>cosrays = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cosrays' Line='cosrays = ""'>
  <DD>List of cosmic ray files.  Cosmic ray files contain lines of cosmic ray
  coordinates and energy (see DESCRIPTION section).  If no
  file or a new (nonexistent) file is specified then a number of random
  cosmic rays given by the parameter <I>ncosrays</I> is generated.  If a
  new file name is specified then the events generated are recorded in the
  file.  If the list of cosmic ray files is shorter than the list of
  input images then the last cosmic ray file is reused.
  </DD>
  </DL>
  <DL>
  <DT><B>ncosrays = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncosrays' Line='ncosrays = 0'>
  <DD>If no cosmic ray file or a new file is specified then the task will
  generate this number of random cosmic rays.  The positions are
  uniformly random within the limits of the image and the energy is
  uniformly random between zero and a maximum.
  </DD>
  </DL>
  <DL>
  <DT><B>energy = 30000.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='energy' Line='energy = 30000.'>
  <DD>When generating random events the cosmic rays will have a uniform energy
  distribution (in electrons) between zero and this maximum.
  </DD>
  </DL>
  <DL>
  <DT><B>radius = 0.5</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='radius' Line='radius = 0.5'>
  <DD>The half-intensity radius of gaussian profile cosmic rays in pixels
  along the major axis.
  </DD>
  </DL>
  <DL>
  <DT><B>ar = 1.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ar' Line='ar = 1.'>
  <DD>Minor to major axial ratio for cosmic rays.
  </DD>
  </DL>
  <DL>
  <DT><B>pa = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pa' Line='pa = 0.'>
  <DD>Position angle in degrees measured counterclockwise from the X axis for
  cosmic rays.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>comments = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='comments' Line='comments = yes'>
  <DD>Include comments recording task parameters in the image header?
  </DD>
  </DL>
  <P>
  PACKAGE PARAMETERS
  <P>
  These parameters define certain computational shortcuts which greatly
  affect the computational speed.  They should be adjusted with care.
  <DL>
  <DT><B>nxc = 5, nyc = 5</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nxc' Line='nxc = 5, nyc = 5'>
  <DD>Number of cosmic ray centers per pixel in X and Y.  Rather than evaluate
  cosmic rays precisely at each subpixel coordinate, a set of templates
  with a grid of subpixel centers is computed and then the nearest template to
  the desired position is chosen.  The larger the number the more memory
  and startup time required.
  </DD>
  </DL>
  <DL>
  <DT><B>nxsub = 10, nysub = 10</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nxsub' Line='nxsub = 10, nysub = 10'>
  <DD>Number of pixel subsamples in X and Y used in computing the cosmic
  ray profiles.  This is the subsampling in the central
  pixel and the number of subsamples decreases linearly from the center.
  This affects the time required to compute the cosmic ray templates.
  </DD>
  </DL>
  <DL>
  <DT><B>dynrange = 100000.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dynrange' Line='dynrange = 100000.'>
  <DD>The intensity profile of the gaussian cosmic rays extends to infinity so
  a dynamic range, the ratio of the peak intensity to the cutoff
  intensity, is imposed.  Because the cosmic rays are small this parameter
  is not critical.
  </DD>
  </DL>
  <DL>
  <DT><B>ranbuf = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ranbuf' Line='ranbuf = 0'>
  <DD>Random number buffer size.  When generating readout and poisson noise,
  evaluation of new random values has an affect on the execution time.
  If truly (or computationally truly) random numbers are not needed
  then this number of random values is stored and a simple
  uniform random number is used to select from the stored values.
  To force evaluation of new random values for every pixel set the
  value of this parameter to zero.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task creates or modifies images with readout noise, poisson noise,
  and cosmic ray events.  New images are created with the specified
  dimensions and real datatype.  Existing images may be modified in place
  or new images may be created.
  <P>
  If a new image is created it is has the mean level given by the parameter
  <I>background</I>.  With no noise and no cosmic rays this task can be used to
  create images of constant background value.  For existing images the
  background is added before computing any noise.  To add noise to an
  existing image without modifying the mean counts set the background
  to zero.
  <P>
  For new images a set of header keywords may be added by specifying an
  image or data file with the <I>header</I> parameter (see also <B>mkheader</B>).
  If a data file is specified lines beginning with FITS keywords are
  entered in the image header.  Leading whitespace is ignored and any
  lines beginning with words having lowercase and nonvalid FITS keyword
  characters are ignored.  In addition to this optional header,
  keywords, parameters for the gain and read noise are defined.
  Finally, comments may be added to the image header recording the task
  parameters and any information from the cosmic ray file which are not
  cosmic ray definitions.
  <P>
  Poisson photon noise is generated by setting the <I>poisson</I> parameter.
  For new images the input data value is the background while for
  existing images the input data value is added to the background value.
  The data value is then multiplied by the gain, a poisson deviate is
  generated, and divided by the gain.  Expressed as a formula:
  <P>
  <PRE>
        New images: out = P(background * gain) / gain
   Existing images: out = P((in+background)*gain) / gain
  </PRE>
  <P>
  where P(x) is a poisson deviate with mean x, in and out are the input
  and final pixel values, and background and gain are the parameter
  values of the same name.
  <P>
  Readout or gaussian noise is generated by specifying a gaussian sigma with
  the parameter <I>rdnoise</I>.  The sigma is divided by the specified gain
  to convert to image data units.  Gaussian random numbers of mean zero are
  then generated for each pixel and added to the image, or background
  value for new images, after the photon noise is computed.
  <P>
  Generating gaussian and poisson random numbers computationally is
  the main determinant of the execution time in this task.
  Two things are done to speed up the task.
  First, the gaussian approximation is used for data values greater
  than 20 (after applying the background and gain).  The square root
  of the data value is used as the gaussian sigma about the data
  value.  For values less than 20 a true poisson deviate is generated.
  The second speed up is to allow storing a number of normalized gaussian
  values given by the package parameter <I>ranbuf</I> as they are generated.  If
  more values than this are desired then a uniform random number is used
  to select one of these stored values.  This applies to both the read noise
  and poisson noise gaussian approximation though not the true poisson
  evaluation.  For most purposes this approximation is good and one would
  need to look very hard to detect the nonrandomness in the noise.
  However, if one wants to take the extra computational time then
  by setting the <I>ranbuf</I> parameter to zero each gaussian
  random number will be generated independently.
  <P>
  The cosmic ray model is an elliptical gaussian of specified
  half-intensity radius, axial ratio, and position angle.  Normally the
  radius will be small (smaller than the point spread function) and the
  axial ratio will be 1.  The cosmic rays are subsampled and can have the
  number of centers given by the <I>nxc/nyc</I> package parameters.  The method
  of generating the cosmic rays is that described for the task
  <B>mkobjects</B>.  Specifically it is the same as adding gaussian
  profile stars.
  <P>
  The total flux (not the peak) of the cosmic ray is given by the energy
  in electrons so that the value is divided by the gain to produce the
  total flux in the image.  Note that this task can be used to add cosmic
  ray spikes to one dimensional images such as spectra but the strengths
  will appear low because of the part of the event which falls outside
  the single line.
  <P>
  The positions and energies of the cosmic rays can be specified in a
  file or the task can generate random events.  Specific cosmic rays are
  specified by a file containing lines of x and y positions and energy.
  Positions outside the limits of the image are ignored.  If no cosmic
  ray file is given or if a new, nonexistent file is named then the
  number of cosmic rays given by the <I>ncosrays</I> parameter is
  generated with uniform spatial distribution within the image and
  uniform energy distribution between zero and that given by the
  <I>energy</I> parameter.  By giving a new file name the randomly
  generated cosmic rays will be recorded for reuse or to allow
  identifying the events while testing tasks and algorithms.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Create a new image with a background of 1000, a read noise
  of 10 electrons, a gain of 2, and 50 random cosmic rays.  Don't keep a
  record of the cosmic rays.
  <P>
  <PRE>
  	cl&gt; mknoise testim back=1000 rd=10 gain=2 poisson+ ncos=50
  </PRE>
  <P>
  2. Add cosmic rays to an image and create a new output image.
  <P>
  <PRE>
  	cl&gt; head cosfile
  	20.3 50.1 1000
  	325.6 99.6 250
  	cl&gt; mknoise dev$pix out=newpix cos=cosfile
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>MKNOISE V2.11+</B></DT>
  <! Sec='REVISIONS' Level=0 Label='MKNOISE' Line='MKNOISE V2.11+'>
  <DD>The random number seed can be set from the clock time by using the value
  "<TT>INDEF</TT>" to yield different random numbers for each execution.
  </DD>
  </DL>
  <DL>
  <DT><B>MKNOISE V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='MKNOISE' Line='MKNOISE V2.11'>
  <DD>The default value of "<TT>ranbuf</TT>" was changed to zero.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  mkobjects, mkheader
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
