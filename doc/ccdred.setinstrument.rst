.. _setinstrument:

setinstrument — Set instrument parameters
=========================================

**Package: ccdred**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  setinstrument -- Set instrument parameters
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  setinstrument instrument
  </UL>
  <! EndSection:   'USAGE	'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>instrument</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='instrument' Line='instrument'>
  <DD>Instrument identification for instrument parameters to be set.  If <TT>'?'</TT>
  then a list of the instrument identifiers is printed.
  </DD>
  </DL>
  <DL>
  <DT><B>site = "<TT>kpno</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='site' Line='site = "kpno"'>
  <DD>Site ID.
  </DD>
  </DL>
  <DL>
  <DT><B>directory = "<TT>ccddb$</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='directory' Line='directory = "ccddb$"'>
  <DD>Instrument directory containing instrument files.  The instrument files
  are found in the subdirectory given by the site ID. 
  </DD>
  </DL>
  <DL>
  <DT><B>review = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='review' Line='review = yes'>
  <DD>Review the instrument parameters?  If yes then <B>eparam</B> is run for
  the parameters of <B>ccdred</B> and <B>ccdproc</B>.
  </DD>
  </DL>
  <DL>
  <DT><B>query</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='query' Line='query'>
  <DD>Parameter query if initial instrument is not found.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The purpose of the task is to allow the user to easily set default
  parameters for a new instrument.  The default parameters are generally
  defined by support personal in an instrument directory for a particular
  site.  The instrument directory is the concatenation of the specified
  directory and the site.  For example if the directory is "<TT>ccddb$</TT>" and
  the site is "<TT>kpno</TT>" then the instrument directory is "<TT>ccddb$kpno/</TT>".
  The user may have his own set of instrument files in a local directory.
  The current directory is used by setting the directory and site to the
  null string ("<TT></TT>").
  <P>
  The user specifies an instrument identifier.  This instrument may
  be specific to a particular observatory, telescope, instrument, and
  detector.  If the character <TT>'?'</TT> is specified or the instrument file is
  not found then a list of instruments
  in the instrument directory is produced by paging the file "<TT>instruments.men</TT>".
  The task then performs the following operations:
  <DL>
  <DT><B>(1)</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(1)'>
  <DD>If an instrument translation file with the name given by the instrument
  ID and the extension "<TT>.dat</TT>" is found then the instrument translation
  file parameter, <I>ccdred.instrument</I>, is set to this file.
  If it does not exist then the user is queried again.  Note that a
  null instrument, "<TT></TT>", is allowed to set no translation file.
  </DD>
  </DL>
  <DL>
  <DT><B>(2)</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(2)'>
  <DD>If an instrument setup script with the name given by the instrument ID
  and the extension "<TT>.cl</TT>" is found then the commands in the file are
  executed (using the command <I>cl &lt; script</I>.  This script generally
  sets default parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>(3)</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(3)'>
  <DD>If the review flag is set the task <B>eparam</B> is run to allow the user
  to examine and modify the parameters for the package <B>ccdred</B> and task
  <B>ccdproc</B>.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To get a list of the instruments;
  <P>
  <PRE>
  	cl&gt; setinstrument ?
  	[List of instruments]
  <P>
  2. To set the instrument and edit the processing parameters:
  <P>
  	cl&gt; setinstrument ccdlink
  	[Edit CCDRED parameters]
  	[Edit CCDPROC parameters]
  <P>
  3. To use your own instrument translation file and/or setup script in
  your working directory.
  <P>
  	cl&gt; setinst.site=""
  	cl&gt; setinst.dir=""
  	cl&gt; setinst myinstrument
  <P>
  To make these files see help under <B>instruments</B>.  Copying and modifying
  system files is also straightforward.
  <P>
  	cl&gt; copy ccddb$kpno/fits.dat .
  	cl&gt; edit fits.dat
  	cl&gt; setinst.site=""
  	cl&gt; setinst.dir=""
  	cl&gt; setinst fits
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  instruments, ccdred, ccdproc
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
