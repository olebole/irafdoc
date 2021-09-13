gtpar — Pset to specify graph parameters for 'gtedit' task.
===========================================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>gtpar (May92)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>gtpar (May92)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>gtpar</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  pltpar -- Parameters describing plot attributes.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  pltpar
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Parameters in the 'gtpar' pset specify the attributes of plots drawn with the
  'gtedit' task.
  <P>
  Note that this is a pset, not an executable task.  Invoking the pset by name
  runs 'eparam', enabling the parameters to be interactively edited. 
  Parameters can also be modified on the
  CL command line by specifying the pset name and parameter name,
  for example, "<TT>gtpar.box = no</TT>").
  The pset name will also appear as one of
  the task parameters in the 'gtedit' task;
  to change values in the pset,
  position the cursor to the 'gtpar' pset name and type "<TT>:e</TT>" to invoke 'eparam'.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_">(wx1 = 0) [real]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(wx1 = 0) [real]'>
  <DD>Left world X-coordinate (if autoscaling is not used).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(wx2 = 0.) [real]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(wx2 = 0.) [real]'>
  <DD>Right world X-coordinate (if autoscaling is not used).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(wy1 = 0.) [real]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(wy1 = 0.) [real]'>
  <DD>Lower world Y-coordinate (if no autoscaling is used).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(wy2 = 0.) [real]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(wy2 = 0.) [real]'>
  <DD>Upper world Y-coord (if not autoscaling).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(marker = box) [string, allowed values:  point | box | plus | </A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(marker = box) [string, allowed values:  point | box | plus | '>
  <DD>cross | circle | diamond | hline | vline | hebar | vebar]
  <P>
  The name of the style of marker plotted at each point if 'pointmode=yes'.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(szmarker = 0.005) [real]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(szmarker = 0.005) [real]'>
  <DD>The size of the markers if 'pointmode = yes'.  If this parameter is greater 
  than 0, its value represents the marker size in world coordinates (WC).  If it 
  is less than zero, the absolute value will be used, representing size in 
  normalized device coordinates (NDC).  If it is set to exactly zero, and the
  input is from a list file,
  then the third column in the input data is used as the marker size.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(logx = no) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(logx = no) [boolean]'>
  <DD>Scale the X axis logarithmically?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(logy = no) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(logy = no) [boolean]'>
  <DD>Scale the Y axis logarithmically?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(box = yes) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(box = yes) [boolean]'>
  <DD>Draw the box containing the axes and labels around periphery of the 
  window?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(ticklabels = yes) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(ticklabels = yes) [boolean]'>
  <DD>Label major tick marks?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(grid = no) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(grid = no) [boolean]'>
  <DD>Draw grid lines on plot?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(xlabel) [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(xlabel) [string]'>
  <DD>X-axis label.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(ylabel) [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(ylabel) [string]'>
  <DD>Y-axis label.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(title = imtitle)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(title = imtitle)'>
  <DD>The plot title consists of a standard system-supplied string containing
  the user's name, date, etc.  If the 'title' parameter contains the string
  "<TT>imtitle</TT>" (the default), then the plot title will contain a second line
  made up from the input file or table name.  Otherwise, the title will
  contain the string value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(vx1 = 0.) [real, min = 0, max = 1]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(vx1 = 0.) [real, min = 0, max = 1]'>
  <DD>Left limit of device viewport.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(vx2 = 0.) [real, min = 0, max = 1]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(vx2 = 0.) [real, min = 0, max = 1]'>
  <DD>Right limit of device viewport.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(vy1 = 0.) [real, min = 0, max = 1]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(vy1 = 0.) [real, min = 0, max = 1]'>
  <DD>Bottom limit of device viewport.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(vy2 = 0.) [real], min = 0, max = 1]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(vy2 = 0.) [real], min = 0, max = 1]'>
  <DD>Upper limit of device viewport.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(majrx = 5) [integer]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(majrx = 5) [integer]'>
  <DD>Number of major divisions along the X grid.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(minrx = 5) [integer]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(minrx = 5) [integer]'>
  <DD>Number of minor divisions along the X grid.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(majry = 5) [integer]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(majry = 5) [integer]'>
  <DD>Number of major divisions along the Y grid.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(minry = 5) [integer]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(minry = 5) [integer]'>
  <DD>Number of minor divisions along the Y grid.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(round = no) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(round = no) [boolean]'>
  <DD>Round axes to nice values?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(fill = yes) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(fill = yes) [boolean]'>
  <DD>Fill the viewport rather than enforcing unity aspect ratio?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  sgraph
  <P>
  Type "<TT>help tables opt=sys</TT>" for a higher-level description of the 'tables' 
  package.
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>