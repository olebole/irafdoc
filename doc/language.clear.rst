.. _clear:

clear — Clear the terminal screen
=================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  clear -- clear the terminal screen
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  clear
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>clear</I> command clears the terminal screen.  For this to work properly
  the environment variable <I>terminal</I> must correctly identify the terminal
  currently in use.  If the terminal should get stuck in reverse video mode,
  <I>clear</I> will restore normal video mode as well as clearing the screen.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Clear the screen and print the current directory.
  <P>
  	cl&gt; cle;dir
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  beep, stty
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
