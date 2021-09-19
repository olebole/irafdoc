.. _quadsections:

quadsections: Produce image section list for sections of quadformat images
==========================================================================

**Package: quadred**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  quadsections -- Create image sections
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  quadsplit images
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>images</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='images' Line='images' -->
  <dd>List of image names for images in <b>quadformat</b>.
  </dd>
  </dl>
  <dl>
  <dt><b>window = <tt>"datasec"</tt> (datasec|trimsec|biassec)</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='window' Line='window = "datasec" (datasec|trimsec|biassec)' -->
  <dd>Type of section to output.  The choices are <tt>"datasec"</tt> for the amplifier
  section which includes the bias if any is present, <tt>"trimsec"</tt> for the trim
  section, and <tt>"biassec"</tt> for the bias section.
  </dd>
  </dl>
  <dl>
  <dt><b>section = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='section' Line='section = ""' -->
  <dd>Section to be overlapped.  The output sections will be the parts of the
  amplifier windows which are included within this section.
  </dd>
  </dl>
  <dl>
  <dt><b>template = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='template' Line='template = ""' -->
  <dd>Template for producing the output.  The template replaces occurs of
  $I with the image name, $S with the section, and $A with the amplifier
  label.  If none is specified then the default template <tt>"$I$S\\n"</tt> is
  used which produces the image name with section separated by new-lines.
  The special characters <tt>"\n"</tt> is the new-line and the extra <tt>"\"</tt> is
  required to pass the new-line through to the formatting routine.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Images in <tt>"quadformat"</tt> (see help topic <b>quadformat</b>) are broken down
  in sections and written to the standard output in a specified format.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. To print the default data sections.
  </p>
  <pre>
      qu&gt; quadsec quad0072
      quad0072[1:1034,1:1024]
      quad0072[1163:2196,1:1024]
      quad0072[1:1034,1025:2048]
      quad0072[1163:2196,1025:2048]
  </pre>
  <p>
  3. To apply an overlap section.
  </p>
  <pre>
      qu&gt; quadsec quad0072 section=[1000:2000,1000:2000]
      quad0072[1000:1034,1000:1024]
      quad0072[1163:2000,1000:1024]
      quad0072[1000:1034,1025:2000]
      quad0072[1163:2000,1025:2000]
  </pre>
  <p>
  2. To print the trim sections.
  </p>
  <pre>
      qu&gt; quadsec quad0072 window=trimsec
      quad0072[11:1034,1:1024]
      quad0072[1163:2186,1:1024]
      quad0072[11:1034,1025:2048]
      quad0072[1163:2186,1025:2048]
  </pre>
  <p>
  4.  To make a custom output.
  </p>
  <pre>
      qu&gt; quadsec quad0072 template="image=$I, section=$S, amplifier=$A\\n"
      image=quad0072, section=[1:1034,1:1024], amplifier=11
      image=quad0072, section=[1163:2196,1:1024], amplifier=12
      image=quad0072, section=[1:1034,1025:2048], amplifier=21
      image=quad0072, section=[1163:2196,1025:2048], amplifier=22
      qu&gt; quadsec quad0072 template="$I.$A,"
      quad0072.11,quad0072.12,quad0072.21,quad0072.22,
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  quadformat
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
