.. _lparam:

lparam — List the parameters of a task
======================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  lparam -- list the parameters of a task or pset
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  lparam pset [pset ...]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>pset</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pset' Line='pset'>
  <DD>The name of the parameter set to be listed.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Lparam</I> lists one or more parameter sets.  Psets are specified either by
  the name of the task with which the pset is associated, or by filename (pset
  files have the "<TT>.par</TT>" extension).  If a file type pset is listed the extension
  must be included, since it is the presence or absence of the filename
  extension which <B>lparam</B> uses to distinguish between task-psets and named
  (file) psets.
  <P>
  Each parameter is listed on a single line with the following format:
  <P>
  	param = value		prompt string
  <P>
  Here "<TT>param</TT>" is the name of the parameter, "<TT>value</TT>" is the current value of
  the parameter (blank if undefined), and "<TT>prompt string</TT>" is the prompt for
  the parameter, if any.  If the parameter is hidden, then the line is enclosed
  in parentheses.  For arrays, instead of the values, a list of the
  dimensionalities is given.  The <I>eparam</I> task may be used to examine
  or edit the contents of an array.  When more than one task is listed the
  task name is prefixed to the list of each tasks parameters.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. List the parameter for the task <I>delete</I>.  Note that the positional
  parameters are listed first, in the order in which they must be specified
  on the command line, followed by the hidden parameters.
  <P>
  <PRE>
  cl&gt; lparam delete
          files = "temp"          list of files to be deleted
       go_ahead = yes              ?
        (verify = no)             verify operation before deleting each file?
  (default_acti = yes)            default delete action for verify query
   (allversions = yes)            delete all versions of each file
      (subfiles = yes)            delete any subfiles of each file
          (mode = "ql")           
  </PRE>
  <P>
  2. List the contents of the file pset "<TT>delete.par</TT>".  Named psets such as this
  are most commonly produced using the <B>":w filename"</B> colon command in
  <B>eparam</B>, e.g., to prepare several different versions of the parameter
  set for a task.
  <P>
  	cl&gt; lparam delete.par
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  You cannot list the parameters of a task that does not have a parameter
  file (e.g., all builtin tasks).
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  eparam, dparam, cache
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
