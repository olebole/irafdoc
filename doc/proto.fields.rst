.. _fields:

fields — Extract specified fields from a list
=============================================

**Package: proto**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  fields -- extract selected fields from a list.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  fields files fields
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>files</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>File or files from which the fields are to be extracted.
  </DD>
  </DL>
  <DL>
  <DT><B>fields</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fields' Line='fields'>
  <DD>The fields to be extracted.  
  </DD>
  </DL>
  <DL>
  <DT><B>lines = "<TT>1-</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lines' Line='lines = "1-"'>
  <DD>The lines from which the fields are to be extracted.  If multiple files are 
  being extracted, the same lines apply to each file.
  </DD>
  </DL>
  <DL>
  <DT><B>quit_if_missing = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='quit_if_missing' Line='quit_if_missing = no'>
  <DD>This flag determines the task behavior when a field is missing from the
  specified line.  If <B>quit_if_missing</B> = yes, the task exits and an error 
  is reported.
  </DD>
  </DL>
  <DL>
  <DT><B>print_file_names = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='print_file_names' Line='print_file_names = no'>
  <DD>If <B>print_file_name</B> = yes, the first string of each output line of
  extracted fields is the file name.  
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The list processing tool <I>fields</I> is used to extract whitespace
  separated fields from the specified files and lines.
  The input to this task can be either the standard input or a list of
  files; output is a new list of the extracted fields.
  <P>
  The fields of a line are numbered from 1 up to a newline character; those
  fields to be extracted are specified as a range of numbers.
  If a specified field is missing from a selected
  line the action taken is determined by the <B>quit_if_missing</B> flag;
  <I>fields</I> will either continue processing after printing a warning
  message, or call an error and exit.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Reverse the order of the 5 columns in list file "<TT>list</TT>".
  <PRE>
  <P>
  	cl&gt; fields list 5-1 &gt; newlist
  </PRE>
  <P>
  2. Extract columns 1 and 3 from file "<TT>newlist</TT>" and pipe them to task
  <I>graph</I>.
  <PRE>
  <P>
  	cl&gt; fields newlist 1,3 | graph
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>FIELDS V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='FIELDS' Line='FIELDS V2.11'>
  <DD>The default value for the <I>lines</I> parameter was changed to an open
  upper limit.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  joinlines, xtools.ranges
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
