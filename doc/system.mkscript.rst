mkscript — Make a command script
================================

**Package: system**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>mkscript (Nov85)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>system</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>mkscript (Nov85)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>mkscript</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  mkscript -- make a script for a command sequence to be run in batch
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage_">USAGE	</A></H2>
  <! BeginSection: 'USAGE	'>
  <UL>
  mkscript script task submit
  </UL>
  <! EndSection:   'USAGE	'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_script">script</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='script' Line='script'>
  <DD>Script file name.  Commands will be successively added to this file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_task">task   </A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='task' Line='task   '>
  <DD>Task name of command to be added to the script.  If given on the command
  line then only commands for this task may be added to the script.
  If not given on the command line then the task will query for a task
  name for each new command.  Currently the task name must not be abbreviated.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_submit">submit</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='submit' Line='submit'>
  <DD>Submit the completed script as a background job as the last act of the task?
  If not given on the command line the task will query before submitting the
  script.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_append">append = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='append' Line='append = no'>
  <DD>Append new commands to an existing script file?
  If no the file will be deleted first.   If <I>verify</I> = yes
  the user will be asked to confirm the deletion.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_hidden">hidden = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='hidden' Line='hidden = yes'>
  <DD>Include hidden parameters in each command?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verify">verify = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verify' Line='verify = yes'>
  <DD>Verify each command, any file deletions, and the final script?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logfile">logfile = "<TT>script.log</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = "script.log"'>
  <DD>Script log file name.  When the script is submitted as a background job
  by this task any command and error output is directed to this file.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  A command script is created consisting of a number of commands to be
  executed sequentially.  The task assumes the responsibility of formatting
  the command and placing it in the script file.  The user sets the
  parameter values using the parameter editor <B>eparam</B>.  As an optional
  final stage the task will optionally submit the script as a background job.
  <P>
  The sequence of steps are outline as follows:
  <DL>
  <DT><B><A NAME="l_">(1)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(1)'>
  <DD>If the script already exists and <I>append</I> = no the script file
  is deleted.  When <I>verify</I> = yes the deletion is verified with the
  user.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(2)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(2)'>
  <DD>If the task is not specified on the command line then the user
  is queried for a task name.
  <DL>
  <DT><B><A NAME="l_">(2a)</A></B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='(2a)'>
  <DD>The task must be loaded.  If it has not been loaded a message is printed
  and the task query is repeated.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(3)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(3)'>
  <DD><B>Eparam</B> is now invoked to allow the user to set the task
  parameters.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(4)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(4)'>
  <DD>If <I>verify</I> = yes the command is printed and the user is asked if the
  command is ok.  If ok the command is added to the script.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(5)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(5)'>
  <DD>The user is asked if another command is to be added to the script.  While
  the response is yes steps 2 to 5 are repeated.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(6)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(6)'>
  <DD>If <I>verify</I> = yes the script is paged and the user is asked if the
  script is ok.  If not ok the script is deleted, with user confirmation,
  and steps 2 to 6 are repeated.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(7)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(7)'>
  <DD>If the submit parameter is not specified on the command line the user
  is asked if the script should be submitted as a background job.
  </DD>
  </DL>
  <P>
  The parameter <I>hidden</I> is important for the following reason.  If
  the hidden parameters are not explicitly included in the script commands
  then the values of the hidden parameters will be those in the parameter
  file at the time of execution.  Thus, in changes in the hidden parameters
  with <B>eparam</B> or explicit changes may produce unexpected results.
  However, if the hidden parameters are never changed then the commands
  are more readable when the hidden parameters are not included.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  One of the most common usages in data reductions is to create repeated
  commands with different input data or parameters.
  <P>
  <PRE>
  cl&gt; mkscript script.cl transform
  <P>
  [<I>eparam</I> is called to set the parameter values for <I>transform</I>]
  <P>
  transform ("n1r.008", "n1r.008a", "disp012,distort,disp013",
  database="identify.db", interptype="spline3", x1=1., x2=256., dx=1.,
  nx=256., xlog=no, y1=4300., y2=6300., dy=INDEF, ny=800., ylog=no,
  flux=yes, logfiles="STDOUT,logfile")
  <P>
  Is the command ok? (yes):
  Add another command? (yes):
  <P>
  [<I>eparam</I> is called again for task <I>transform</I>]
  <P>
  transform ("n1r.010", "n1r.010a", "disp013,distort",
  database="identify.db", interptype="spline3", x1=1., x2=256., dx=1.,
  nx=256., xlog=no, y1=4300., y2=6300., dy=INDEF, ny=800., ylog=no,
  flux=yes, logfiles="STDOUT,logfile")
  <P>
  Is the command ok? (yes):
  Add another command? (yes): no
  <P>
  [The script is paged]
  <P>
  Is the script ok? (yes):
  Submit the script as a background job? (yes):
  Script script.cl submitted at:
  Fri 10:32:57 01-Nov-85
  [1]
  </PRE>
  <P>
  To combine several tasks:
  <P>
  <PRE>
  cl&gt; mkscript script.cl ver- sub- hid-
  Task name of command to be added to script: response
  <P>
  [<I>eparam</I> is called for <I>response</I> and parameter values are set]
  <P>
  Add another command? (yes):
  Task name of command to be added to script: imarith
  Add another command? (yes): no
  </PRE>
  <P>
  To run the command script as a foreground job:
  <P>
  cl&gt; cl &lt; script.cl
  <P>
  To run the command script as a background job:
  <P>
  cl&gt; cl &lt; script.cl &gt;&amp; logfile &amp;
  <P>
  Note that the output including possible error output is redirected to a logfile.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  The current implementation is preliminary.  It is done with a script which
  makes it seem somewhat slow.  The most important bug is that the command
  formatter is based on the output of <B>lparam</B>.  If a task parameter
  name exceeds 12 characters it is truncated by <B>lparam</B> and is then
  also truncated by the command formatter.  The script will then fail when
  executed!  Also the task name may not be abbreviated.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  eparam
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>