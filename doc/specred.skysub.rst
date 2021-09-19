.. _skysub:

skysub: Sky subtract extracted multispec spectra
================================================

**Package: specred**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  skysub -- Sky subtract extracted multispec spectra
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  skysub input
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>List of input multispec spectra to sky subtract.
  </dd>
  </dl>
  <dl>
  <dt><b>output = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output = ""' -->
  <dd>List of output sky subtracted spectra.  If no output is specified then
  the output replaces the input spectra.
  </dd>
  </dl>
  <dl>
  <dt><b>objaps = <tt>""</tt>, objbeams = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='objaps' Line='objaps = "", objbeams = ""' -->
  <dd>Object aperture and beam numbers.  An empty list selects all aperture
  or beam numbers.  Only the selected apertures are sky subtracted.
  Other apertures are left unmodified.  Note that it is valid to include
  the sky apertures in the object selection which results in residual
  sky spectra after subtraction by a mean sky.
  </dd>
  </dl>
  <dl>
  <dt><b>skyaps = <tt>""</tt>, skybeams = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='skyaps' Line='skyaps = "", skybeams = ""' -->
  <dd>Sky aperture and beam numbers.  An empty list selects all aperture or
  beam numbers.
  </dd>
  </dl>
  <dl>
  <dt><b>skyedit = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='skyedit' Line='skyedit = yes' -->
  <dd>Edit the sky spectra?  If yes the sky spectra are graphed using the
  task <b>specplot</b> and the user may delete contaminated sky spectra with
  the <tt>'d'</tt> key and exit with <tt>'q'</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>combine = <tt>"average"</tt> (average|median|sum)</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='combine' Line='combine = "average" (average|median|sum)' -->
  <dd>Option for combining pixels at the same dispersion coordinate after any
  rejection operation.  The options are to compute the  <tt>"average"</tt>, <tt>"median"</tt>,
  or <tt>"sum"</tt> of the pixels.  The median uses the average of the two central
  values when the number of pixels is even.
  </dd>
  </dl>
  <dl>
  <dt><b>reject = <tt>"none"</tt> (none|minmax|avsigclip)</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='reject' Line='reject = "none" (none|minmax|avsigclip)' -->
  <dd>Type of rejection operation performed on the pixels which overlap at each
  dispersion coordinate.  The algorithms are discussed in the
  DESCRIPTION section.  The rejection choices are:
  <pre>
        none - No rejection
      minmax - Reject the nlow and nhigh pixels
   avsigclip - Reject pixels using an averaged sigma clipping algorithm
  </pre>
  </dd>
  </dl>
  <dl>
  <dt><b>scale = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='scale' Line='scale = no' -->
  <dd>Scale the sky spectra by the mode?
  </dd>
  </dl>
  <dl>
  <dt><b>saveskys = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='saveskys' Line='saveskys = yes' -->
  <dd>Save the sky spectra?  If no then the mean sky spectra will be deleted after
  sky subtraction is completed.  Otherwise a one dimensional image with
  the prefix <tt>"sky"</tt> and then the output name is created.
  </dd>
  </dl>
  <dl>
  <dt><b>logfile = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = ""' -->
  <dd>Logfile for making a record of the sky subtraction operation.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This task selects a subset of aperture spectra from a multispec
  format image, called sky spectra though they could be anything,
  and combines them into a master spectrum which is subtracted
  from another subset of spectra called the objects.  Options include
  saving the master sky spectrum and reviewing the selected sky spectra
  graphically and deleting some of them.
  </p>
  <p>
  The sky apertures are selected using the aperture and beam numbers
  defined during extraction (see the <b>apextract</b> package).  In
  some applications the beam numbers are used to code object and sky
  apertures and selection by beam number is quite easy.  Otherwise one
  must list the aperture numbers explicitly.
  </p>
  <p>
  The object apertures are also selected using an aperture and beam
  number list.  Spectra not selected to be objects are not modified
  by the sky subtraction.  Note that it is perfectly valid to include
  the sky spectra in the object list to produce residual sky spectra.
  </p>
  <p>
  When interactively editing the sky spectra the task <b>specplot</b>
  is used.  To delete a spectrum type <tt>'d'</tt>.  To undelete the last deleted
  spectrum type <tt>'e'</tt>.  When finished type <tt>'e'</tt>.
  </p>
  <p>
  The sky spectra are combined using one of combining and rejection options from
  the task <b>scombine</b> except for the option <tt>"none"</tt>.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1.  To median and subtract apertures 1,10,15,20 from all apertures:
  </p>
  <pre>
      ms&gt; skysub obj010.ms out=skysub010.ms skyaps="1,10,15,20"
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  specplot, scombine
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
