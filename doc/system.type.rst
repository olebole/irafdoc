.. _type:

type: Type a text file on the standard output
=============================================

**Package: system**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  type -- type a file or files on the standard output
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  type input_files
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input_files</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input_files' Line='input_files' -->
  <dd>A template specifying the file or files to be typed.
  </dd>
  </dl>
  <dl>
  <dt><b>map_cc = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='map_cc' Line='map_cc = yes' -->
  <dd>If set, output any non-printing control characters in the input text in
  a printable form, e.g., ctrl/c (ASCII 3) would be output as ^C.
  </dd>
  </dl>
  <dl>
  <dt><b>device = <tt>"terminal"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='device' Line='device = "terminal"' -->
  <dd>The output device, defaulting to the user's terminal.  If the special device
  <tt>"text"</tt> is named, any standout mode control characters embedded in the text
  will cause the enclosed text to be output in upper case.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Type</i> copies the named files (or the files selected by
  the file template) to the standard output.
  If there is more than one file in the input list, a header naming the file
  to be printed will precede each output file.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Type all files in the current directory with the extension <tt>".x"</tt> on the
  standard output.  Do not pause between files or pages (unlike <i>page</i>).
  </p>
  <p>
  	cl&gt; type *.x
  </p>
  <p>
  2. Capture the manual page for task <i>hedit</i> in a text file, in a form
  suitable for printing on any device.
  </p>
  <p>
  	cl&gt; help hedit | type dev=text &gt; hedit.doc
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  page, head, tail, concatenate, lprint
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
