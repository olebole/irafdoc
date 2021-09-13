cosmicrays — Remove cosmic rays using flux ratio algorithm
==========================================================

**Package: crutil**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>cosmicrays (Apr98)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.crutil</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>cosmicrays (Apr98)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>cosmicrays</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  cosmicrays -- detect and replace cosmic rays
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  cosmicrays input output
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images in which to detect cosmic rays.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output images in which the detected cosmic rays will be replaced
  by an average of neighboring pixels.  If the output image name differs
  from the input image name then a copy of the input image is made with
  the detected cosmic rays replaced.  If no output images are specified
  then the input images are modified in place.  In place modification of
  an input image also occurs when the output image name is the same as
  the input image name.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_crmasks">crmasks = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='crmasks' Line='crmasks = ""'>
  <DD>List of cosmic ray mask files to be created; one for each input image.  If no
  file names are given then no cosmic ray mask is created.  If an existing
  mask is specified the newly detected cosmic rays will be added.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_threshold">threshold = 25.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='threshold' Line='threshold = 25.'>
  <DD>Detection threshold above the mean of the surrounding pixels for cosmic
  rays.  The threshold will depend on the noise characteristics of the
  image and how weak the cosmic rays may be for detection.  A typical value
  is 5 or more times the sigma of the background.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fluxratio">fluxratio = 2.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fluxratio' Line='fluxratio = 2.'>
  <DD>The ratio (as a percent) of the mean neighboring pixel flux to the candidate
  cosmic ray pixel for rejection.  The value depends on the seeing and the
  characteristics of the cosmic rays.  Typical values are in the range
  2 to 10 percent.  This value may be reset interactively from a plot
  or defined by identifying selected objects as stars or cosmic rays.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_npasses">npasses = 5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='npasses' Line='npasses = 5'>
  <DD>Number of cosmic ray detection passes.  Since only the locally strongest
  pixel is considered a cosmic ray, multiple detection passes are needed to
  detect and replace cosmic ray events with multiple neighboring pixels.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_window">window = 5</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='window' Line='window = 5'>
  <DD>Size of cosmic ray detection window.  A square window of either 5 by 5 or
  7 by 7 is used to detect cosmic rays.  The smaller window allows detection
  in the presence of greater background gradients but is less sensitive at
  discriminating multiple event cosmic rays from stars.  It is also marginally
  faster.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Examine parameters interactively?  A plot of the mean flux within the
  detection window (x100) vs the flux ratio (x100) is plotted and the user may
  set the flux ratio threshold, delete and undelete specific events, and
  examine specific events.  This is useful for new data in which one is
  uncertain of an appropriate flux ratio threshold.  Once determined the
  task need not be used interactively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_train">train = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='train' Line='train = no'>
  <DD>Define the flux ratio threshold by using a set of objects identified
  as stars (or other astronomical objects) or cosmic rays?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_objects">objects = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='objects' Line='objects = ""'>
  <DD>Cursor list of coordinates of training objects.  If null (the null string "<TT></TT>")
  then the image display cursor will be read.  The user is responsible for first
  displaying the image.  Otherwise a file containing cursor coordinates
  may be given.  The format of the cursor file is "<TT>x y wcs key</TT>" where
  x and y are the pixel coordinates, wcs is an arbitrary number such as 1,
  and key may be <TT>'s'</TT> for star or <TT>'c'</TT> for cosmic ray.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_savefile">savefile = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='savefile' Line='savefile = ""'>
  <DD>File to save (by appending) the training object coordinates.  This is of
  use when the objects are identified using the image display cursor.  The
  saved file can then be input as the object cursor list for repeating the
  execution.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_plotfile">plotfile</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='plotfile' Line='plotfile'>
  <DD>If a plot file is specified then the graph of the flux ratio (x100) vs
  the mean flux (x100) is recorded as metacode.  This may be spooled or examined
  later.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_graphics">graphics = "<TT>stdgraph</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>Interactive graphic output device for interactive examination of the
  detection parameters.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cursor">cursor = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""'>
  <DD>Interactive graphics cursor input.  If null the graphics display cursor
  is used, otherwise a file containing cursor input may be specified.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_answer">answer</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='answer' Line='answer'>
  <DD>This parameter is used for interactive queries when processing a list of
  images.  The responses may be "<TT>no</TT>", "<TT>yes</TT>", "<TT>NO</TT>", or "<TT>YES</TT>".  The upper case
  responses permanently enable or disable the interactive review while
  the lower case reponses allow selective examination of certain input
  images.  <I>This parameter should not be specified on the command line.
  If it is then the value will be ignored and the task will act as if
  the answer "yes" is given for each image; i.e. it will enter the interactive
  phase without prompting.</I>
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_image_cursor_commands">IMAGE CURSOR COMMANDS</A></H2>
  <! BeginSection: 'IMAGE CURSOR COMMANDS'>
  <UL>
  <P>
  <PRE>
  ?	Help
  c	Identify the object as a cosmic ray
  s	Identify the object as a star
  g	Switch to the graphics plot
  q	Quit and continue with the cleaning
  </PRE>
  <P>
  GRAPHICS CURSOR COMMANDS
  <P>
  <PRE>
  ?	Help
  a	Toggle between showing all candidates and only the training points
  d	Mark candidate for replacement (applys to <TT>'+'</TT> points)
  e	Mark candidates in a region for replacement (applys to <TT>'+'</TT> points)
  q	Quit and return to image cursor or replace the selected pixels
  r	Redraw the graph
  s	Make a surface plot for the candidate nearest the cursor
  t	Set the flux ratio threshold at the y cursor position
  u	Mark candidate to not be replaced (applys to <TT>'x'</TT> points)
  v	Mark candidates in a region to not be replaced (applys to <TT>'x'</TT> points)
  w	Adjust the graph window (see <B>gtools</B>)
  &lt;space&gt;	Print the pixel coordinates
  </PRE>
  <P>
  There are no colon commands except those for the windowing options (type
  :\help or see <B>gtools</B>).
  </UL>
  <! EndSection:   'IMAGE CURSOR COMMANDS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
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
  masks, and with <B>crfix</B>.
  <P>
  This task may be applied to an image previously processed to detect
  additional cosmic rays.
  <P>
  The cosmic ray detection algorithm consists of the following steps.
  First a pixel must be the brightest pixel within the specified
  detection window (either 5x5 or 7x7).  The mean flux in the surrounding
  pixels with the second brightest pixel excluded (which may also be a
  cosmic ray event) is computed and the candidate pixel must exceed this
  mean by the amount specified by the parameter <I>threshold</I>.  A plane
  is fit to the border pixels of the window and the fitted background is
  subtracted.  The mean flux (now background subtracted) and the ratio of
  this mean to the cosmic ray candidate (the brightest pixel) are
  computed.  The mean flux (x100) and the ratio (x100) are recorded for
  interactive examination if desired.
  <P>
  Once the list of cosmic ray candidates has been created and a threshold for
  the flux ratio established (by the parameter <I>fluxratio</I>, by the
  "<TT>training</TT>" method, or by using the graphics cursor in the interactive plot)
  the pixels with ratios below the threshold are replaced in the output by
  the average of the four neighboring pixels (with the second strongest pixel
  in the detection window excluded if it is one of these pixels).  Additonal
  pixels may then be detected and replaced in further passes as specified by
  the parameter <I>npasses</I>.  Note that only pixels in the vicinity of
  replaced pixels need be considered in further passes.
  <P>
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
  <P>
  After the initial list of cosmic ray candidates has been created and before
  the final replacing cosmic rays there are two optional steps to allow
  examining the candidates and setting the flux ratio threshold dividing
  cosmic rays from real objects.  The first optional step is define the flux
  ratio boundary by reference to user specified classifications; that is
  "<TT>training</TT>".  To do this step the <I>train</I> parameter must be set to yes.
  The user classified objects are specified by a cursor input list.  This
  list can be an actual file or the image display cursor as defined by the
  <I>objects</I> parameter.  The <I>savefile</I> parameter is also used during
  the training to record the objects specified.  The parameter specifies a
  file to append the objects selected.  This is useful when the objects are
  defined by interactive image cursor and does not make much sense when using
  an input list.
  <P>
  If the <I>objects</I> parameter is specified as a null string then
  the image display cursor will be repeatedly read until a <TT>'q'</TT> is
  entered.  The user first displays the image and then when the task
  reads the display cursor the cursor shape will change.  The user
  points at objects and types <TT>'s'</TT> for a star (or other astronomical
  object) and <TT>'c'</TT> for a cosmic ray.  Note that this input is used
  to search for the matching object in the cosmic ray candidate list
  and so it is possible the selected object is not in the list though
  it is unlikely.  The selection will be quietly ignored in that case.
  To exit the interactive selection of training objects type <TT>'q'</TT>.
  <P>
  If <TT>'g'</TT> is typed a graph of all the candidates is drawn showing
  "<TT>flux</TT>" vs. "<TT>flux ratio</TT>" (see below for more).  Training objects will
  be shown with a box and the currently set flux ratio threshold will
  also be shown.  Exiting the plot will return to entering more training
  objects.  The plot will remain and additional objects will immediately
  be shown with a new box.  Thus, if one wants to see the training
  objects identified in the plot as one selects them from the image
  display first type a <TT>'g'</TT> to draw the initial plot.  Also by switching
  to the plot with <TT>'g'</TT> allows you to draw surface plots (with <TT>'s'</TT>) or
  get the pixel coordinates of a candidate (the space key) to be
  found in the display using the coordinate readout of the display.
  Note that the display interaction is simpler than might be desired
  because this task does not directly connect to the display.
  <P>
  The most likely use for training is with the interactive image display.
  However one may prepare an input list by other means, one example
  is with <B>rimcursor</B>, and then specify the file name.  The savefile
  may also be used a cursor input to repeat the cosmic ray operation
  (but be careful not to have the cursor input and save file be the
  same file!).
  <P>
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
  <P>
  After the training step the user will be queried to examine the candidates
  in the flux vs flux ratio plane if the <I>interactive</I> flag is set.
  Responses may be made for specific images or for all images by using
  lower or upper case answers respectively.  When the parameters are
  examined interactively the user may change the flux ratio threshold
  (<TT>'t'</TT> key).  Changes made are stored in the parameter file and, thus,
  learned for further images.  Pixels to be deleted are marked by crosses
  and pixels which are peaks of objects are marked by pluses.  The user
  may explicitly delete or undelete any point if desired but this is only
  for special cases near the threshold.  In the future keys for
  interactive display of the specific detections will be added.
  Currently a surface plot of any candidate may be displayed graphically
  in four 90 degree rotated views using the <TT>'s'</TT> key.  Note that the
  initial graph does not show all the points some of which are clearly
  cosmic rays because they have negative mean flux or flux ratio.  To
  view all data one must rewindow the graph with the <TT>'w'</TT> key or ":/"<TT>
  commands (see <B>gtools</B>).
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To replace cosmic rays in a set of images ccd* without training:
  <P>
  <PRE>
      cl&gt; cosmicrays ccd* new//ccd*
      ccd001: Examine parameters interactively? (yes):
      [A scatter plot graph is made.  One can adjust the threshold.]
      [Looking at a few points using the <TT>'s'</TT> key can be instructive.]
      [When done type <TT>'q'</TT>.]
      ccd002: Examine parameters interactively? (yes): NO
      [No further interactive examination is done.]
  </PRE>
  <P>
  After cleaning one typically displays the images and  possibly blinks them.
  A difference image or mask image may also be created.
  <P>
  2. To use the interactive training method for setting the flux ratio threshold:
  <P>
  <PRE>
      # First display the image.
      cl&gt; display ccd001 1
      z1 = 123.45 z2= 543.21
      cl&gt; cosmicrays ccd001 ccd001cr train+
      [After the cosmic ray candidates are found the image display
      [cursor will be activated.  Mark a cosmic ray with <TT>'c'</TT> and
      [a star with <TT>'s'</TT>.  Type <TT>'g'</TT> to get a plot showing the two
      [points with boxes.  Type <TT>'q'</TT> to go back to the image display.
      [As each new object is marked a box will appear in the plot and
      [the threshold may change.  To find the location of an object
      [seen in the plot use <TT>'g'</TT> to go to the graph, space key to find
      [the pixel coordinates, <TT>'q'</TT> to go back to the image display,
      [and the image display coordinate box to find the object.
      [When done with the training type <TT>'q'</TT>.
      ccd001: Examine parameters interactively? (yes): no
  </PRE>
  <P>
  3.  To create a mask image a bad pixel file must be specified.
  <P>
  <PRE>
      cl&gt; cosmicrays ccd001 ccd001 crmask=crccd001
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  crmedian, crnebula, crgrow, crfix, credit, gtools, imedit, rimcursor
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'IMAGE CURSOR COMMANDS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>