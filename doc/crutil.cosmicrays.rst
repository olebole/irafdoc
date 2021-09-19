.. _cosmicrays:

cosmicrays: Remove cosmic rays using flux ratio algorithm
=========================================================

**Package: crutil**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  cosmicrays -- detect and replace cosmic rays
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  cosmicrays input output
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>List of input images in which to detect cosmic rays.
  </dd>
  </dl>
  <dl>
  <dt><b>output</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output' -->
  <dd>List of output images in which the detected cosmic rays will be replaced
  by an average of neighboring pixels.  If the output image name differs
  from the input image name then a copy of the input image is made with
  the detected cosmic rays replaced.  If no output images are specified
  then the input images are modified in place.  In place modification of
  an input image also occurs when the output image name is the same as
  the input image name.
  </dd>
  </dl>
  <dl>
  <dt><b>crmasks = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='crmasks' Line='crmasks = ""' -->
  <dd>List of cosmic ray mask files to be created; one for each input image.  If no
  file names are given then no cosmic ray mask is created.  If an existing
  mask is specified the newly detected cosmic rays will be added.
  </dd>
  </dl>
  <dl>
  <dt><b>threshold = 25.</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='threshold' Line='threshold = 25.' -->
  <dd>Detection threshold above the mean of the surrounding pixels for cosmic
  rays.  The threshold will depend on the noise characteristics of the
  image and how weak the cosmic rays may be for detection.  A typical value
  is 5 or more times the sigma of the background.
  </dd>
  </dl>
  <dl>
  <dt><b>fluxratio = 2.</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fluxratio' Line='fluxratio = 2.' -->
  <dd>The ratio (as a percent) of the mean neighboring pixel flux to the candidate
  cosmic ray pixel for rejection.  The value depends on the seeing and the
  characteristics of the cosmic rays.  Typical values are in the range
  2 to 10 percent.  This value may be reset interactively from a plot
  or defined by identifying selected objects as stars or cosmic rays.
  </dd>
  </dl>
  <dl>
  <dt><b>npasses = 5</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='npasses' Line='npasses = 5' -->
  <dd>Number of cosmic ray detection passes.  Since only the locally strongest
  pixel is considered a cosmic ray, multiple detection passes are needed to
  detect and replace cosmic ray events with multiple neighboring pixels.
  </dd>
  </dl>
  <dl>
  <dt><b>window = 5</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='window' Line='window = 5' -->
  <dd>Size of cosmic ray detection window.  A square window of either 5 by 5 or
  7 by 7 is used to detect cosmic rays.  The smaller window allows detection
  in the presence of greater background gradients but is less sensitive at
  discriminating multiple event cosmic rays from stars.  It is also marginally
  faster.
  </dd>
  </dl>
  <dl>
  <dt><b>interactive = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes' -->
  <dd>Examine parameters interactively?  A plot of the mean flux within the
  detection window (x100) vs the flux ratio (x100) is plotted and the user may
  set the flux ratio threshold, delete and undelete specific events, and
  examine specific events.  This is useful for new data in which one is
  uncertain of an appropriate flux ratio threshold.  Once determined the
  task need not be used interactively.
  </dd>
  </dl>
  <dl>
  <dt><b>train = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='train' Line='train = no' -->
  <dd>Define the flux ratio threshold by using a set of objects identified
  as stars (or other astronomical objects) or cosmic rays?
  </dd>
  </dl>
  <dl>
  <dt><b>objects = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='objects' Line='objects = ""' -->
  <dd>Cursor list of coordinates of training objects.  If null (the null string <tt>""</tt>)
  then the image display cursor will be read.  The user is responsible for first
  displaying the image.  Otherwise a file containing cursor coordinates
  may be given.  The format of the cursor file is <tt>"x y wcs key"</tt> where
  x and y are the pixel coordinates, wcs is an arbitrary number such as 1,
  and key may be <tt>'s'</tt> for star or <tt>'c'</tt> for cosmic ray.
  </dd>
  </dl>
  <dl>
  <dt><b>savefile = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='savefile' Line='savefile = ""' -->
  <dd>File to save (by appending) the training object coordinates.  This is of
  use when the objects are identified using the image display cursor.  The
  saved file can then be input as the object cursor list for repeating the
  execution.
  </dd>
  </dl>
  <dl>
  <dt><b>plotfile</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='plotfile' Line='plotfile' -->
  <dd>If a plot file is specified then the graph of the flux ratio (x100) vs
  the mean flux (x100) is recorded as metacode.  This may be spooled or examined
  later.
  </dd>
  </dl>
  <dl>
  <dt><b>graphics = <tt>"stdgraph"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"' -->
  <dd>Interactive graphic output device for interactive examination of the
  detection parameters.
  </dd>
  </dl>
  <dl>
  <dt><b>cursor = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""' -->
  <dd>Interactive graphics cursor input.  If null the graphics display cursor
  is used, otherwise a file containing cursor input may be specified.
  </dd>
  </dl>
  <dl>
  <dt><b>answer</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='answer' Line='answer' -->
  <dd>This parameter is used for interactive queries when processing a list of
  images.  The responses may be <tt>"no"</tt>, <tt>"yes"</tt>, <tt>"NO"</tt>, or <tt>"YES"</tt>.  The upper case
  responses permanently enable or disable the interactive review while
  the lower case reponses allow selective examination of certain input
  images.  <i>This parameter should not be specified on the command line.
  If it is then the value will be ignored and the task will act as if
  the answer "yes" is given for each image; i.e. it will enter the interactive
  phase without prompting.</i>
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Image cursor commands</h3>
  <!-- BeginSection: 'IMAGE CURSOR COMMANDS' -->
  <pre>
  ?	Help
  c	Identify the object as a cosmic ray
  s	Identify the object as a star
  g	Switch to the graphics plot
  q	Quit and continue with the cleaning
  </pre>
  <p>
  GRAPHICS CURSOR COMMANDS
  </p>
  <pre>
  ?	Help
  a	Toggle between showing all candidates and only the training points
  d	Mark candidate for replacement (applys to <tt>'+'</tt> points)
  e	Mark candidates in a region for replacement (applys to <tt>'+'</tt> points)
  q	Quit and return to image cursor or replace the selected pixels
  r	Redraw the graph
  s	Make a surface plot for the candidate nearest the cursor
  t	Set the flux ratio threshold at the y cursor position
  u	Mark candidate to not be replaced (applys to <tt>'x'</tt> points)
  v	Mark candidates in a region to not be replaced (applys to <tt>'x'</tt> points)
  w	Adjust the graph window (see <b>gtools</b>)
  &lt;space&gt;	Print the pixel coordinates
  </pre>
  <p>
  There are no colon commands except those for the windowing options (type
  :\help or see <b>gtools</b>).
  </p>
  <!-- EndSection:   'IMAGE CURSOR COMMANDS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Cosmic ray events in each input image are detected and replaced by the
  average of the four neighbors.  The replacement may be performed
  directly on the input image if no output image is specified or if the
  output image name is the same as the input image name.  If a new image
  is created it is a copy of the input image except for the replaced
  pixels.  
  Optional output includes
  a plot file showing the parameters of the
  detected cosmic ray candidates and the flux ratio threshold used, a
  cosmic ray mask identifying the cosmic rays found, and
  a file of training objects marked with the image display cursor.  The
  cosmic ray mask may be used for display purposes, combined with other
  masks, and with <b>crfix</b>.
  </p>
  <p>
  This task may be applied to an image previously processed to detect
  additional cosmic rays.
  </p>
  <p>
  The cosmic ray detection algorithm consists of the following steps.
  First a pixel must be the brightest pixel within the specified
  detection window (either 5x5 or 7x7).  The mean flux in the surrounding
  pixels with the second brightest pixel excluded (which may also be a
  cosmic ray event) is computed and the candidate pixel must exceed this
  mean by the amount specified by the parameter <i>threshold</i>.  A plane
  is fit to the border pixels of the window and the fitted background is
  subtracted.  The mean flux (now background subtracted) and the ratio of
  this mean to the cosmic ray candidate (the brightest pixel) are
  computed.  The mean flux (x100) and the ratio (x100) are recorded for
  interactive examination if desired.
  </p>
  <p>
  Once the list of cosmic ray candidates has been created and a threshold for
  the flux ratio established (by the parameter <i>fluxratio</i>, by the
  <tt>"training"</tt> method, or by using the graphics cursor in the interactive plot)
  the pixels with ratios below the threshold are replaced in the output by
  the average of the four neighboring pixels (with the second strongest pixel
  in the detection window excluded if it is one of these pixels).  Additonal
  pixels may then be detected and replaced in further passes as specified by
  the parameter <i>npasses</i>.  Note that only pixels in the vicinity of
  replaced pixels need be considered in further passes.
  </p>
  <p>
  The division between the peaks of real objects and cosmic rays is made
  based on the flux ratio between the mean flux (excluding the center
  pixel and the second strongest pixel) and the candidate pixel.  This
  threshold depends on the point spread function and the distribution of
  multiple cosmic ray events and any additional neighboring light caused
  by the events.  This threshold is not strongly coupled to small changes
  in the data so that once it is set for a new type of image data it may
  be used for similar images.  To set it initially one may examine the
  scatter plot of the flux ratio as a function of the mean flux.  This
  may be done interactively or from the optional plot file produced.
  </p>
  <p>
  After the initial list of cosmic ray candidates has been created and before
  the final replacing cosmic rays there are two optional steps to allow
  examining the candidates and setting the flux ratio threshold dividing
  cosmic rays from real objects.  The first optional step is define the flux
  ratio boundary by reference to user specified classifications; that is
  <tt>"training"</tt>.  To do this step the <i>train</i> parameter must be set to yes.
  The user classified objects are specified by a cursor input list.  This
  list can be an actual file or the image display cursor as defined by the
  <i>objects</i> parameter.  The <i>savefile</i> parameter is also used during
  the training to record the objects specified.  The parameter specifies a
  file to append the objects selected.  This is useful when the objects are
  defined by interactive image cursor and does not make much sense when using
  an input list.
  </p>
  <p>
  If the <i>objects</i> parameter is specified as a null string then
  the image display cursor will be repeatedly read until a <tt>'q'</tt> is
  entered.  The user first displays the image and then when the task
  reads the display cursor the cursor shape will change.  The user
  points at objects and types <tt>'s'</tt> for a star (or other astronomical
  object) and <tt>'c'</tt> for a cosmic ray.  Note that this input is used
  to search for the matching object in the cosmic ray candidate list
  and so it is possible the selected object is not in the list though
  it is unlikely.  The selection will be quietly ignored in that case.
  To exit the interactive selection of training objects type <tt>'q'</tt>.
  </p>
  <p>
  If <tt>'g'</tt> is typed a graph of all the candidates is drawn showing
  <tt>"flux"</tt> vs. <tt>"flux ratio"</tt> (see below for more).  Training objects will
  be shown with a box and the currently set flux ratio threshold will
  also be shown.  Exiting the plot will return to entering more training
  objects.  The plot will remain and additional objects will immediately
  be shown with a new box.  Thus, if one wants to see the training
  objects identified in the plot as one selects them from the image
  display first type a <tt>'g'</tt> to draw the initial plot.  Also by switching
  to the plot with <tt>'g'</tt> allows you to draw surface plots (with <tt>'s'</tt>) or
  get the pixel coordinates of a candidate (the space key) to be
  found in the display using the coordinate readout of the display.
  Note that the display interaction is simpler than might be desired
  because this task does not directly connect to the display.
  </p>
  <p>
  The most likely use for training is with the interactive image display.
  However one may prepare an input list by other means, one example
  is with <b>rimcursor</b>, and then specify the file name.  The savefile
  may also be used a cursor input to repeat the cosmic ray operation
  (but be careful not to have the cursor input and save file be the
  same file!).
  </p>
  <p>
  The flux ratio threshold is determined from the training objects by
  finding the point with the minimum number of misclassifications
  (stars as cosmic rays or cosmic rays as stars).  The threshold is
  set at the lowest value so that it will always go through one of
  the cosmic ray objects.  There should be at least one of each type
  of object defined for this to work.  The following option of
  examining the cosmic ray candidates and parameters may still be
  used to modify the derived flux ratio threshold.  One last point
  about the training objects is that even if some of the points
  lie on the wrong side of the threshold they will remain classified
  as cosmic ray or non-cosmic ray.  In other words, any object
  classified by the user will remain in that classification regardless
  of the final flux ratio threshold.
  </p>
  <p>
  After the training step the user will be queried to examine the candidates
  in the flux vs flux ratio plane if the <i>interactive</i> flag is set.
  Responses may be made for specific images or for all images by using
  lower or upper case answers respectively.  When the parameters are
  examined interactively the user may change the flux ratio threshold
  (<tt>'t'</tt> key).  Changes made are stored in the parameter file and, thus,
  learned for further images.  Pixels to be deleted are marked by crosses
  and pixels which are peaks of objects are marked by pluses.  The user
  may explicitly delete or undelete any point if desired but this is only
  for special cases near the threshold.  In the future keys for
  interactive display of the specific detections will be added.
  Currently a surface plot of any candidate may be displayed graphically
  in four 90 degree rotated views using the <tt>'s'</tt> key.  Note that the
  initial graph does not show all the points some of which are clearly
  cosmic rays because they have negative mean flux or flux ratio.  To
  view all data one must rewindow the graph with the <tt>'w'</tt> key or <tt>":/"</tt>
  commands (see <b>gtools</b>).
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. To replace cosmic rays in a set of images ccd* without training:
  </p>
  <pre>
      cl&gt; cosmicrays ccd* new//ccd*
      ccd001: Examine parameters interactively? (yes):
      [A scatter plot graph is made.  One can adjust the threshold.]
      [Looking at a few points using the <tt>'s'</tt> key can be instructive.]
      [When done type <tt>'q'</tt>.]
      ccd002: Examine parameters interactively? (yes): NO
      [No further interactive examination is done.]
  </pre>
  <p>
  After cleaning one typically displays the images and  possibly blinks them.
  A difference image or mask image may also be created.
  </p>
  <p>
  2. To use the interactive training method for setting the flux ratio threshold:
  </p>
  <pre>
      # First display the image.
      cl&gt; display ccd001 1
      z1 = 123.45 z2= 543.21
      cl&gt; cosmicrays ccd001 ccd001cr train+
      [After the cosmic ray candidates are found the image display
      [cursor will be activated.  Mark a cosmic ray with <tt>'c'</tt> and
      [a star with <tt>'s'</tt>.  Type <tt>'g'</tt> to get a plot showing the two
      [points with boxes.  Type <tt>'q'</tt> to go back to the image display.
      [As each new object is marked a box will appear in the plot and
      [the threshold may change.  To find the location of an object
      [seen in the plot use <tt>'g'</tt> to go to the graph, space key to find
      [the pixel coordinates, <tt>'q'</tt> to go back to the image display,
      [and the image display coordinate box to find the object.
      [When done with the training type <tt>'q'</tt>.
      ccd001: Examine parameters interactively? (yes): no
  </pre>
  <p>
  3.  To create a mask image a bad pixel file must be specified.
  </p>
  <pre>
      cl&gt; cosmicrays ccd001 ccd001 crmask=crccd001
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  crmedian, crnebula, crgrow, crfix, credit, gtools, imedit, rimcursor
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'IMAGE CURSOR COMMANDS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
