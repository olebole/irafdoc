.. _lprint:

lprint: Print a file on the line printer device
===============================================

**Package: system**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  lprint -- print a file or files
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  lprint files
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>files</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='files' Line='files' -->
  <dd>A filename template specifying the files to be printed.
  </dd>
  </dl>
  <dl>
  <dt><b>device = <tt>"printer"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='device' Line='device = "printer"' -->
  <dd>The output device.  If the value of <i>device</i> is the reserved string
  <tt>"printer"</tt>, the name of the actual printer device is taken from the value
  of the environment variable <tt>"printer"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>map_cc = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='map_cc' Line='map_cc = yes' -->
  <dd>If set to <tt>"yes"</tt>, any unprintable characters embedded in the text are printed
  in the form <tt>"^X"</tt>, where ^A is &lt;ctrl/A&gt; (ASCII 1), and so on.
  </dd>
  </dl>
  <dl>
  <dt><b>paginate = <tt>"auto"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='paginate' Line='paginate = "auto"' -->
  <dd>If <i>paginate</i> is set to <tt>"auto"</tt> and the standard input is not redirected,
  pages are broken and a header is printed at the top of each page.
  If <i>paginate</i> is set to <tt>"auto"</tt> and the standard input <i>is</i> redirected,
  the input text is not paginated, allowing proper operation when <i>lprint</i>
  is used in a pipe, e.g., taking input from <i>help</i>.
  If <tt>"paginate"</tt> is set to <tt>"yes"</tt>, pages are broken even if the input text
  is being read from STDIN.
  </dd>
  </dl>
  <dl>
  <dt><b>label = <tt>"STDIN"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='label' Line='label = "STDIN"' -->
  <dd>If displaying a header with input from the standard input, use the
  <tt>"label"</tt> string where the filename would appear in a normal header.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The named files, or the standard input, are printed on the standard
  line printer device.  Each file is printed starting at the top of a new
  page, with a header giving the page number and the date of last modification
  for the file.  Pagination and headers are normally suppressed when reading
  input from the standard input, but may be enabled if desired.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Print all files with an extension of either <tt>".x"</tt> or <tt>".h"</tt>, followed by
  all files with the extension <tt>".com"</tt>.  Note that filename sorting occurs only
  within a comma delimited field of the filename template, hence the <tt>"*.[xh]"</tt>
  files are printed in sort order, followed by the <tt>".com"</tt> files.
  </p>
  <p>
  	cl&gt; lprint *.[xh],*.com
  </p>
  <p>
  2. Print the output of the <i>imstat</i> task on the versatec printer,
  paginating the output with the given label on each page.  Note that the
  command may be broken after the <tt>"pipe"</tt> character without need for
  explicit backslash continuation.
  </p>
  <pre>
  	cl&gt; imstat nite1.* |
  	&gt;&gt;&gt; lprint pag+ label="Image Statistics" device=versatec
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  type
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
