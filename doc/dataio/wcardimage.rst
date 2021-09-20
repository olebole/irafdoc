.. _wcardimage:

wcardimage: Convert text files to cardimage files
=================================================

**Package: dataio**

.. raw:: html

  <h3>Usage	</h3>
  <!-- BeginSection: 'USAGE	' -->
  <p>
  wcardimage infiles outfiles
  </p>
  <!-- EndSection:   'USAGE	' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>textfile</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='textfile' Line='textfile' -->
  <dd>A character string identifying the file (s) on disk to be processed.
  The string acts as a <span style="font-family: monospace;">"template"</span> so that multiple files can be pro-
  cessed.
  </dd>
  </dl>
  <dl>
  <dt><b>cardfile</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='cardfile' Line='cardfile' -->
  <dd>Name of the output tape device of the form <span style="font-family: monospace;">"mta800"</span> or <span style="font-family: monospace;">"mta800[#]"</span>
  or name of disk file (s). EOT and BOT are acceptable tape file numbers.
  The file number will be appended to
  the output file name in the case of multiple file disk output.
  </dd>
  </dl>
  <dl>
  <dt><b>new_tape</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='new_tape' Line='new_tape' -->
  <dd>Specifies whether the output tape is blank or contains data.
  </dd>
  </dl>
  <dl>
  <dt><b>contn_string = <span style="font-family: monospace;">"&gt;&gt;"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='contn_string' Line='contn_string = "&gt;&gt;"' -->
  <dd>Character string which will be inserted at the beginning of
  card image lines which have been split from a single text line.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes' -->
  <dd>Print messages of actions performed?
  </dd>
  </dl>
  <dl>
  <dt><b>detab = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='detab' Line='detab = yes' -->
  <dd>Remove tabs?
  </dd>
  </dl>
  <dl>
  <dt><b>card_length = 80</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='card_length' Line='card_length = 80' -->
  <dd>Number of columns per card.
  </dd>
  </dl>
  <dl>
  <dt><b>cards_per_blk = 50</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='cards_per_blk' Line='cards_per_blk = 50' -->
  <dd>Number of card images per physical record.
  </dd>
  </dl>
  <dl>
  <dt><b>ebcdic = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ebcdic' Line='ebcdic = no' -->
  <dd>Translate ascii characters to ebcdic?
  </dd>
  </dl>
  <dl>
  <dt><b>ibm = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ibm' Line='ibm = no' -->
  <dd>Translate ascii characters to ibm ebcdic?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  If multiple file disk output is requested, <span style="font-family: monospace;">".crd"</span> is appended to the input
  file name. Oversize lines are split and prefixed by the string <span style="font-family: monospace;">"&gt;&gt;"</span>.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Convert a set of IRAF text files to a set of blocked ASCII cardimage files
  on tape, replacing tabs with blanks and prefixing the leftover portions
  of oversize lines with <span style="font-family: monospace;">"&gt;&gt;"</span>.
  </p>
  <pre>
  
  	cl&gt; wcardimage files* mtb1600[1]
  </pre>
  <p>
  2. Convert a set of IRAF text files to a set of blocked EBCDIC cardimage files
  on tape, replacing tabs with blanks and prefixing the leftover portions
  of oversize lines with <span style="font-family: monospace;">"&gt;&gt;"</span>.
  </p>
  <p>
  	cl&gt; wcardimage files* mtb1600[1] eb+
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  The card_length in bytes must be an integral number of chars.
  At present WCARDIMAGE can only handle lines with less than or equal to
  161 characters.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  rcardimage
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
