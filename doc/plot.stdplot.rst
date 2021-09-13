.. _stdplot:

stdplot — Plot metacode on the standard plotter device
======================================================

**Package: plot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  stdplot -- draw metacode on the standard plotter device
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  stdplot input
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of input metacode files.
  </DD>
  </DL>
  <DL>
  <DT><B>device = "<TT>stdplot</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = "stdplot"'>
  <DD>The type of plotting device.
  </DD>
  </DL>
  <DL>
  <DT><B>generic = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='generic' Line='generic = no'>
  <DD>The remaining parameters are ignored when <B>generic</B> = yes.
  </DD>
  </DL>
  <DL>
  <DT><B>debug = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='debug' Line='debug = no'>
  <DD>If <B>debug</B> = yes, the graphics instructions are decoded and printed
  during processing.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>If <B>verbose</B> = yes, the elements of polylines, cell arrays, etc. will
  be printed in debug mode.
  </DD>
  </DL>
  <DL>
  <DT><B>gkiunits = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gkiunits' Line='gkiunits = no'>
  <DD>By default, coordinates are printed in NDC rather than GKI units.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Task <I>stdplot</I> translates metacode and draws it on a plotting
  device.
  Input is GKI metacode, which can be read from one or more binary
  files or redirected from the standard input.
  <P>
  If <B>debug</B> is set to yes, the plotting instructions are printed in
  readable form during processing.
  If <B>verbose</B> = yes, elements of polyline and cell array calls are
  printed in addition to the default debug output.
  Coordinates can be printed in either GKI (0 - 32767) or NDC (0.0 - 1.0)
  units.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Extract the fourth frame from metacode file "<TT>oned.mc</TT>" and plot it.
  <P>
      cl&gt; gkiextract oned.mc 4 | stdplot
  <P>
  2. Plot metacode frame "<TT>contour.demo</TT>" in debug mode, so the plotting
  instructions can be read as they are processed.
  <P>
      cl&gt; stdplot contour.demo debug+
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  gkiextract stdgraph
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
