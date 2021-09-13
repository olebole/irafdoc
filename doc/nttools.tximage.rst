.. _tximage:

tximage — Extract images from rows of 3-D tables.
=================================================

**Package: nttools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tximage -- Extract 1-D images from cells of a 3-D table.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tximage intable output
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task extracts one or more 1-D images from cells of a 3-D table.
  The input may be a filename template, including wildcard characters, 
  or the name of a file (preceded by an @ sign) containing table names. 
  The output may be either a directory specification or a list of image names. 
  If the output is a list of images then there must be the same number of names 
  in the input and output lists, and the names are taken in pairs, one from 
  input and one from output.
  <P>
  Images can be extracted only from a single column in the input table.
  That column must be designated by an appropriate column selector appended to 
  the table name. Type 'help selectors' to get more information on row/column 
  selector syntax.
  <P>
  Row selectors may be used to select subsets of rows from the input table.
  If no row selector is used, all rows will be extracted, and the number
  of output images will be the number of rows in the input table.
  <P>
  Since one input table may generate several output images, the task adopts
  the following naming scheme for these output images: their names are
  built by appending a suffix to the name given in parameter "<TT>output</TT>".
  The suffix has the form "<TT>_rXXXX</TT>", where XXXX stands for the row number 
  in the input table. The suffix is appended before the file name extension.
  The task recognizes as valid image name extensions the values "<TT>.??h</TT>",
  "<TT>.fits</TT>" and "<TT>.fit</TT>". Any other extension is assumed to be part of the root
  file name. If only one row is extracted, no suffixing takes place.
  <P>
  NOTE: Be careful when using a wildcard for the extension.
  If you have the files "<TT>table.tab</TT>" and "<TT>table.lis</TT>" in the current directory,
  for example, then the command "<TT>tximage tab* test/</TT>" would expand both files 
  to the subdirectory "<TT>test</TT>".
  <P>
  Basic column information describing the column where the image came from
  is written into the image header in the "<TT>COLDATA</TT>" keyword. This information
  can be used later by task 'tiimage' to re-insert the image into a cell of 
  a 3-D table.
  <P>
  The task does not propagate array dimensionality when extracting arrays
  into images. If dimensionality information exists in the 3-D table, that 
  information is lost, that is, the table cell from the input table is written 
  as a structureless, plain 1-D image.
  <P>
  The input row number is written to the header of the output image in
  keyword ORIG_ROW. This allows 'tiimage' to put the data back where 
  'tximage' got them from.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>intable [file name list/template]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name list/template]'>
  <DD>A list of one or more tables to be expanded. A column selector selecting
  a single column is mandatory. Row selectors are supported as well.
  </DD>
  </DL>
  <DL>
  <DT><B>output [file name template]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output [file name template]'>
  <DD>Either a directory name or a list of output image names.
  </DD>
  </DL>
  <DL>
  <DT><B>(verbose = yes) [boolean]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(verbose = yes) [boolean]'>
  <DD>Display names of input and output files ?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  Extract 1-D images from a column named FLUX from rows 11 to 13 of a 3-D 
  table:
  <P>
  <PRE>
  cl&gt; tximage "table.tab[c:FLUX][r:row=(11:13)]" image
  </PRE>
  <P>
  This will generate three images named "<TT>image_r0011</TT>", "<TT>image_r0012</TT>"
  and "<TT>image_r0013</TT>".
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>References</H3>
  <! BeginSection: 'REFERENCES'>
  <UL>
  This task was written by I. Busko.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  tiimage, selectors
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
