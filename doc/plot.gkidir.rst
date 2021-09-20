.. _gkidir:

gkidir: Directory listing of metacode file
==========================================

**Package: plot**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  gkidir -- print directory of plots within the named metacode file
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  gkidir input
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>The metacode file or files to be examined.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Task <b>gkidir</b> examines GKI metacode files, and prints a directory of
  the plots contained in each input file.  Each plot is listed with its
  size and an identifying title string.  The title string is the MFTITLE
  string if given, or else the longest GTEXT string found (hopefully the
  plot title), or else the string <span style="font-family: monospace;">"(no title)"</span>.  The output format is as
  follows:
  </p>
  <pre>
  
  	file1: 
  	    [1] (1234 words)	title_string
  	    [2] (78364 words)	title_string
  
  	file2:
  	    [1] (874 words)	title_string
  		.
  		.
  		.
  
  </pre>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. List the plots in the GKI metacode file <span style="font-family: monospace;">"file"</span>:
  </p>
  <p>
      cl&gt; gkidir file
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  gkiextract
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
