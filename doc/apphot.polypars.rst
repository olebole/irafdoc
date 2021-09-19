.. _polypars:

polypars: Edit the polyphot parameters
======================================

**Package: apphot**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  polypars -- edit the polygonal aperture photometry parameters
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  polypars
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>zmag = 25.00</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='zmag' Line='zmag = 25.00' -->
  <dd>The zero point offset for the magnitude scale.
  </dd>
  </dl>
  <dl>
  <dt><b>mkpolygon = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='mkpolygon' Line='mkpolygon = no' -->
  <dd>Draw the polygons on the screen.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The zero point of the magnitude scale is determined by <i>zmag</i>.
  </p>
  <p>
  If the <i>mkpolygon</i> switch is enabled polygons are marked on the screen.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. List the polygonal aperture photometry parameters.
  </p>
  <pre>
  	ap&gt; lpar polypars
  </pre>
  <p>
  2. Edit the polygonal aperture photometry parameters.
  </p>
  <pre>
  	ap&gt; polypars
  </pre>
  <p>
  3. Edit the POLYPARS parameters from within the POLYPHOT task.
  </p>
  <pre>
      da&gt; epar polyphot
  
  	... edit a few polyphot parameters
  
  	... move to the polypars parameter and type :e
  
  	... edit the polypars parameters and type :wq
  
  	... finish editing the polyphot parameters and type :wq
  </pre>
  <p>
  4. Save the current POLYPARS parameter set in a text file polynite1.par.
  This can also be done from inside a higher level task as in the
  above example.
  </p>
  <pre>
      da&gt; polypars
  
  	... edit some parameters
  
  	... type ":w polynite1.par"  from within epar
  
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
  polyphot. polymark
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
