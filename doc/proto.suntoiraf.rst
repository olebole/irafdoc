suntoiraf — Convert Sun rasters into IRAF images
================================================

**Package: proto**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>suntoiraf (Apr92)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>proto</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>suntoiraf (Apr92)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>suntoiraf</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  suntoiraf -- convert Sun raster files into IRAF images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  suntoiraf input
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_names">names</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='names' Line='names'>
  <DD>List of raster files to be converted.  The output image names will be
  the same as the individual input file names with a "<TT>.imh</TT>" appended
  (assuming that you are using the Old Image Format).  Rasterfiles with
  an extension of `.ras', will have the extension omitted.  The images will
  appear in the same directory as the raster files, typically the <B>Unix</B>
  login directory when the task is used within an imtool R_DISPOSE string.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_apply_lut">apply_lut = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apply_lut' Line='apply_lut = yes'>
  <DD>Apply the lookup table translation to each pixel?  If <B>apply_lut</B> =
  no, the pixel values will be taken directly from the raster file.  If
  <B>apply_lut</B> = yes, an NTSC weighted translation from the rasterfile's
  color lookup table will be applied to each pixel to convert to grayscale.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_delete">delete = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='delete' Line='delete = no'>
  <DD>Delete the rasterfile after making the image?  This is useful for making
  automated (Unix or IRAF) scripts for producing photographic or other hardcopy.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print informative information while the transformation is occurring?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_listonly">listonly = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='listonly' Line='listonly = no'>
  <DD>List the rasterfile header information instead?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_yflip">yflip = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='yflip' Line='yflip = yes'>
  <DD>Flip the output image top to bottom?  Rasterfiles are stored in reverse
  vertical order from IRAF images.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Suntoiraf</B> will convert Sun raster files into IRAF images.  This is
  useful, for example, to make <B>solitaire</B> photographic prints or
  other hardcopy from an <B>imtool</B> window (see IMTOOL HINTS, below).
  <P>
  For general use, <B>suntoiraf</B> will convert non-run-length-encoded
  Sun rasterfiles into IRAF images.  The output image will have the same
  name as the input rasterfile, but with a `.imh' (or other IRAF image
  extension) appended.  If the rasterfile has an extension of `.ras', this
  extension will be omitted from the image name.
  <P>
  If <B>apply_lut</B> = no, the (typically 8 bit) pixel values will be
  copied directly to the output with no interpretation.  If <B>apply_lut</B>
  = yes, the NTSC equalization weighting will be applied to the RGB lookup
  table to convert the color rasterfile to a grayscale image.  The weights
  are 0.299, 0.587, and 0.114 for the red, green, and blue LUT entries,
  respectively.
  <P>
  Various options are available to tailor the operation of the task to
  your (or your script's) precise liking.  If <B>delete</B> = yes, the
  input raster file will be removed from the disk after the image
  conversion.  This is useful in script applications.  If <B>verbose</B> =
  yes, a running commentary will be presented, otherwise the operation of
  the task is silent except for error messages.  If <B>listonly</B> = yes,
  the task will report information about each input rasterfile, rather
  than converting it.  If <B>yflip</B> = yes, the storage order of the
  lines of the output image will be inverted from the input rasterfile.
  Since the display convention is inverted for rasterfiles relative to
  IRAF images, this will result in an upright output image.  On the other
  hand, if <B>yflip</B> = no, the storage order will be preserved at the
  expense of the output orientation appearing inverted.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_imtool_hints">IMTOOL HINTS</A></H2>
  <! BeginSection: 'IMTOOL HINTS'>
  <UL>
  One possible first step in making a hardcopy is to create the raster files
  from the imtool window.  The recommended way to do this is to select "<TT>Imcopy</TT>"
  from the imtool frame menu.  If the menu is popped up by positioning the
  cursor on the right hand side of the window frame (and away from the edge
  of the screen), the menu won't overlay the window, possibly contaminating
  the hardcopy.  The resulting raster file will save not only the pixels from
  the imtool buffer but also the lookup table information.
  <P>
  Another way to generate an imtool screendump is to use the &lt;F7&gt; function
  key, but this requires care because of the possibility of catching cursor
  fallout in the solitaire.  If you do use the &lt;F7&gt; function key, position the
  cursor to minimize its visual impact.  The cursor will appear in the
  hardcopy (solitaire) unless it happens to blink out at the moment that
  the hardcopy is made.
  <P>
  A possibly confusing choice is the "<TT>Save</TT>" option in the imtool setup menu.
  This is inappropriate because no lookup table information is preserved.
  <P>
  Only the portion of the frame buffer that is displayed in the window
  will be snapped - what you see is what you get.
  <P>
  If you have to adjust the contrast and brightness of the image very
  much by using the right mouse button, you may want to redisplay the
  image using a different Z1 and Z2.  This will preserve the grayscale
  resolution in cases in which the "<TT>effective</TT>" Z1 and Z2 are much
  different than the "<TT>actual</TT>" Z1 and Z2.
  <P>
  In the setup menu try:
  <P>
  <PRE>
      Show colorbar:	No
      Background color:	black
  </PRE>
  <P>
  The choice of the background color may have an effect on any graphics
  in the frame.
  <P>
  If you use the <B>imttodmd</B> shell script available at NOAO/Tucson,
  the pixel files for the images will be created in the IRAF directory
  `tmp$', which is typically the UNIX directory `/tmp/'.  If you have
  trouble with this directory filling up, the pixel files may be placed
  into another directory by setting the UNIX environment variable `tmp'
  to the desired pathname:
  <P>
  <PRE>
      % setenv tmp '/scr1/v13/pixels/'
  </PRE>
  <P>
  *before* starting up IMTOOL (IN THE PARENT SHELL OF THE IMTOOL).
  Note that if this is set when IRAF is entered, all IRAF temporary
  files will end up in this directory.
  </UL>
  <! EndSection:   'IMTOOL HINTS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  These are rather specific to NOAO/Tucson, but may suggest ways that the
  task may be useful to you.
  <P>
  To configure imtool for one button solitaire operation:
  <P>
  The Unix shell script, "/ursa/iraf/extern/nlocal/lib/imttodmd"<TT> (on
  Ursa and its kin) can be used to make imtool solitaire prints.  The
  script may move to /usr/local/bin in the future and would thus be
  available like any other unix command.  Imttodmd is meant to be
  called directly by the imtool.  For example, place these lines in
  your `.login' file:
  <P>
  <PRE>
      setenv R_RASTERFILE 'snap.%d'
      setenv R_DISPOSE '/ursa/iraf/extern/nlocal/lib/imttodmd %s'
  </PRE>
  <P>
  More recent versions of imtool also allow setting these strings from
  the setup panel.
  <P>
  The parent shell of the imtool must have these variables defined in
  its environment prior to starting imtool.  If you aren't sure what
  this means, the simplest thing to do is to edit these lines into
  your <B>.login</B>, log off of the workstation <B>completely</B>, and
  log back into Unix, Sunview, and IRAF.
  <P>
  Pressing &lt;F7&gt; will send snaps directly to the solitaire queue, leaving
  no intermediate files.  Only the windowed portion of the frame buffer
  will be snapped.  The necessary files will twinkle in and out of
  existence in the current working directory of the imtool, typically
  your Unix login directory.  Your windows will be frozen until the
  solitaire is safely on its way, at which time the screen will beep.
  This should take on the order of half a minute for a 512 square
  imtool on a lightly loaded system.  If faster response is needed,
  the script may be run in the background:
  <P>
  <PRE>
      setenv R_DISPOSE    '/ursa/iraf/extern/nlocal/lib/imttodmd %s &amp;'
  </PRE>
  <P>
  Care should be taken in this case to avoid having too many
  (<B>too many is typically more than one</B>) background job running
  at once.
  <P>
  <P>
  To make one-button snap files and solitaires:
  <P>
  The <B>imttodmd</B> script has various options for leaving the
  intermediate files around.  To leave the snap images in your
  directory and also make solitaires (i.e., if you are highly
  suspicious by nature) set the variable:
  <P>
  <PRE>
      setenv R_DISPOSE    '/ursa/iraf/extern/nlocal/lib/imttodmd -image %s'
  </PRE>
  <P>
  <P>
  To only make the images, with no solitaire output:
  <P>
  <PRE>
      setenv R_DISPOSE    '/ursa/iraf/extern/nlocal/lib/imttodmd -nocrt %s'
  </PRE>
  <P>
  This will allow you to run a single CRTPICT job after collecting all
  the snap files.
  <P>
  <P>
  To make solitaires from an imtool window, the old way:
  <P>
  Enter this from the UNIX shell, <B>before starting suntools</B>:
  <P>
  <PRE>
      % setenv R_RASTERFILE "frame.%d"
  </PRE>
  <P>
  Start suntools, login to iraf and load the noao, tv and local
  packages.  Display an image and press the &lt;F7&gt; function key to
  create a raster file named "<TT>frame.N</TT>", where N is an index number
  generated by imtool.  This raster file will be appear in your
  <B>UNIX</B> login directory.
  <P>
  Dump the raster files to the solitaire queue:
  <P>
  <PRE>
      lo&gt; suntoiraf frame.*
      lo&gt; crtpict frame.*.i.imh ztrans=min_max z1=5 z2=260
  	(The z1 &amp; z2 values were empirically determined.)
  </PRE>
  <P>
  *** Don't forget to clean up! ***
  <P>
  <PRE>
      lo&gt; imdelete frame.*.i.imh
      lo&gt; delete frame.*
  </PRE>
  <P>
  The solitaires should be ready the next day in the basket by the
  main computer lab.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  irafil, binfil, and the UNIX man page for imtool
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'IMTOOL HINTS' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>