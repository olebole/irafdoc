.. _help:

help — Print online documentation
=================================

**Package: system**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  help -- print online documentation for the named modules or packages
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  help [template]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>template</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='template' Line='template'>
  <DD>A string listing the modules or packages for which help is desired.
  Each list element may be a simple name or a pattern matching template.
  Abbreviations are permitted.  If <I>template</I> is omitted a long format
  menu will be printed for the current package, listing each task (or
  subpackage) and describing briefly what it is.
  </DD>
  </DL>
  <DL>
  <DT><B>file_template = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='file_template' Line='file_template = no'>
  <DD>If this switch is set the template is interpreted as a filename matching
  template, and all help blocks found in the named files are output.  The help
  database is not searched, hence manual pages can be printed or documents
  may be formatted without entering the files into a help database.
  In other words, "<TT>help file.hlp fi+</TT>" makes it possible to use <I>help</I> as
  a conventional text formatter.
  </DD>
  </DL>
  <DL>
  <DT><B>all = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='all' Line='all = no'>
  <DD>Print help for all help modules matching <I>template</I>, rather than only the
  first one found.
  </DD>
  </DL>
  <DL>
  <DT><B>parameter = "<TT>all</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='parameter' Line='parameter = "all"'>
  <DD>If the value of this parameter is not "<TT>all</TT>", only the help text
  for the given parameter will be printed.
  </DD>
  </DL>
  <DL>
  <DT><B>section = "<TT>all</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='section' Line='section = "all"'>
  <DD>If the value of this parameter is not "<TT>all</TT>", only the help text for the
  given section (e.g. "<TT>usage</TT>", "<TT>description</TT>", "<TT>examples</TT>") will be printed.
  </DD>
  </DL>
  <DL>
  <DT><B>option = help</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='option' Line='option = help'>
  <DD>The option parameter specifies the type of help desired, chosen from
  the following:
  <DL>
  <DT><B>help</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='help' Line='help'>
  <DD>Print the full help block for the named module.
  </DD>
  </DL>
  <DL>
  <DT><B>source</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='source' Line='source'>
  <DD>Print the source code for the module (which often contains additional
  detailed comments).
  </DD>
  </DL>
  <DL>
  <DT><B>sysdoc</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='sysdoc' Line='sysdoc'>
  <DD>Print the technical system documentation for the named module.
  </DD>
  </DL>
  <DL>
  <DT><B>directory</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='directory' Line='directory'>
  <DD>Print a directory of all help blocks available for the named package.
  </DD>
  </DL>
  <DL>
  <DT><B>alldoc</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='alldoc' Line='alldoc'>
  <DD>Print all help blocks in the file containing the help block for
  the named procedure (i.e., both the user and system documentation).
  </DD>
  </DL>
  <DL>
  <DT><B>files</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='files' Line='files'>
  <DD>Print the names of all help files associated with the named modules or
  packages.
  </DD>
  </DL>
  <DL>
  <DT><B>summary</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='summary' Line='summary'>
  <DD>Print only the titles and sizes of help blocks in referenced help files.
  The contents of the blocks are skipped.  Titles are printed for <I>all</I>
  help blocks found in the file containing the help block for the named module.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>page = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='page' Line='page = yes'>
  <DD>Pause after every page of output text.  Turning this off for large documents
  speeds up output considerably.
  </DD>
  </DL>
  <DL>
  <DT><B>nlpp = 59</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nlpp' Line='nlpp = 59'>
  <DD>The number of lines per page if output is redirected, e.g., to <I>lprint</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>lmargin = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lmargin' Line='lmargin = 1'>
  <DD>Left margin on output.
  </DD>
  </DL>
  <DL>
  <DT><B>rmargin = 72</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rmargin' Line='rmargin = 72'>
  <DD>Right margin on output.
  </DD>
  </DL>
  <DL>
  <DT><B>search = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='search' Line='search = no'>
  <DD>If enabled the 
  <A HREF="#l_template">template</A>
  is interpreted as a search string and the task
  is started with the search panel open with the results of the search.  The
  <A HREF="#l_file_template">file_template</A>
  parameter is ignored with search turned on.
  </DD>
  </DL>
  <DL>
  <DT><B>home = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='home' Line='home = ""'>
  <DD>The home page for the task.  If not set and no 
  <A HREF="#l_template">template</A>
  is specified
  the task will start with the online help in the main window, otherwise it
  may be set to a filename to be displayed when the task starts.  This file
  may contain a text help block which will be formatted before display,  or
  it may be a valid HTML file.  See below for a description of the format of
  a homepage file which provides links to tasks.
  </DD>
  </DL>
  <DL>
  <DT><B>printer = "<TT>printer</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='printer' Line='printer = "printer"'>
  <DD>Default hardcopy printer name. If the <I>value</I> of the parameter is the
  reserved string "<TT>printer</TT>", the actual device is the value of the CL
  environment variable <I>printer</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>showtype = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='showtype' Line='showtype = no'>
  <DD>Add task-type suffix in package menus?
  </DD>
  </DL>
  <DL>
  <DT><B>quickref = "<TT>uparm$quick.ref</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='quickref' Line='quickref = "uparm$quick.ref"'>
  <DD>Name of the quick-reference file used for searching.  This file is created
  the first time the task is run in GUI mode or whenever it doesn't exist, 
  or when any help database file has been updated.
  </DD>
  </DL>
  <DL>
  <DT><B>uifname = "<TT>lib$scr/help.gui</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='uifname' Line='uifname = "lib$scr/help.gui"'>
  <DD>The user interface file.   This file is what defines the look and behavior
  of all the graphical user interface elements.   Experts may create variants
  of this file.
  </DD>
  </DL>
  <DL>
  <DT><B>helpdb = "<TT>helpdb</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='helpdb' Line='helpdb = "helpdb"'>
  <DD>The filename of the help database to be searched.  If the <I>value</I> of the
  parameter is the reserved string "<TT>helpdb</TT>", the actual filename is the value
  of the CL environment variable <I>helpdb</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>device = "<TT>terminal</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = "terminal"'>
  <DD>Output device if the standard output is not redirected.  Allowable values
  include:
  <DL>
  <DT><B>terminal</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='terminal' Line='terminal'>
  <DD>If the <I>value</I> of
  the parameter is the reserved string "<TT>terminal</TT>",  the actual device name is
  the value of the CL environment variable <I>terminal</I>.  
  </DD>
  </DL>
  <DL>
  <DT><B>text</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='text' Line='text'>
  <DD>Output the formatted help page as plain text.
  </DD>
  </DL>
  <DL>
  <DT><B>gui</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='gui' Line='gui'>
  <DD>Invoke the GUI for browsing the help system.  This option will only work if
  the <I>stdgraph</I> environment variable is set the <I>xgterm</I>, and the
  user is running IRAF from an <I>XGterm</I> window.
  </DD>
  </DL>
  <DL>
  <DT><B>html</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='html' Line='html'>
  <DD>Output the formatted help page as HTML text.
  </DD>
  </DL>
  <DL>
  <DT><B>ps (or postscript)</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='ps' Line='ps (or postscript)'>
  <DD>Output the formatted help page as postscript.
  </DD>
  </DL>
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Basic usage</H3>
  <! BeginSection: 'BASIC USAGE'>
  <UL>
  Despite the complex appearing hidden parameters, <B>help</B> is easy to use
  for simple tasks.  <B>Help</B> is most commonly used to get help on the current
  package, and to get help on a program named in a CL menu.  To get help on
  the current package one need only type <B>help</B> without any arguments.
  For example, if the current package is <B>plot</B>, the command and its output
  might appear as follows:
  <P>
  <PRE>
  	pl&gt; help
  		contour - Make a contour plot of an image
  		  graph - Graph one or more image sections or lists
  		   pcol - Plot a column of an image
  		  pcols - Plot the average of a range of image columns
  		   prow - Plot a line (row) of an image
  		  prows - Plot the average of a range of image lines
  		surface - Make a surface plot of an image
  	pl&gt;
  </PRE>
  <P>
  To get help on a module one supplies the module name as an argument,
  <P>
  	pl&gt; help graph
  <P>
  and the manual page for the <B>plot.graph</B> program will be printed on the
  terminal.  To get a hardcopy of the manual page on the printer, the output
  may be redirected to the line printer, as follows:
  <P>
  	pl&gt; help graph | lprint
  </UL>
  <! EndSection:   'BASIC USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The function of the <B>help</B> program is to perform a depth first search
  of the help database <I>helpdb</I>, printing help for all packages and modules
  matching the template.  By default the standard IRAF help database is searched,
  but any other help database may be searched if desired.  A help database is
  precompiled with the <B>mkhelpdb</B> program to speed up runtime searches for
  help modules.  The standard IRAF help database contains the documentation and
  source for all CL programs and system and math library procedures installed
  in IRAF.
  <P>
  A help template is a string type parameter to the CL.  The form of a template
  is a list of patterns delimited by commas, i.e.,
  <P>
  	"<TT>pattern1, pattern2, ..., patternN</TT>"
  <P>
  The form of a pattern is
  <P>
  	package_pattern.module_pattern
  <P>
  If the "<TT>.</TT>" is omitted <I>module_pattern</I> is assumed.  The standard pattern
  matching meta-characters, i.e., "<TT>*?[]</TT>", are permitted in patterns.
  Simple patterns are assumed to be abbreviations.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Gui operation</H3>
  <! BeginSection: 'GUI OPERATION'>
  <UL>
  <P>
  The GUI component of the task is a front-end to the IRAF 
  <A HREF="system.help"><B>help</B></A>
  task which provides on-the-fly conversion of help documents to HTML for
  presentation in the GUI or formatted PostScript for hardcopy.  
  The GUI is started by setting the 
  <A HREF="#l_device"><I>device</I></A>
  parameter to the special value <I>gui</I>, it is only available when using
  an XGterm window to start IRAF and assuming the <I>stdgraph</I> environment
  variable is set to xgterm.
  <P>
  Help pages may be loaded on the command line, through use of a
  file browser, or by navigating the help databases using a familiar CL
  package menu scheme.   It also features a search capability similar to the 
  <A HREF="system.references"><B>references</B></A>
  task and a complete history mechanism. 
  <P>
  When invoked with no command line arguments the task starts as a browser
  and the user is presented with a GUI that has the toplevel CL package menu
  in the upper navigation window.  The main display window below will contain
  any help page specified in the 
  <A HREF="#l_template">template</A>
  parameter or loaded on
  the command line by specifying the 
  <A HREF="#l_template">template</A>
  and 
  <A HREF="#l_file_template">file_template</A>
  parameters. If the 
  <A HREF="#l_search">search</A>
  parameter is enabled the 
  <A HREF="#l_template">template</A>
  is taken to be a search phrase and the database is searched for tasks
  matching the keyword and the GUI will appear with the search panel mapped
  so the user can select the task help to
  view.  When no 
  <A HREF="#l_template">template</A>
  is given the main display window will start with the page specified by the 
  <A HREF="#l_home">home</A>
  parameter, this can be a user-defined HTML file giving links to specific tasks
  (see below for details) or if 
  <A HREF="#l_home">home</A>
  is empty the display will contain the online help for the task.
  <P>
  The first time the task is run, or whenever the help database is updated,
  a quick reference file (specified by the task 
  <A HREF="#l_quickref">quickref </A>
  parameter) and package menu file will be created in the user's <I>uparm</I>
  directory to speed up help searching and subsequent startups of the task.
  <P>
  </UL>
  <! EndSection:   'GUI OPERATION'>
  <H3>Navigating the help system</H3>
  <! BeginSection: 'NAVIGATING THE HELP SYSTEM'>
  <UL>
  When run as a GUI browser <I>HELP</I> works very much like any WWW browser.
  The top panel is a list widget that will always contain a CL package listing,
  at startup this will be the toplevel <I>"Home"</I> package menu one would see
  when first logging into the CL containing the core system packages, NOAO
  package, and any site-specific external package, or in the case of starting
  with a specific task it will be the parent package for the task.  Additionally,
  system documents for the 
  <A HREF="os"><B>os</B></A>
  HSI routines and the 
  <A HREF="sys.imfort"><B>imfort</B></A>
  and
  <A HREF="math"><B>math</B></A>
  interfaces will be available in the <I>Home</I> package although
  these are programmatic interfaces and not tasks which can be executed.
  <P>
  New packages or task help pages are loaded by selecting an item from the 
  package menu list using the left mouse button.  If the requested item is a 
  package, the menu listing will change as though the package were loaded in
  the CL, and the help display panel will contain a listing of the package
  tasks with a one-line description for each task such as would be seen with 
  a <I>"help &lt;package&gt;"</I> command using the standard task.  New items may then
  be selected using either the menu list or links in the display panel.  If the
  item is a task, the help page for the task will appear in the display panel.
  In either case new pages may be selected from the menu listing.  
  <P>
  Specific help documents may also be requested by entering the task/package
  name in the <B>Topic</B> text widget above the menu list.  As when selecting
  from the package menu list, items selected this way will cause the menu
  list to change to the package menu for the parent package if the item is a
  task (displaying the help page in the display panel) or the package menu
  if the item is a package (displaying the one-liner package listing in the
  display panel).
  <P>
  Using the <B>Back</B> button will revert to the previous page in the history
  list which will either be the previously loaded package or help page.
  Similarly, selecting the <B>Forward</B> button will move the next page further
  down in the history list, either button will become insensitive when the 
  end of the list on either end is reached.  Selecting the <B>Up</B> button will
  cause the browser to immediately jump up the previous package, skipping 
  over any help pages that were loaded in between.  The <B>Home</B> button will
  cause the default homepage (either the user-defined page if specified by the
  task <I>home</I> parameter or the online help) to be displayed.  Browsing
  in this way can also be done using the navigation menu created by hitting
  the right mouse button while in the main display panel.
  <P>
  Users can also jump to specific pages in the history list using the
  <B>History</B> button on the main menubar.   The right column of the menu
  will indicate whether the item is a task, package, internal link or a text
  file.  The history list is truncated at about 40 entries in the menu but
  the user may work back incrementally by selecting the last item of the 
  menu, after which the History button will display the previous 40 entries.
  The history list may be cleared except for the current page by selecting
  the <I>Clear History</I> menu item.
  <P>
  </UL>
  <! EndSection:   'NAVIGATING THE HELP SYSTEM'>
  <H3>Browsing a help document</H3>
  <! BeginSection: 'BROWSING A HELP DOCUMENT'>
  <UL>
  Once a help page is loaded the middle menubar above the display panel
  will change to activate widgets based on the position within the history
  list and options available for a particular page.  The left-most group
  of buttons are the standard navigation buttons described above.
  The middle group of buttons contains the <B>Sections</B> and
  <B>Parameters</B> buttons which are used to browse within a help document.
  The <I>Sections</I> button is a menu listing all of the sections found
  within a help page, allowing the user to jump to a specific section
  rather than scrolling through the entire document. The <I>Sections</I>
  menu is also available using the middle mouse button from the
  main display area.  The <I>Parameters</I> button is similarly a menu
  listing of all task parameter help sections found within the document.
  Both or either of these buttons will become insensitive when no section
  or parameter information is found in the document.
  <P>
  The right-most group of buttons represent the various help options available
  for each page.  The default is to get the task help, however help pages
  may have an associated <B>source</B> file or <B>sysdoc</B> (e.g. if the task is
  a CL script there may be a pointer to the script source itself, or a package
  may have a general overview document listed as the system document).  Once
  a help page is loaded these buttons will change become sensitive if that option
  is available, simply select the button to view the option.  Selecting the
  <B>Files</B> button will bring up a panel listing all the files associated
  with a particular help topic.  When a help topic is selected and an option is
  defined but the file does not exist, the options button will display a yellow
  diamond icon even if the button is insensitive, a green icon indicates the
  currently selected option.  This feature may be disabled by selecting the
  "<TT>Show missing files</TT>" item from the main menubar <B>Options</B> menu.
  <P>
  </UL>
  <! EndSection:   'BROWSING A HELP DOCUMENT'>
  <H3>Searching</H3>
  <! BeginSection: 'SEARCHING'>
  <UL>
  Searching the help database is done by selecting the <B>Search</B> button
  from the main menubar to bring up the search panel.  Users may then enter 
  one or more keywords into the <B>Topic</B> field at the bottom of the panel
  and initiate the search with either a carriage return or hitting the
  <I>Search</I> button just beside it.  The panel will then show a list of all
  tasks and packages which match the search phrase along with a one-line
  description of the task.  Help pages may be displayed by selecting either the
  task or package link with the left mouse button, in both case the package
  menu list on the main help window will be updated to list the package
  contents allowing other tasks from that package to be selected in the normal
  way.
  <P>
  By default the exact phrase entered in the topic window will be used for the
  search.  This can be relaxed by toggling the  "<TT>Require exact match</TT>" button
  at the top of the panel.  For example,  to search for all tasks matching
  <I>either</I> the keyword "<TT>flat</TT>" or "<TT>field</TT>" turn off the exact match
  toggle and the search will return not only tasks matching "<TT>flat field</TT>" but 
  also any task description containing only one of the words such as the
  VELVECT task which plots velocity <I>field</I>s.
  <P>
  Within a help document itself one can search for a string by selecting
  the <B>Find</B> button from the main menubar to bring up a panel used to
  enter the search string.  When the text is entered the main display 
  window will reposition itself and highlight the text found within the
  document.  Searches can be repeated and will wrap around the document
  automatically, searches can be done either forward or backward through
  the text and may be case insensitive.
  <P>
  </UL>
  <! EndSection:   'SEARCHING'>
  <H3>User_defined home pages</H3>
  <! BeginSection: 'USER_DEFINED HOME PAGES'>
  <UL>
  By default the <I>help</I> GUI will start with the online help page displayed
  in the main help window.  The user can change this by setting the task
  <B>home</B> parameter to be a path to any valid file.  This file may be plain
  text, a help document in LROFF format which will be converted to HTML for
  display, or a native HTML document.
  <P>
  HTML files may contain URLs of the form
  <PRE>
  	<B>&lt;a href=</B><I>[package.]task</I><B>&gt;</B><I>url_text</I><B>&lt;/a&gt;
  </PRE>
  <P>
  where </B><I>url_text</I> is the text to appear in the window and the URL itself
  consists of an optional package and task name delimited by a period.  For
  example, to create a link to the 
  <A HREF="onedspec.splot"><B>splot</B></A>
  task in a document one would use the URL
  <PRE>
  	<B>&lt;a href=onedspec.splot&gt;splot&lt;/a&gt;</B>
  </PRE>
  <P>
  In this way users can create a homepage which serves as a <I>"bookmark"</I>
  file or index of shortcuts to the most commonly accessed help pages.
  <P>
  </UL>
  <! EndSection:   'USER_DEFINED HOME PAGES'>
  <H3>Loading files</H3>
  <! BeginSection: 'LOADING FILES'>
  <UL>
  Text files may be loaded on the command line when starting the task by
  specifying the filename and setting the
  <A HREF="#l_file_template">file_template</A>
  task parameter.  The named file
  will be searched for a <I>.help</I> LROFF directing indicating it contains
  a help block that will be converted to HTML for display.  If no help
  block is found the file will be displayed as-is, meaning existing
  HTML documents can be loaded and will be formatted correctly.
  <P>
  Once the task is running users may load a file by selecting the <B>Open
  File...</B> menu item from the main menubar <B>File</B> menu or the
  right-mouse-button menu from within the main display area.  This will
  open a file browser allowing users to change directories by using the
  navigation buttons at the top of the panel, or selecting items from the
  leftmost directory listing.  Selecting a file on the rightmost list will
  cause it to be loaded and automatically formatted if it contains a help
  block.  The file list may be filtered to select only those files matching
  a particular template by changing the <B>Filter</B> box at the top of
  the panel.  Filenames or directories may be entered directly using the
  <B>Selection</B> box at the bottom of the panel.
  <P>
  </UL>
  <! EndSection:   'LOADING FILES'>
  <H3>Saving files</H3>
  <! BeginSection: 'SAVING FILES'>
  <UL>
  Once a file has been loaded in the browser it may be saved to disk as 
  either <I>source</I> (i.e. the original LROFF file if that was converted
  for the display, or whatever file is currently displayed regardless of
  format), <I>text</I> to save formatted plain text such as that produced
  by the standard <B>help</B> task, <I>HTML</I> to save the converted HTML
  used in the display, or <I>PostScript</I> to save formatted PostScript of
  the document such as that sent to the printer using the <B>Print</B> 
  button.  Not all options will be available depending on the format of the
  input text, unavailable options will be insensitive in the GUI.
  <P>
  The <B>Save</B> panel is opened by selecting the <B>Save As...</B> menu
  item from the  main menubar <B>File</B> menu or the right-mouse-button
  menu from within the main display area.   The file browser operates the
  same as when loading images, the only difference is that file selection 
  simply defines the filename to be used and does not cause the save to
  occur automatically.  Users can overwrite existing files by selecting the
  <I>Options</I> toggle at the bottom of the panel.
  <P>
  </UL>
  <! EndSection:   'SAVING FILES'>
  <H3>Hardcopy output and saving disk files.</H3>
  <! BeginSection: 'HARDCOPY OUTPUT AND SAVING DISK FILES.'>
  <UL>
  Help pages may be output to any configured IRAF printer by selecting the
  main menubar <B>Print</B> button to bring up the print panel.  Task help pages
  will be converted to formatted PostScript and may be sent to either a
  printer or saved to disk depending on the selection made in the printer 
  panel.  If the printer name is set to the special value <I>"printer"</I> then
  the device named by the CL <I>printer</I> environment variable will be used.
  When saving to disk files the default action is to save to a filename whose
  name is the task name plus a "<TT>.ps</TT>" extension.  Either of these are changeable
  within the GUI as is the default page size to be used when generating the
  PostScript.
  <P>
  The main menubar <B>File</B> button can also be used to bring up the file
  browser in order to save the current document to disk.  Help pages may be
  saved as either the origin LROFF source for the file, formatted text as you
  would get from the standard help task, HTML as is displayed in the GUI, or
  formatted PostScript.  The choice of formats is dictated by the type of file
  being displayed (e.g. you cannot save PostScript of a program source).
  <P>
  </UL>
  <! EndSection:   'HARDCOPY OUTPUT AND SAVING DISK FILES.'>
  <H3>Lroff directive extensions for html</H3>
  <! BeginSection: 'LROFF DIRECTIVE EXTENSIONS FOR HTML'>
  <UL>
  To better support HTML links within documents and to other help pages two
  new directives have been added to the LROFF text formatter.  These are
  <B>.hr</B> to specify a link (an HTML <I>HREF</I> directive) and <B>.hn</B>
  to specify a name (an HTML <I>NAME</I> directive).  The syntax for these are
  as follows:
  <PRE>
  <P>
  	<B>.hn</B><I> &lt;name&gt;</I>
  	<B>.hr</B><I> &lt;link&gt; &lt;text&gt; </I>
  </PRE>
  <P>
  where <I>&lt;name&gt;</I> is the destination name of an internal link, <I>&lt;link&gt;</I>
  is the URL of the link to be created, and <I>&lt;text&gt;</I> is the text to be
  displayed in the HTML.  The URL syntax is either a <TT>'#'</TT> character followed
  by a destination name, a simple <I>task</I> name or <I>package</I> name,
  or a <I>package.task</I> pair giving a more precise task.  For internal links
  the current document is repositioned so the name is at the top of the display,
  for task help links new help pages will be loaded in the browser.  
  <P>
  These directives are ignored when converting the LROFF to either formatted
  plain text or PostScript.
  <P>
  
  </UL>
  <! EndSection:   'LROFF DIRECTIVE EXTENSIONS FOR HTML'>
  <H3>Gui examples</H3>
  <! BeginSection: 'GUI EXAMPLES'>
  <UL>
  1) Start <I>help</I> as a GUI browser:
  <PRE>
  <P>
  	cl&gt; help dev=gui
  </PRE>
  <P>
  2) Begin by searching for the phrase 'gauss', tasks and packages may be
  selected from the search panel which will appear when the task starts:
  <PRE>
  <P>
  	cl&gt; help gauss dev=gui search+
  </PRE>
  <P>
  3) Load an LROFF help page in the browser at startup
  <PRE>
  <P>
  	cl&gt; help mytask.hlp dev=gui file+
  </PRE>
  <P>
  </UL>
  <! EndSection:   'GUI EXAMPLES'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Print the help text for the program <I>delete</I> in the package
  <I>system</I> (output will be directed to the terminal):
  <P>
  <PRE>
  	cl&gt; help system.delete
  or
  	cl&gt; help delete
  or
  	cl&gt; help del
  </PRE>
  <P>
  2. Print the help text on the line printer:
  <PRE>
  <P>
  	cl&gt; help delete | lprint
  </PRE>
  <P>
  3. Print help for the current package:
  <PRE>
  <P>
  	cl&gt; help
  </PRE>
  <P>
  4. Print the usage section of all modules in the package <B>images</B>:
  <PRE>
  <P>
  	cl&gt; help images.* section=usage
  </PRE>
  <P>
  5. Print a directory of all help blocks in the packages <B>clpackage</B>
  and <B>clio</B> (and any others whose names begin with the string "<TT>cl</TT>"):
  <PRE>
  <P>
  	cl&gt; help cl* op=dir
  </PRE>
  <P>
  6. Print a directory of each package in the database (useful for getting an
  overview of the contents of a help database):
  <PRE>
  <P>
  	cl&gt; help * op=dir
  </PRE>
  <P>
  7. Print the source for all of the string utilities in the system library
  package <B>fmtio</B>:
  <PRE>
  <P>
  	cl&gt; help fmtio.str* op=source
  </PRE>
  <P>
  8. Find all tasks that delete something:
  <PRE>
  <P>
  	cl&gt; help * | match delete
  </PRE>
  <P>
  9. Print the manual pages for the <I>help</I> and <I>lprint</I> tasks on the
  default printer device:
  <PRE>
  <P>
  	cl&gt; help help,lprint | lpr
  </PRE>
  <P>
  10. Capture the manual page for task <I>hedit</I> in a text file, in a form
  suitable for printing on any device.
  <PRE>
  <P>
  	cl&gt; help hedit dev=text &gt; hedit.txt
  </PRE>
  <P>
  11. Print the manual page for task <I>hedit</I> as a Postscript file. 
  <PRE>
  <P>
  	cl&gt; help hedit dev=ps | lprint
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  On some systems, typing the next command keystroke before the end-of-page
  prompt is printed may result in the character being echoed (messing up the
  output) and then ignored when raw mode is enabled for the prompt.
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  <A HREF="system.references">references</A>
  ,
  <A HREF="system.phelp">phelp</A>
  ,
  <A HREF="system.mkhelpdb">mkhelpdb</A>
  ,
  <A HREF="system.hdbexamine">hdbexamine</A>
  ,
  <A HREF="system.mkmanpage">mkmanpage</A>
  ,
  <A HREF="system.lroff">lroff</A>
  , the online task help documents.
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'BASIC USAGE' 'DESCRIPTION' 'GUI OPERATION' 'NAVIGATING THE HELP SYSTEM' 'BROWSING A HELP DOCUMENT' 'SEARCHING' 'USER_DEFINED HOME PAGES' 'LOADING FILES' 'SAVING FILES' 'HARDCOPY OUTPUT AND SAVING DISK FILES.' 'LROFF DIRECTIVE EXTENSIONS FOR HTML' 'GUI EXAMPLES' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
