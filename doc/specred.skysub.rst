.. _skysub:

skysub — Sky subtract extracted multispec spectra
=================================================

**Package: specred**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  skysub -- Sky subtract extracted multispec spectra
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  skysub input
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input multispec spectra to sky subtract.
  </DD>
  </DL>
  <DL>
  <DT><B>output = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = ""'>
  <DD>List of output sky subtracted spectra.  If no output is specified then
  the output replaces the input spectra.
  </DD>
  </DL>
  <DL>
  <DT><B>objaps = "<TT></TT>", objbeams = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='objaps' Line='objaps = "", objbeams = ""'>
  <DD>Object aperture and beam numbers.  An empty list selects all aperture
  or beam numbers.  Only the selected apertures are sky subtracted.
  Other apertures are left unmodified.  Note that it is valid to include
  the sky apertures in the object selection which results in residual
  sky spectra after subtraction by a mean sky.
  </DD>
  </DL>
  <DL>
  <DT><B>skyaps = "<TT></TT>", skybeams = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='skyaps' Line='skyaps = "", skybeams = ""'>
  <DD>Sky aperture and beam numbers.  An empty list selects all aperture or
  beam numbers.
  </DD>
  </DL>
  <DL>
  <DT><B>skyedit = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='skyedit' Line='skyedit = yes'>
  <DD>Edit the sky spectra?  If yes the sky spectra are graphed using the
  task <B>specplot</B> and the user may delete contaminated sky spectra with
  the <TT>'d'</TT> key and exit with <TT>'q'</TT>.
  </DD>
  </DL>
  <DL>
  <DT><B>combine = "<TT>average</TT>" (average|median|sum)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='combine' Line='combine = "average" (average|median|sum)'>
  <DD>Option for combining pixels at the same dispersion coordinate after any
  rejection operation.  The options are to compute the  "<TT>average</TT>", "<TT>median</TT>",
  or "<TT>sum</TT>" of the pixels.  The median uses the average of the two central
  values when the number of pixels is even.
  </DD>
  </DL>
  <DL>
  <DT><B>reject = "<TT>none</TT>" (none|minmax|avsigclip)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reject' Line='reject = "none" (none|minmax|avsigclip)'>
  <DD>Type of rejection operation performed on the pixels which overlap at each
  dispersion coordinate.  The algorithms are discussed in the
  DESCRIPTION section.  The rejection choices are:
  <P>
  <PRE>
        none - No rejection
      minmax - Reject the nlow and nhigh pixels
   avsigclip - Reject pixels using an averaged sigma clipping algorithm
  </PRE>
  <P>
  </DD>
  </DL>
  <DL>
  <DT><B>scale = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scale' Line='scale = no'>
  <DD>Scale the sky spectra by the mode?
  </DD>
  </DL>
  <DL>
  <DT><B>saveskys = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='saveskys' Line='saveskys = yes'>
  <DD>Save the sky spectra?  If no then the mean sky spectra will be deleted after
  sky subtraction is completed.  Otherwise a one dimensional image with
  the prefix "<TT>sky</TT>" and then the output name is created.
  </DD>
  </DL>
  <DL>
  <DT><B>logfile = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = ""'>
  <DD>Logfile for making a record of the sky subtraction operation.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task selects a subset of aperture spectra from a multispec
  format image, called sky spectra though they could be anything,
  and combines them into a master spectrum which is subtracted
  from another subset of spectra called the objects.  Options include
  saving the master sky spectrum and reviewing the selected sky spectra
  graphically and deleting some of them.
  <P>
  The sky apertures are selected using the aperture and beam numbers
  defined during extraction (see the <B>apextract</B> package).  In
  some applications the beam numbers are used to code object and sky
  apertures and selection by beam number is quite easy.  Otherwise one
  must list the aperture numbers explicitly.
  <P>
  The object apertures are also selected using an aperture and beam
  number list.  Spectra not selected to be objects are not modified
  by the sky subtraction.  Note that it is perfectly valid to include
  the sky spectra in the object list to produce residual sky spectra.
  <P>
  When interactively editing the sky spectra the task <B>specplot</B>
  is used.  To delete a spectrum type <TT>'d'</TT>.  To undelete the last deleted
  spectrum type <TT>'e'</TT>.  When finished type <TT>'e'</TT>.
  <P>
  The sky spectra are combined using one of combining and rejection options from
  the task <B>scombine</B> except for the option "<TT>none</TT>".
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  To median and subtract apertures 1,10,15,20 from all apertures:
  <P>
  <PRE>
      ms&gt; skysub obj010.ms out=skysub010.ms skyaps="1,10,15,20"
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  specplot, scombine
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
