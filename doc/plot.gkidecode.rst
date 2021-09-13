.. _gkidecode:

gkidecode — Decode metacode on the standard output
==================================================

**Package: plot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  gkidecode -- decode one or more GKI metacode files
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  gkidecode input
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The input metacode, which can be read from a list of files or
  redirected from the standard input.
  </DD>
  </DL>
  <DL>
  <DT><B>generic = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='generic' Line='generic = no'>
  <DD>The remaining parameters are ignored when <B>generic</B> = yes.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>If <B>verbose</B> = yes, the elements of polylines, cell arrays, etc. will
  be printed.
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
  Task <B>gkidecode</B> is a debugging tool used to decode GKI metacode
  files.  The plotting instructions are decoded and printed in readable 
  form on the standard output.  The input metacode can be read from one
  or more files or redirected from the standard input.
  <P>
  If <B>verbose</B> = yes, elements of polyline and cell array calls are
  printed in addition to the default output.
  Coordinates can be printed in either GKI (0 - 32767) or NDC (0.0 - 1.0)
  units.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Decode the metacode instructions in file crtpict.mc in verbose mode.
  <P>
      cl&gt; gkidecode crtpict.mc verbose+
  <P>
  2. Print a shorter listing of the same file on the versatec.
  <P>
      cl&gt; gkidecode crtpict.mc | lprint dev=ver
  <P>
  3. Decode the third frame in metacode file "<TT>oned.mc</TT>".
  <P>
      cl&gt; gkiextract oned.mc 3 | gkidecode
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  stdgraph stdplot 
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
