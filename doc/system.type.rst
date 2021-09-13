.. _type:

type — Type a text file on the standard output
==============================================

**Package: system**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  type -- type a file or files on the standard output
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  type input_files
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input_files</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input_files' Line='input_files'>
  <DD>A template specifying the file or files to be typed.
  </DD>
  </DL>
  <DL>
  <DT><B>map_cc = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='map_cc' Line='map_cc = yes'>
  <DD>If set, output any non-printing control characters in the input text in
  a printable form, e.g., ctrl/c (ASCII 3) would be output as ^C.
  </DD>
  </DL>
  <DL>
  <DT><B>device = "<TT>terminal</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='device' Line='device = "terminal"'>
  <DD>The output device, defaulting to the user's terminal.  If the special device
  "<TT>text</TT>" is named, any standout mode control characters embedded in the text
  will cause the enclosed text to be output in upper case.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Type</I> copies the named files (or the files selected by
  the file template) to the standard output.
  If there is more than one file in the input list, a header naming the file
  to be printed will precede each output file.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Type all files in the current directory with the extension "<TT>.x</TT>" on the
  standard output.  Do not pause between files or pages (unlike <I>page</I>).
  <P>
  	cl&gt; type *.x
  <P>
  2. Capture the manual page for task <I>hedit</I> in a text file, in a form
  suitable for printing on any device.
  <P>
  	cl&gt; help hedit | type dev=text &gt; hedit.doc
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  page, head, tail, concatenate, lprint
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
