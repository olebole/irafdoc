.. _setinstrument:

setinstrument: Set instrument parameters
========================================

**Package: ccdred**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  setinstrument -- Set instrument parameters
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage	</h3>
  <!-- BeginSection: 'USAGE	' -->
  <p>
  setinstrument instrument
  </p>
  <!-- EndSection:   'USAGE	' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>instrument</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='instrument' Line='instrument' -->
  <dd>Instrument identification for instrument parameters to be set.  If <tt>'?'</tt>
  then a list of the instrument identifiers is printed.
  </dd>
  </dl>
  <dl>
  <dt><b>site = <tt>"kpno"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='site' Line='site = "kpno"' -->
  <dd>Site ID.
  </dd>
  </dl>
  <dl>
  <dt><b>directory = <tt>"ccddb$"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='directory' Line='directory = "ccddb$"' -->
  <dd>Instrument directory containing instrument files.  The instrument files
  are found in the subdirectory given by the site ID. 
  </dd>
  </dl>
  <dl>
  <dt><b>review = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='review' Line='review = yes' -->
  <dd>Review the instrument parameters?  If yes then <b>eparam</b> is run for
  the parameters of <b>ccdred</b> and <b>ccdproc</b>.
  </dd>
  </dl>
  <dl>
  <dt><b>query</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='query' Line='query' -->
  <dd>Parameter query if initial instrument is not found.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The purpose of the task is to allow the user to easily set default
  parameters for a new instrument.  The default parameters are generally
  defined by support personal in an instrument directory for a particular
  site.  The instrument directory is the concatenation of the specified
  directory and the site.  For example if the directory is <tt>"ccddb$"</tt> and
  the site is <tt>"kpno"</tt> then the instrument directory is <tt>"ccddb$kpno/"</tt>.
  The user may have his own set of instrument files in a local directory.
  The current directory is used by setting the directory and site to the
  null string (<tt>""</tt>).
  </p>
  <p>
  The user specifies an instrument identifier.  This instrument may
  be specific to a particular observatory, telescope, instrument, and
  detector.  If the character <tt>'?'</tt> is specified or the instrument file is
  not found then a list of instruments
  in the instrument directory is produced by paging the file <tt>"instruments.men"</tt>.
  The task then performs the following operations:
  </p>
  <dl>
  <dt><b>(1)</b></dt>
  <!-- Sec='DESCRIPTION' Level=0 Label='' Line='(1)' -->
  <dd>If an instrument translation file with the name given by the instrument
  ID and the extension <tt>".dat"</tt> is found then the instrument translation
  file parameter, <i>ccdred.instrument</i>, is set to this file.
  If it does not exist then the user is queried again.  Note that a
  null instrument, <tt>""</tt>, is allowed to set no translation file.
  </dd>
  </dl>
  <dl>
  <dt><b>(2)</b></dt>
  <!-- Sec='DESCRIPTION' Level=0 Label='' Line='(2)' -->
  <dd>If an instrument setup script with the name given by the instrument ID
  and the extension <tt>".cl"</tt> is found then the commands in the file are
  executed (using the command <i>cl &lt; script</i>.  This script generally
  sets default parameters.
  </dd>
  </dl>
  <dl>
  <dt><b>(3)</b></dt>
  <!-- Sec='DESCRIPTION' Level=0 Label='' Line='(3)' -->
  <dd>If the review flag is set the task <b>eparam</b> is run to allow the user
  to examine and modify the parameters for the package <b>ccdred</b> and task
  <b>ccdproc</b>.
  </dd>
  </dl>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. To get a list of the instruments;
  </p>
  <pre>
  	cl&gt; setinstrument ?
  	[List of instruments]
  
  2. To set the instrument and edit the processing parameters:
  
  	cl&gt; setinstrument ccdlink
  	[Edit CCDRED parameters]
  	[Edit CCDPROC parameters]
  
  3. To use your own instrument translation file and/or setup script in
  your working directory.
  
  	cl&gt; setinst.site=""
  	cl&gt; setinst.dir=""
  	cl&gt; setinst myinstrument
  
  To make these files see help under <b>instruments</b>.  Copying and modifying
  system files is also straightforward.
  
  	cl&gt; copy ccddb$kpno/fits.dat .
  	cl&gt; edit fits.dat
  	cl&gt; setinst.site=""
  	cl&gt; setinst.dir=""
  	cl&gt; setinst fits
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  instruments, ccdred, ccdproc
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
