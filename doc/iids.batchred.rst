.. _batchred:

batchred — Batch processing of IIDS/IRS spectra
===============================================

**Package: iids**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  batchred - Automated processing of IIDS/IRS spectra
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  batchred
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  This script task has many parameters, but most are used as
  variables internal to the task and are not user parameters.
  There are 5 parameters having similar purposes: standard,
  sensfunc, bswitch, calibrate, and addsets. Each corresponds
  to the ONEDSPEC task of the same name and BATCHRED will generate
  the commands necessary to invoke those tasks if the associated
  parameter is set to yes (the default in all cases).
  <P>
  <DL>
  <DT><B>standard = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='standard' Line='standard = yes'>
  <DD></DD>
  </DL>
  <DL>
  <DT><B>sensfunc = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sensfunc' Line='sensfunc = yes'>
  <DD></DD>
  </DL>
  <DL>
  <DT><B>bswitch = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='bswitch' Line='bswitch = yes'>
  <DD></DD>
  </DL>
  <DL>
  <DT><B>calibrate = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='calibrate' Line='calibrate = yes'>
  <DD></DD>
  </DL>
  <DL>
  <DT><B>addsets = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='addsets' Line='addsets = yes'>
  <DD></DD>
  </DL>
  <DL>
  <DT><B>fnu = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fnu' Line='fnu = no'>
  <DD>This parameter is identical to the fnu parameter for CALIBRATE.
  </DD>
  </DL>
  <DL>
  <DT><B>wave1 = 0.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wave1' Line='wave1 = 0.0'>
  <DD>This parameter is identical to the wave1 parameter for BSWITCH.
  </DD>
  </DL>
  <DL>
  <DT><B>wave2 = 0.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wave2' Line='wave2 = 0.0'>
  <DD>This parameter is identical to the wave2 parameter for BSWITCH.
  </DD>
  </DL>
  <DL>
  <DT><B>subset = 32767</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='subset' Line='subset = 32767'>
  <DD>This parameter is identical to the subset parameter for BSWITCH.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Through a question and answer session, a series of commands to
  ONEDSPEC is generated which are then processed as a batch job
  to reduce "<TT>typical</TT>" spectra from the IIDS and IRS spectrographs.
  <P>
  By setting the appropriate hidden parameters, the user may
  "<TT>turn off</TT>" command generation for any of the possible tasks.
  <P>
  A script task is generated having the name "<TT>process.cl</TT>" which is
  submitted to the CL as the final command of BATCHRED.
  All terminal output which would normally appear during the course
  of running each of the individual tasks is redirected to a log file
  (default=ttylog).
  <P>
  After the script has been generated, the user may suppress running
  the processing task. The script file remains on disk so that subsequent
  cases may be appended, such as when
  several independent runs of data are to be processed in one
  stream (e.g. several nights of data, each to be reduced separately).
  <P>
  The questions which are asked are described below:
  <P>
  "<TT>Root name for spectra file names:</TT>" This is the input root file name
  for all spectra which will be run through STANDARD and BSWITCH.
  <P>
  "<TT>Root name for spectra to be created:</TT>" This is the output root file
  name which all newly created spectra will use. It is also the
  input file name for tasks CALIBRATE and ADDSETS since these tasks
  operate on spectra created by BSWITCH.
  <P>
  "<TT>Starting record number for spectra to be created:</TT>" All created spectra
  will have a suffix number starting with this value and incremented
  by one for each new spectrum created.
  <P>
  "<TT>File name to contain statistics information:</TT>" This file will contain
  informative output from SENSFUNC and BSWITCH. (default=stats)
  <P>
  "<TT>File name to contain a log of terminal output:</TT>" All tasks talk back
  to let you know how things are proceding. The backtalk is saved
  in this file. (default=ttylog)
  <P>
  "<TT>File name for output from STANDARD and input to SENSFUNC:</TT>" Just
  what it says. (default=std)
  <P>
  "<TT>Record string to process:</TT>" The spectra are assumed to be representable
  by strings (try "<TT>help ranges</TT>" for details on the formats allowed).
  Both STANDARD and BSWITCH expect ranges of spectral record numbers
  which are appended to the root given in answer to the first question
  above. This question is asked repeatedly so that you can enter as
  many strings of spectra as you like and is ended by hitting return
  without entering a value. There is a short delay after entering
  each string of records while a check is made to verify that all
  your spectra actually exist.
  <P>
  "<TT>Standard star name:</TT>" For each record string STANDARD expects
  the name of the standard star observed, but it must be given in
  a manner acceptable to STANDARD. (see STANDARD and LCALIB for
  more details).
  <P>
  "<TT>Use weighted averages:</TT>" If answered yes, then SENSFUNC and BSWITCH
  will use their weighted averaging schemes.
  <P>
  "<TT>Apply magnitude fudging:</TT>" If answered yes, then SENSFUNC will 
  use its "<TT>fudge</TT>" option. (see SENSFUNC)
  <P>
  "<TT>Solve for grey additive extinction constant:</TT>" If answered yes, then
  SENSFUNC will solve for this value.
  <P>
  "<TT>File name for sensitivity image file:</TT>" This will be the root name
  for the output sensitivity spectra from SENSFUNC.
  <P>
  At anytime during the processing phase, you can inquire about the
  progress by listing the latest contents of the file "<TT>ttylog</TT>"
  either by "<TT>type ttylog</TT>" or by "<TT>tail ttylog</TT>". The latter command
  lists the last 12 lines of the file.
  <P>
  Be sure to have all your record strings, standard star names,
  and options well planned and written down so that you can enter
  the answers correctly. The batch reductions are not overly
  tolerant of incorrect entries although some preliminary checks
  are performed during the entry process.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  The following invokes the batch reductions using all task options;
  <P>
  	cl&gt; batchred
  <P>
  The following inhibits the STANDARD and SENSFUNC tasks which must have
  been run previously. This is equivalent to the IPPS "<TT>autoreduce</TT>":
  <P>
  	cl&gt; batchred standard- sensfunc-
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  If you make an error while entering the requested information, there
  is no way to effect repairs other than to (1) start all over, or (2) edit
  the generated script file "<TT>process.cl</TT>" using the system editor.
  <P>
  If a task encounters an irrecoverable error, the background job
  hangs until you kill it using "<TT>kill N</TT>" where N is the job number.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  mkscript, standard, sensfunc, bswitch, calibrate, addsets
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
