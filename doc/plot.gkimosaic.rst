gkimosaic — Condense metacode frames to fit on one page
=======================================================

**Package: plot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>gkimosaic (Mar87)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>plot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>gkimosaic (Mar87)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>gkimosaic</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  gkimosaic -- condense metacode frames to fit on one page
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  gkimosaic input
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The metacode input, which can be redirected from STDIN or read from
  one or more binary metacode files.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = ""'>
  <DD>If <B>output</B> is specified, the mosaiced metacode is spooled to this
  file for later plotting.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_device">device = "<TT>stdgraph</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = "stdgraph"'>
  <DD>Output plotting device.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nx">nx = 2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nx' Line='nx = 2'>
  <DD>The number of plots to draw in the x direction.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ny">ny = 2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ny' Line='ny = 2'>
  <DD>The number of plots to draw in the y direction.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fill">fill = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fill' Line='fill = no'>
  <DD>The plots are reduced by equal factors in x and y when <B>fill</B> = no. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rotate">rotate = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rotate' Line='rotate = no'>
  <DD>Output the mosaiced plots rotated by 90 degrees.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>If plotting to <B>stdgraph</B>, interactively examine each page of plots.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cursor">cursor = "<TT>stdgcur</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = "stdgcur"'>
  <DD>Source of cursor input.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Task <B>gkimosaic</B> condenses the plots in a metacode file to fit
  on a single page.  The plots can be examined interactively after
  each pageful.  The number of plots in x and y can be specified.  This
  task is useful for browsing through a large metacode file, and for
  compactly plotting a large number of metacode frames.
  <P>
  When <B>fill</B> = no, the plots will be
  reduced by equal factors in x and y; the aspect ratio of the original 
  plot is preserved.  When <B>fill</B> = yes, the transformations in x and
  y are handled separately, meaning that the reduction factors will not
  be equal unless <B>nx</B> = <B>ny</B>.  
  <P>
  The mosaiced plots are drawn on the page rotated by 90 degrees
  when <B>rotate</B> = yes.  This means the x axis of the plots can be
  placed along either the page width or length.
  The plots can be output to a plotting <B>device</B>,
  or spooled in file <B>output</B> for later plotting.
  <P>
  If plotting to <B>stdgraph</B>, the plot can be interactively
  examined after each page of output by setting <B>interactive</B> = yes.
  The world coordinate system information of the individual plots has 
  been retained for cursor readback.
  Standard cursor mode keystroke commands are available as well as the
  <I>gkimosaic</I> specific commands listed below.  Colon commands :nx, :ny, 
  :fill and :rotate take effect on the next page of output.  Command :skip
  allows you to browse through a metacode file, skipping either forward or
  backward by N input plots.
  <PRE>
  <P>
  	q				quit
  	return				quit
  	spacebar			continue
  	?				print help information
  <P>
  	:nx N				change value of nx to N
  	:ny N				change value of ny to N
  	:fill yes, :fill+, :fill	sets fill = yes
  	:fill no, :fill-		sets fill = no
  	:rotate yes, :rotate+, :rotate	sets rotate = yes
  	:rotate no, :rotate-		sets rotate = no
  	:skip +/-N			skip forward/backward N plots
  <P>
  </PRE>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Plot every frame in the metacode file "<TT>oned.plots</TT>".  There will be 4 plots
  to the page originally, but this can be overridden interactively.
  <P>
      cl&gt; gkimosaic oned.plots
  <P>
  2. Extract every third plot from the metacode file "<TT>oned.plots</TT>" with task
  <I>gkiextract</I> and plot them four to a page.
  <P>
      cl&gt; gkiextract oned.plots 1-99x3 | gkimosaic
  <P>
  3. Plot all frames in every metacode file beginning with "<TT>mcode.</TT>" and
  condense them so 16 fit on a page.  The metacode is being spooled;
  it will be plotted, perhaps, when the computer isn't so busy.  Interactive
  mode is automatically disabled when not plotting to a graphics terminal.
  <P>
      cl&gt; gkimosaic mcode.* nx=4 ny=4 output=plt.spool
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  Setting <B>device</B> to "<TT>stdvdm</TT>" does not work.  To produce an output file
  of mosaiced metacode, use the <I>output</I> parameter or the "<TT>&gt;G</TT>" graphics 
  stream redirection feature of the cl.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  gkidir, gkiextract
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>