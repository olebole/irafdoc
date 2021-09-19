.. _txsort:

txsort: Sort a list of apphot/daophot text databases
====================================================

**Package: ptools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  txsort -- sort a list of APPHOT/DAOPHOT text database file(s)
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  txsort textfile field
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>textfiles </b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='textfiles' Line='textfiles ' -->
  <dd>The input APPHOT/DAOPHOT text database(s) to be sorted.
  The sort is performed in place.
  </dd>
  </dl>
  <dl>
  <dt><b>field</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='field' Line='field' -->
  <dd>The field to be sorted on. <i>Field</i> may be any quantity defined by
  the APPHOT/DAOPHOT #K and #N keywords. The keywords may be
  of type integer or real, in which case a numeric sort is performed,
  boolean, in which case the boolean constant <tt>"no"</tt> has a smaller value
  than <tt>"yes"</tt>, or character in which case an alphabetic sort is performed.
  </dd>
  </dl>
  <dl>
  <dt><b>ascend = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ascend' Line='ascend = yes' -->
  <dd>Sort in increasing value order.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  TXSORT is a simple task which accepts a list of APPHOT/DAOPHOT text
  database files
  and sorts them in place based on the value of the selected field
  specifier <i>field</i>. By default the sort is performed in increasing order
  of the value
  of <i>field</i>, but a reverse sort can be performed by 
  setting <i>ascend</i> = <tt>"no"</tt>.
  </p>
  <p>
  If <i>field</i> is a real or integer quantity the sort is numeric; if boolean
  the boolean constant <tt>"no"</tt> is assumed to have a smaller value than <tt>"yes"</tt>; if
  character the sort is alphabetic.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1.  Sort the output of the APPHOT task PHOT in increasing order of
  the y position.
  </p>
  <pre>
      pt&gt; txsort m92.mag.1 YCENTER
  </pre>
  <p>
  2. Sort the output of the DAOPHOT task ALLSTAR in increasing order of
     magnitude.
  </p>
  <pre>
      pt&gt; txsort m92.al.1 MAG
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  ptools.tbsort,tables.tsort,ptools.psort,sort
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
