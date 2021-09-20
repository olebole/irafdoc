.. _clear:

clear: Clear the terminal screen
================================

**Package: language**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  clear
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The <i>clear</i> command clears the terminal screen.  For this to work properly
  the environment variable <i>terminal</i> must correctly identify the terminal
  currently in use.  If the terminal should get stuck in reverse video mode,
  <i>clear</i> will restore normal video mode as well as clearing the screen.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Clear the screen and print the current directory.
  </p>
  <p>
  	cl&gt; cle;dir
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  beep, stty
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
