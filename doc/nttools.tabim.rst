.. _tabim:

tabim: Copy a table column to an image.
=======================================

**Package: nttools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  tabim -- Copy a table column to an image.
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  tabim intable output colname ndim n1 n2 n3 n4 n5 n6
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  This task writes values from a column of a table to an image.
  If the image does not exist, it will be created.
  The value in the first row is assigned to the first pixel of the image,
  and the value in the last row is assigned to the last pixel of the image.
  Columns containing pixel numbers (optionally written by 'imtab') are ignored,
  but you can specify the axis lengths of a multi-dimensional output image.
  The number of rows in the table must equal the number of pixels in the image.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>intable = <tt>""</tt> [file name template]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='intable' Line='intable = "" [file name template]' -->
  <dd>The names of the input tables.
  </dd>
  </dl>
  <dl>
  <dt><b>output = <tt>""</tt> [file name template]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output = "" [file name template]' -->
  <dd>The names of the output images.
  If an output image does not exist it will be created.
  If the image does exist it will be overwritten with values from the table.
  A section of an existing image may be specified,
  but note that the size must equal the number of rows in the table.
  </dd>
  </dl>
  <dl>
  <dt><b>colname = <tt>""</tt> [string]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='colname' Line='colname = "" [string]' -->
  <dd>The name of the column in 'intable' that is to be written to the image.
  The same column name is used for all input tables.
  </dd>
  </dl>
  <dl>
  <dt><b>ndim = 0 [integer, min=0, max=7]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ndim' Line='ndim = 0 [integer, min=0, max=7]' -->
  <dd>If the output image does not exist,
  'ndim' can be used to specify
  the dimension of the image to be created.
  ndim = 0 or 1 results in a one-dimensional image
  which has as many elements as rows in the table.
  If 'ndim' is greater than one
  and the output image does not already exist,
  then the parameters 'n1', 'n2', etc will be taken
  to specify the axis lengths of the output image.
  The lengths of all but the last axis will be gotten from 'n1', 'n2', etc.;
  the last axis length will be computed from
  the number of rows in the table
  and the lengths of the other axes.
  It is an error if the product of the specified axis lengths
  does not divide evenly into the number of rows in the table.
  </dd>
  </dl>
  <dl>
  <dt><b>n1 = 1 [integer, min=1, max=INDEF]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='n1' Line='n1 = 1 [integer, min=1, max=INDEF]' -->
  <dd>Length of first axis.
  'n1', 'n2', etc., are ignored if ndim = 0 or 1.
  </dd>
  </dl>
  <dl>
  <dt><b>n2 = 1 [integer, min=1, max=INDEF]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='n2' Line='n2 = 1 [integer, min=1, max=INDEF]' -->
  <dd>Length of second axis.
  This and the subsequent axis length parameters will be ignored if ndim &lt; 3.
  </dd>
  </dl>
  <dl>
  <dt><b>n3 = 1 [integer, min=1, max=INDEF]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='n3' Line='n3 = 1 [integer, min=1, max=INDEF]' -->
  <dd>Length of third axis.
  </dd>
  </dl>
  <dl>
  <dt><b>n4 = 1 [integer, min=1, max=INDEF]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='n4' Line='n4 = 1 [integer, min=1, max=INDEF]' -->
  <dd>Length of fourth axis.
  </dd>
  </dl>
  <dl>
  <dt><b>n5 = 1 [integer, min=1, max=INDEF]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='n5' Line='n5 = 1 [integer, min=1, max=INDEF]' -->
  <dd>Length of fifth axis.
  </dd>
  </dl>
  <dl>
  <dt><b>n6 = 1 [integer, min=1, max=INDEF]</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='n6' Line='n6 = 1 [integer, min=1, max=INDEF]' -->
  <dd>Length of sixth axis.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1.  Copy column <tt>"flux"</tt> from table <tt>"hr465.tab"</tt> to
  the 1-D image <tt>"hr465_flux.imh"</tt>:
  </p>
  <pre>
  	ta&gt; tabim hr465.tab hr465_flux.imh flux 1
  </pre>
  <p>
  2.  Create a three-dimensional image <tt>"ir27.imh"</tt> of size 62 x 64 x 4.
  Read the values from column <tt>"v1"</tt> of table <tt>"t18_30.tab"</tt>,
  which has 62*64*4 rows.
  </p>
  <pre>
  	ta&gt; tabim t18_30.tab ir27.imh v1 3 62 64
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>References</h3>
  <!-- BeginSection: 'REFERENCES' -->
  <p>
  This task was written by Phil Hodge.
  </p>
  <!-- EndSection:   'REFERENCES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  The 'imtab' task copies an image to a column of a table.
  </p>
  <p>
  Type <tt>"help tables option=sys"</tt> for a higher-level description of
  the tables package.
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  -->
  
