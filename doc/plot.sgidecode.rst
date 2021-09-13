.. _sgidecode:

sgidecode — Decode an SGI format metacode file
==============================================

**Package: plot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  sgidecode -- decode simple graphics interface (SGI) metacode files
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  sgidecode input
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The input SGI metacode files.
  </DD>
  </DL>
  <DL>
  <DT><B>generic = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='generic' Line='generic = no'>
  <DD>Ignore remaining parameters?
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print metacode in a verbose format?
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
  Task <I>sgidecode</I> is a debugging tool used to decode SGI metacode
  files.  The plotting instructions are decoded and printed in readable
  form on the standard output.  The input metacode can be read from one
  or more files or redirected from the standard input.
  <P>
  Coordinates are printed in NDC units (0-1) by default.  When <B>gkiunits</B>
  = yes, coordinates are printed in gki units (0-32767).  Parameter
  <B>verbose</B> is currently not implemented.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Decode the metacode in file "<TT>home$vdm.sgi</TT>".
  <P>
      cl&gt; sgidecode home$vdm.sgi
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  gkidecode sgikern
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
