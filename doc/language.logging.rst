.. _logging:

logging: Discussion of CL logging
=================================

**Package: language**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <pre>
  logging -- Using the CL logging features
  </pre>
  <!-- EndSection:   'NAME' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The CL has some simple logging features to allow the recording of events of
  interactive sessions.  From these saved event logs, one can trace a particular
  data analysis sequence, track errors in programs, and create new CL scripts. 
  Other uses for the logfile exist as well. 
  </p>
  <p>
  There are currently five types of logging messages, with a parameter to
  control what is actually logged.  These include:
  </p>
  <pre>
         commands - commands and keystrokes of an interactive session
       background - messages about and from background jobs
           errors - logging of error messages
            trace - start/stop trace of script and executable tasks
             user - user messages, via the <i>putlog</i> builtin
  </pre>
  <p>
  All of these types of messages except the interactive commands will show up as
  comments (i.e., starting with a <tt>'#'</tt>) in the logfile.  This facilitates using a
  previous logfile as input to the CL or as the basis for a script task. 
  </p>
  <p>
  The CL parameters discussed below are used to control the logging features.
  These parameters can be set on the command line, in the <tt>"login.cl"</tt> file, or
  with the command <tt>"eparam cl"</tt>. 
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>keeplog = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='keeplog' Line='keeplog = no' -->
  <dd>The overall on/off switch for the CL logging.  When set to `yes', the logfile
  will be opened and logging will commence.  If the named logfile does not
  exist, it will be created, otherwise log messages will be appended to the
  existing file.
  </dd>
  </dl>
  <dl>
  <dt><b>logfile = <tt>"home$logfile"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = "home$logfile"' -->
  <dd>The name of the logfile.
  </dd>
  </dl>
  <dl>
  <dt><b>logmode = <tt>"commands nobackground noerrors notrace"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='logmode' Line='logmode = "commands nobackground noerrors notrace"' -->
  <dd><i>Logmode</i> controls what goes into the logfile.  The following options
  are currently available:
  <dl>
  <dt><b>[no]commands</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='' Line='[no]commands' -->
  <dd>Enables or disables logging of interactive commands.  (This is usually always
  enabled.)
  </dd>
  </dl>
  <dl>
  <dt><b>[no]background</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='' Line='[no]background' -->
  <dd>Enables or disables background logging.  This includes start/stop messages
  when background jobs are submitted and complete, as well as log messages
  from the background job itself.
  </dd>
  </dl>
  <dl>
  <dt><b>[no]errors</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='' Line='[no]errors' -->
  <dd>Enables or disables error logging within script and executable tasks.
  If enabled, error messages printed on the terminal will also be logged.
  </dd>
  </dl>
  <dl>
  <dt><b>[no]trace</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='' Line='[no]trace' -->
  <dd>Enables or disables tracing of script and executable tasks.  If enabled, start
  and stop messages are logged, which include the package and task names, and the
  time.  The start message also includes the filename of the task (.cl or .e). 
  </dd>
  </dl>
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Turn all the logging features on except for background logging:
  </p>
  <p>
  	cl&gt; logmode = <tt>"commands nobackground errors trace"</tt>
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  Background logging to the same logfile can cause problems.  The environment
  variable <i>filewait</i> should be set to `no' to avoid file access conflicts.
  Even with this, reliability is not guaranteed and some messages will not
  get into the logfile.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  cl, putlog
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
