.. _logging:

logging — Discussion of CL logging
==================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  <PRE>
  logging -- Using the CL logging features
  </PRE>
  </UL>
  <! EndSection:   'NAME'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The CL has some simple logging features to allow the recording of events of
  interactive sessions.  From these saved event logs, one can trace a particular
  data analysis sequence, track errors in programs, and create new CL scripts. 
  Other uses for the logfile exist as well. 
  <P>
  There are currently five types of logging messages, with a parameter to
  control what is actually logged.  These include:
  <P>
  <PRE>
  <PRE>
         commands - commands and keystrokes of an interactive session
       background - messages about and from background jobs
           errors - logging of error messages
            trace - start/stop trace of script and executable tasks
             user - user messages, via the <I>putlog</I> builtin
  </PRE>
  </PRE>
  <P>
  All of these types of messages except the interactive commands will show up as
  comments (i.e., starting with a <TT>'#'</TT>) in the logfile.  This facilitates using a
  previous logfile as input to the CL or as the basis for a script task. 
  <P>
  The CL parameters discussed below are used to control the logging features.
  These parameters can be set on the command line, in the "<TT>login.cl</TT>" file, or
  with the command "<TT>eparam cl</TT>". 
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>keeplog = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='keeplog' Line='keeplog = no'>
  <DD>The overall on/off switch for the CL logging.  When set to `yes', the logfile
  will be opened and logging will commence.  If the named logfile does not
  exist, it will be created, otherwise log messages will be appended to the
  existing file.
  </DD>
  </DL>
  <DL>
  <DT><B>logfile = "<TT>home$logfile</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = "home$logfile"'>
  <DD>The name of the logfile.
  </DD>
  </DL>
  <DL>
  <DT><B>logmode = "<TT>commands nobackground noerrors notrace</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logmode' Line='logmode = "commands nobackground noerrors notrace"'>
  <DD><P>
  <I>Logmode</I> controls what goes into the logfile.  The following options
  are currently available:
  <DL>
  <DT><B>[no]commands</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='[no]commands'>
  <DD>Enables or disables logging of interactive commands.  (This is usually always
  enabled.)
  </DD>
  </DL>
  <DL>
  <DT><B>[no]background</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='[no]background'>
  <DD>Enables or disables background logging.  This includes start/stop messages
  when background jobs are submitted and complete, as well as log messages
  from the background job itself.
  </DD>
  </DL>
  <DL>
  <DT><B>[no]errors</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='[no]errors'>
  <DD>Enables or disables error logging within script and executable tasks.
  If enabled, error messages printed on the terminal will also be logged.
  </DD>
  </DL>
  <DL>
  <DT><B>[no]trace</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='[no]trace'>
  <DD>Enables or disables tracing of script and executable tasks.  If enabled, start
  and stop messages are logged, which include the package and task names, and the
  time.  The start message also includes the filename of the task (.cl or .e). 
  </DD>
  </DL>
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Turn all the logging features on except for background logging:
  <P>
  	cl&gt; logmode = "<TT>commands nobackground errors trace</TT>"
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  Background logging to the same logfile can cause problems.  The environment
  variable <I>filewait</I> should be set to `no' to avoid file access conflicts.
  Even with this, reliability is not guaranteed and some messages will not
  get into the logfile.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  cl, putlog
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
