.. _stdgraph:

stdgraph — Plot metacode on the standard graphics device
========================================================

**Package: plot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  stdgraph -- draws a plot on the terminal
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  stdgraph input
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The input metacode, may be a list of files or redirected STDIN.
  </DD>
  </DL>
  <DL>
  <DT><B>device = "<TT>stdgraph</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = "stdgraph"'>
  <DD>The terminal type.
  </DD>
  </DL>
  <DL>
  <DT><B>generic = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='generic' Line='generic = no'>
  <DD>The remaining parameters are ignored if <B>generic</B> = yes.
  </DD>
  </DL>
  <DL>
  <DT><B>debug = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='debug' Line='debug = no'>
  <DD>When <B>debug</B> = yes, the decoded plotting instructions are printed
  during processing.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>If <B>verbose</B> = yes, elements of polylines and cell array calls are 
  printed in debug mode.
  </DD>
  </DL>
  <DL>
  <DT><B>gkiunits = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gkiunits' Line='gkiunits = no'>
  <DD>In debug mode, coordinates can be printed in GKI rather than NDC units.
  </DD>
  </DL>
  <DL>
  <DT><B>txquality = "<TT>normal</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='txquality' Line='txquality = "normal"'>
  <DD>The character drawing quality.
  </DD>
  </DL>
  <DL>
  <DT><B>xres = 0, yres= 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xres' Line='xres = 0, yres= 0'>
  <DD>The number of resolution elements in x and y
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Task <I>stdgraph</I> translates GKI metacode and draws a plot on a
  graphics terminal.  Input to
  <I>stdgraph</I> is GKI metacode, which can be read from one or more 
  metacode files or redirected from the standard input.  
  <P>
  Parameters 
  <B>txquality</B>, <B>xres</B>, and <B>yres</B> are used to override the
  values for text quality, and x and y resolution already in the metacode.
  Values for <B>txquality</B> are chosen from normal, low, medium or high.
  High quality characters are software generated, and can be of any size.
  <P>
  If <B>debug</B> is set to yes, the plotting instructions are printed in
  readable form as the metacode is processed.  In debug mode, GKI 
  instructions can be printed in verbose mode, where the elements of
  polylines and cell arrays are printed in addition to the default output.
  Coordinates can be printed in either GKI (0 - 32767) or NDC (0.0 - 1.0)
  units.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Extract the fourth frame from metacode file "<TT>plots.mc</TT>" and plot it.
  <P>
      cl&gt; gkiextract plots.mc 4 | stdgraph
  <P>
  2. Process file "<TT>one.mc</TT>" in debug mode.
  <P>
      cl&gt; stdgraph oned.mc debug+
  <P>
  3. Plot file "<TT>oned.mc</TT>" with high quality text generation.
  <P>
      cl&gt; stdgraph oned.mc txquality=high
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  gkiextract,  stdplot
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
