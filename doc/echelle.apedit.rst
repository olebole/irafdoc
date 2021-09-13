apedit — Edit apertures interactively
=====================================

**Package: echelle**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>apedit (Sep96)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.twodspec.apextract</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>apedit (Sep96)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>apedit</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  apedit -- Edit apertures
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  apedit input
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images for which apertures are to be edited.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_apertures">apertures = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apertures' Line='apertures = ""'>
  <DD>Apertures to recenter, resize, trace, and extract.  This only applies
  to apertures read from the input or reference database.  Any new
  apertures defined with the automatic finding algorithm or interactively
  are always selected.  The syntax is a list comma separated ranges
  where a range can be a single aperture number, a hyphen separated
  range of aperture numbers, or a range with a step specified by "<TT>x&lt;step&gt;</TT>";
  for example, "<TT>1,3-5,9-12x2</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_references">references = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='references' Line='references = ""'>
  <DD>List of reference images to be used to define apertures for the input
  images.  When a reference image is given it supersedes apertures
  previously defined for the input image. The list may be null, "<TT></TT>", or
  any number of images less than or equal to the list of input images.
  If the reference image list is shorter than the input image list the
  last reference image is used for the remaining input images.
  There are three special words which may be used in place of an image
  name.  The word "<TT>last</TT>" refers to the last set of apertures written to
  the database.  The word "<TT>OLD</TT>" requires that an entry exist
  and the word "<TT>NEW</TT>" requires that the entry not exist for each input image.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = no'>
  <DD>Run this task interactively?  If the task is not run interactively then
  all user queries are suppressed and interactive aperture editing is
  disabled.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_find">find = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='find' Line='find = no'>
  <DD>Find the spectra and define apertures automatically?  In order for
  spectra to be found automatically there must be no apertures for the
  input image or reference image defined in the database.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_recenter">recenter = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='recenter' Line='recenter = no'>
  <DD>Recenter the apertures?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_resize">resize = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='resize' Line='resize = no'>
  <DD>Resize the apertures?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_edit">edit = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='edit' Line='edit = yes'>
  <DD>Edit the apertures?  The <I>interactive</I> parameter must also be yes.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_line">line = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='line' Line='line = INDEF'>
  <DD>The dispersion line (line or column perpendicular to the dispersion axis) to
  be graphed.  A value of INDEF uses the middle of the image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nsum">nsum = 10</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nsum' Line='nsum = 10'>
  <DD>Number of dispersion lines to be summed or medianed.  The lines are taken
  around the specified dispersion line.  A positive nsum selects a sum of
  lines and a negative selects a median of lines.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_width">width = 5.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='width' Line='width = 5.'>
  <DD>Width of spectrum profiles.  This parameter is used for the profile
  centering algorithm in this and other tasks.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_radius">radius = 5.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='radius' Line='radius = 5.'>
  <DD>The profile centering error radius for the centering algorithm.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_threshold">threshold = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='threshold' Line='threshold = 0.'>
  <DD>Centering threshold for the centering algorithm.  The range of pixel intensities
  near the initial centering position must exceed this threshold.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_additional_parameters">ADDITIONAL PARAMETERS</A></H2>
  <! BeginSection: 'ADDITIONAL PARAMETERS'>
  <UL>
  I/O parameters and the default dispersion axis are taken from the
  package parameters, the default aperture parameters are taken from the
  task <B>apdefault</B>.  Parameters for the various functions of finding,
  recentering, and resizing are taken from the parameters for the
  appropriate task.
  <P>
  When this operation is performed from the task <B>apall</B> all parameters
  except the package parameters are included in that task.
  </UL>
  <! EndSection:   'ADDITIONAL PARAMETERS'>
  <H2><A NAME="s_cursor_keys">CURSOR KEYS</A></H2>
  <! BeginSection: 'CURSOR KEYS'>
  <UL>
  When editing the apertures interactively the following cursor keys are
  available.
  <P>
  <PRE>
  ?    Print help
  a    Toggle the ALL flag
  b an Set background fitting parameters
  c an Center aperture(s)
  d an Delete aperture(s)
  e an Extract spectra (see APSUM)
  f    Find apertures up to the requested number (see APFIND)
  g an Recenter aperture(s) (see APRECENTER)
  i  n Set aperture ID
  j  n Set aperture beam number
  l ac Set lower limit of current aperture at cursor position
  m    Define and center a new aperture on the profile near the cursor
  n    Define a new aperture centered at the cursor
  o  n Enter desired aperture number for cursor selected aperture and
       remaining apertures are reordered using apidtable and maxsep
       parameters (see APFIND for ordering algorithm)
  q    Quit
  r    Redraw the graph
  s an Shift the center(s) of the current aperture to the cursor
       position
  t ac Trace aperture positions (see APTRACE)
  u ac Set upper limit of current aperture at cursor position
  w    Window the graph using the window cursor keys
  y an Set aperture limits to intercept the data at the cursor y
       position
  z an Resize aperture(s) (see APRESIZE)
  +  c Select the next aperture (in ID) to be the current aperture
  -  c Select the previous aperture (in ID) to be the current aperture
  I    Interrupt task immediately.  Database information is not saved.
  </PRE>
  <P>
  The letter a following the key indicates if all apertures are affected when
  the ALL flag is set.  The letter c indicates that the key affects the
  current aperture while the letter n indicates that the key affects the
  aperture whose center is nearest the cursor.
  </UL>
  <! EndSection:   'CURSOR KEYS'>
  <H2><A NAME="s_colon_commands">COLON COMMANDS</A></H2>
  <! BeginSection: 'COLON COMMANDS'>
  <UL>
  <P>
  <PRE>
  :show [file]	   Print a list of the apertures (default STDOUT)
  :parameters [file] Print current parameter values (default STDOUT)
  :read [name]       Read from database (default current image)
  :write [name]      Write to database (default current image)
  </PRE>
  <P>
  The remaining colon commands are task parameters and print the current
  value if no value is given or reset the current value to that specified.
  Use :parameters to see current parameter values.
  <P>
  <PRE>
  :apertures      :apidtable      :avglimits      :b_function
  :b_grow         :b_high_reject  :b_low_reject   :b_naverage
  :b_niterate     :b_order        :b_sample       :background
  :bkg            :center         :clean          :database
  :extras         :gain           :image          :line
  :llimit         :logfile        :lower          :lsigma
  :maxsep         :minsep         :npeaks         :nsubaps
  :nsum           :order          :parameters     :peak
  :plotfile       :r_grow         :radius         :read
  :readnoise      :saturation     :shift          :show
  :skybox         :t_function     :t_grow         :t_high_reject
  :t_low_reject   :t_naverage     :t_niterate     :t_nsum
  :t_order        :t_sample       :t_step         :t_width
  :threshold      :title          :ulimit         :upper
  :usigma         :weights        :width          :write
  :ylevel		:t_nlost
  </PRE>
  </UL>
  <! EndSection:   'COLON COMMANDS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  For each image in the input image list, apertures are defined and edited
  interactively.  The aperture editor is invoked when the parameters
  <I>interactive</I> and <I>edit</I> are both yes.  When this is the case
  the task will query whether to edit each image.  The responses are
  "<TT>yes</TT>", "<TT>no</TT>", "<TT>YES</TT>", and "<TT>NO</TT>", where the upper case responses suppress
  queries for all following images.
  <P>
  When the aperture editor is entered a graph of the image lines or
  columns specified by the parameters <I>line</I> and <I>nsum</I> is
  drawn.  In the <B>apextract</B> package a dispersion line is either a
  line or column in the image at one point along the dispersion axis.
  The dispersion axis may be defined in the image header under the
  keyword DISPAXIS or by the package parameter <I>dispaxis</I>.  The
  parameter <B>nsum</B> determines how many dispersion lines surrounding
  the specified dispersion line are summed or medianed.  This improves the
  signal in the profiles of weaker spectra.  Once the graph is drawn an
  interactive cursor loop is entered.  The set of cursor keys and colon
  commands is given above and may be printed when the task is running using
  the <TT>'?'</TT> key.  The CURSOR MODE keys and graph formatting options are also
  available (see <B>cursor</B> and <B>gtools</B>).
  <P>
  A status line, usually at the bottom of the graphics terminal,
  indicates the current aperture and shows the ALL flag, <TT>'a'</TT> key, if set.  The
  concept of the current aperture is used by several of the aperture
  editing commands.  Other commands operate on the aperture whose center
  is nearest the cursor.  It is important to know which commands operate
  on the current aperture and which operate on the nearest aperture to
  the cursor.
  <P>
  The cursor keys and colon commands are used to define new apertures,
  delete existing apertures, modify the aperture number, beam number,
  title, center, and limits, set background fitting parameters, trace the
  positions of the spectra in the apertures, and extract aperture
  spectra.  When creating new apertures default parameters are supplied
  in two ways; if no apertures are defined then the default parameters
  are taken from the task <B>apdefault</B> while if there is a current
  aperture then a copy of its parameters are made.
  <P>
  The keys for creating a new aperture are <TT>'m'</TT> and <TT>'n'</TT> and <TT>'f'</TT>.  The key
  <TT>'m'</TT> marks a new aperture and centers the aperture on the profile
  nearest the cursor.  The centering algorithm is described under the
  help topic <B>center1d</B> and the parameters controlling the centering are
  <I>width</I>, <I>radius</I>, and <I>threshold</I>.  The key <TT>'n'</TT> defines a
  new aperture at the position of the cursor without centering.  This is
  used if there is no spectrum profile such as when defining sky apertures
  or when defining apertures in extended profiles.  The <TT>'f'</TT> key finds new
  apertures using the algorithm described in the task <B>apfind</B>.  The
  number of apertures found in this way is limited by the parameter
  <B>nfind</B> and the number includes any previously defined
  apertures.  The new aperture number, beam number, and title are assigned using
  the aperture assignment algorithm described in <B>apfind</B>.
  <P>
  The aperture number for the aperture <I>nearest</I> the cursor is changed
  with the <TT>'j'</TT> key and the beam number is changed with the <TT>'k'</TT> key.  The
  user is prompted for a new aperture number or beam number.  The
  aperture title may be set or changed with the :title colon command.
  <P>
  The <TT>'o'</TT> key may be used to reorder or correct the aperture
  identifications and beam numbers.  This is useful if the aperture
  numbers become disordered due to deletions and additions or if the
  first spectrum is missing when using the automatic identification
  algorithm.  An aperture number is requested for the aperture pointed to
  by the cursor.  The remaining apertures are reordered relative to this
  aperture number.  There is a aperture number, beam number, and title
  assignment algorithm which uses information about the maximum
  separation between consecutive apertures, the direction of increasing
  aperture numbers, and an optional aperture identification table.  See
  <B>apfind</B> for a description of the algorithm.
  <P>
  After defining a new aperture it becomes the current aperture.  The
  current aperture is indicated on the status line and the <TT>'.'</TT>, <TT>'+'</TT>, and
  <TT>'-'</TT> keys are used to select a new current aperture.
  <P>
  Apertures are deleted with <TT>'d'</TT> key.  The aperture <I>nearest</I> the
  cursor is deleted.
  <P>
  The aperture center may be changed with the <TT>'c'</TT>, <TT>'s'</TT>, and <TT>'g'</TT> keys and the
  "<TT>:center value</TT>" colon command.  The <TT>'c'</TT> key applies the centering algorithm
  to the aperture <I>nearest</I> the colon.  The <TT>'s'</TT> key shifts the center
  of the <I>current</I> aperture to the position of the cursor.  The <TT>'g'</TT>
  applies the <B>aprecenter</B> algorithm.  The :center command sets the
  center of the <I>current</I> aperture to the value specified.  Except
  for the last option these commands may be applied to all apertures
  if the ALL flag is set.
  <P>
  The aperture limits are defined relative to the aperture center.  The
  limits may be changed with the <TT>'l'</TT>, <TT>'u'</TT>, <TT>'y'</TT>, and <TT>'z'</TT> keys and with the
  "<TT>:lower value</TT>" and "<TT>:upper value</TT>" commands.  The <TT>'l'</TT> and <TT>'u'</TT> keys set
  the lower and upper limits of the <I>current</I> aperture at the position
  of the cursor.  The colon commands allow setting the limits explicitly.
  The <TT>'y'</TT> key defines both limits for the <I>nearest</I> aperture as
  points at which the y cursor position intercepts the data profile.
  This requires that the aperture include a spectrum profile and that
  the y cursor value lie below the peak of the profile.  The <TT>'z'</TT>
  key applies the <B>apresize</B> algorithm.  Except for the colon
  commands these commands may be applied to all apertures if the ALL
  flag is set.
  <P>
  The key <TT>'b'</TT> modifies the background fitting parameters for the aperture
  <I>nearest</I> the cursor.  The default background parameters are
  specified by the task <B>apdefault</B>.  Note that even though
  background parameters are defined, background subtraction is not
  performed during extraction unless specified.
  When the <TT>'b'</TT> key is used the <B>icfit</B> graphical interface is entered
  showing the background regions and function fit for the current image
  line.  Note that the background regions are specified relative to
  the aperture center and follows changes in the aperture position.
  <P>
  The two types of
  extraction which may be specified are to average all points within
  a set of background regions or fit a function to the points in
  the background regions.  In the first case only the background sample
  parameter is used.  In the latter case the other parameters are
  also used in conjunction with the <B>icfit</B> function fitting commands.
  See <B>apbackground</B> for more on the background parameters.
  <P>
  Each aperture may have different background
  fitting parameters but newly defined apertures inherit the background
  fitting parameters of the last current aperture.  This will usually be
  satisfactory since the background regions are defined relative to the
  aperture center rather than in absolute coordinates.  If the ALL flag
  is set then all apertures will be given the same background
  parameters.
  <P>
  The algorithms used in the tasks <B>apfind, aprecenter, apresize, aptrace</B>,
  and <B>apsum</B> are available from the editor with the keys <TT>'f'</TT>, <TT>'g'</TT>, <TT>'z'</TT>,
  <TT>'t'</TT>, and <TT>'e'</TT>
  respectively.  Excluding finding, if the ALL flag is not set then the
  nearest aperture
  to the cursor is used.  This allows selective recentering, resizing,
  tracing and extracting.
  If the ALL flag is set then all apertures are traced or extracted.
  When extracting the output, rootname and profile name are queried.
  <P>
  Some general purpose keys window the graph <TT>'w'</TT> using the <B>gtools</B>
  commands, redraw the graph <TT>'r'</TT>, and quit <TT>'q'</TT>.
  <P>
  The final cursor key is the <TT>'a'</TT> key.  The cursor keys which modify the
  apertures were defined as operating on either the aperture nearest the
  cursor or the current aperture.  The <TT>'a'</TT> key allows these keys to
  affect all the apertures simultaneously.  The <TT>'a'</TT> key sets a flag which
  is shown on the status line when it is set.  When set, the operation on
  one aperture is duplicated on the remaining apertures.  The operations
  which apply to all apertures are set background <TT>'b'</TT>, center <TT>'c'</TT>, delete
  <TT>'d'</TT>, extract <TT>'e'</TT>, recenter <TT>'g'</TT>, set lower limit <TT>'l'</TT>, shift <TT>'s'</TT>, trace
  <TT>'t'</TT>, set upper limit <TT>'u'</TT>, set limits at the y cursor <TT>'y'</TT>, and resize
  <TT>'z'</TT>.  The <TT>'b'</TT>, <TT>'l'</TT>, <TT>'s'</TT>, and <TT>'u'</TT> keys first set the background,
  aperture limits, or shift for the appropriate aperture and then are
  applied to the other apertures relative to their centers.
  <P>
  All the parameters used in any of the operations may be examined or
  changed through colon commands.  The :parameters command lists all
  parameter values and :show lists the apertures.  The :read and :write
  are used to force an update or save the current apertures and to read
  apertures for the current image or from some other image.  The commands
  all have optional arguments.  For the commands which show information
  the argument specifies a file to which the information is to be
  written.  The default is the standard output.  The database read and
  write and the change image commands take an image name.  If an image
  name is not given for the read and write commands the
  current image name is used.  The change image command default is to
  print the current image name.  The remaining commands take a value.  If
  a value is not given then the current value is printed.
  <P>
  The aperture editor may be selected from nearly every task using the
  <B>edit</B> parameter.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  The aperture editor is a very flexible and interactive tool
  for which it is impossible illustrate all likely uses.  The following
  give some simple examples.
  <P>
  1.  To define and edit apertures for image "<TT>n1.001</TT>":
  <P>
  	cl&gt; apedit n1.001
  <P>
  2.  To define apertures for one image and then apply them to several other
  images:
  <P>
  <PRE>
  	cl&gt; apedit n1.* ref=n1.001
  	Edit apertures for n1.001? (yes)
  	Edit apertures for n1.002? (yes) NO
  </PRE>
  <P>
  Answer "<TT>yes</TT>" to the first query for editing n1.001.  To
  the next query (for n1.002) respond with "<TT>NO</TT>".  The remaining
  images then will not be edited interactively.  Note that after
  defining the apertures for n1.001 they are recorded in the database
  and subsequent images will be able to use them as reference apertures.
  <P>
  3.  Using the "<TT>:image name</TT>" and "<TT>:read image</TT>" colon commands and the
  <TT>'f'</TT>, <TT>'g'</TT>, <TT>'z'</TT>, <TT>'t'</TT> and <TT>'e'</TT> keys the user can perform all the functions
  available in the package without ever leaving the editor.  The <TT>'a'</TT> key
  to set the ALL flag is very useful when dealing with many spectra in a
  single image.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_APEDIT">APEDIT V2.11</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='APEDIT' Line='APEDIT V2.11'>
  <DD>The "<TT>apertures</TT>" parameter can be used to select apertures for resizing,
  recentering, tracing, and extraction.  This parameter name was previously
  used for selecting apertures in the recentering algorithm.  The new
  parameter name for this is now "<TT>aprecenter</TT>".
  <P>
  The aperture ID table information may now be contained in the
  image header under the keywords SLFIBnnn.
  </DD>
  </DL>
  SEE ALSO
  <PRE>
  apdefault, apfind, aprecenter, apresize, aptrace, apsum, apall
  center1d, cursor, gtools, icfit
  </PRE>
  </UL>
  <! EndSection:    'REVISIONS'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'ADDITIONAL PARAMETERS' 'CURSOR KEYS' 'COLON COMMANDS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS'  >
  
  </BODY>
  </HTML>