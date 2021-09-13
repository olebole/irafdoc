.. _ecidentify:

ecidentify — Identify features in spectrum for dispersion solution
==================================================================

**Package: echelle**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  ecidentify -- Determine the dispersion relation in echelle spectra
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  ecidentify images
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of echelle format spectra in which to identify lines and fit
  dispersion functions.
  </DD>
  </DL>
  <DL>
  <DT><B>database = "<TT>database</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database = "database"'>
  <DD>Database in which the feature data and dispersion functions are recorded.
  </DD>
  </DL>
  <DL>
  <DT><B>coordlist = "<TT>linelists$idhenear.dat</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coordlist' Line='coordlist = "linelists$idhenear.dat"'>
  <DD>User coordinate list consisting of an ordered list of line coordinates.  A
  comment line of the form "<TT># units &lt;units&gt;</TT>", where &lt;units&gt; is one of the
  understood units names, defines the units of the line list.  If no units
  are specified then Angstroms are assumed.  Some standard line lists are
  available in the directory "<TT>linelists$</TT>".  The standard line lists are
  described under the topic <I>linelists</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>units = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='units' Line='units = ""'>
  <DD>The units to use if no database entry exists.  The units are specified as
  described in
  <P>
  <PRE>
      cl&gt; help onedspec.package section=units
  </PRE>
  <P>
  If no units are specified and a coordinate list is used then the units of
  the coordinate list are selected.  If a database entry exists then the
  units defined there override both this parameter and the coordinate list.
  </DD>
  </DL>
  <DL>
  <DT><B>match = 1.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='match' Line='match = 1.'>
  <DD>The maximum difference for a match between the feature coordinate function
  value and a coordinate in the coordinate list.  The unit of this parameter
  is that of the user coordinates.
  </DD>
  </DL>
  <DL>
  <DT><B>maxfeatures = 100</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxfeatures' Line='maxfeatures = 100'>
  <DD>Maximum number of the strongest features to be selected automatically from
  the coordinate list (function <TT>'l'</TT>) or from the image data (function <TT>'y'</TT>).
  </DD>
  </DL>
  <DL>
  <DT><B>zwidth = 10.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zwidth' Line='zwidth = 10.'>
  <DD>Width of graphs, in user coordinates, when in zoom mode (function <TT>'z'</TT>).
  </DD>
  </DL>
  <P>
  The following parameters are used in determining feature positions.
  <DL>
  <DT><B>ftype = "<TT>emission</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ftype' Line='ftype = "emission"'>
  <DD>Type of features to be identified.  The possibly abbreviated choices are
  "<TT>emission</TT>" and "<TT>absorption</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>fwidth = 4.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fwidth' Line='fwidth = 4.'>
  <DD>Width in pixels of features to be identified.
  </DD>
  </DL>
  <DL>
  <DT><B>cradius = 5.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cradius' Line='cradius = 5.'>
  <DD>The maximum distance, in pixels, allowed between a feature position
  and the initial estimate when defining a new feature.
  </DD>
  </DL>
  <DL>
  <DT><B>threshold = 10.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='threshold' Line='threshold = 10.'>
  <DD>In order for a feature center to be determined the range of pixel intensities
  around the feature must exceed this threshold.
  </DD>
  </DL>
  <DL>
  <DT><B>minsep = 2.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='minsep' Line='minsep = 2.'>
  <DD>The minimum separation, in pixels, allowed between feature positions
  when defining a new feature.
  </DD>
  </DL>
  <P>
  The following default parameters are used when fitting a function to
  the user coordinates.  If a previous solution is read from the database
  then the parameters from that solution override the defaults below.
  <DL>
  <DT><B>function = "<TT>chebyshev</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = "chebyshev"'>
  <DD>The function to be fit to the user coordinates as a function of the pixel
  coordinate and aperture number.  The choices are bi-dimensional
  "<TT>chebyshev</TT>" and "<TT>legendre</TT>" polynomials.
  </DD>
  </DL>
  <DL>
  <DT><B>xorder = 2</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xorder' Line='xorder = 2'>
  <DD>Order of the fitting function along each echelle order.
  The order is the number of polynomial terms; i.e. xorder = 2 is a linear
  function.
  </DD>
  </DL>
  <DL>
  <DT><B>yorder = 2</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='yorder' Line='yorder = 2'>
  <DD>Order of the fitting function with respect to the aperture number.
  The order is the number of polynomial terms; i.e. yorder = 2 is a linear
  function.
  </DD>
  </DL>
  <DL>
  <DT><B>niterate = 0, lowreject = 3, highreject = 3.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='niterate' Line='niterate = 0, lowreject = 3, highreject = 3.'>
  <DD>Default number of rejection iterations and the sigma clipping thresholds.  If
  <I>niterate</I> is zero then no rejection is done.
  </DD>
  </DL>
  <P>
  The following parameters control the graphics input and output.
  <DL>
  <DT><B>graphics = "<TT>stdgraph</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>Graphics device.  The default is the standard graphics device which is
  generally a graphics terminal.
  </DD>
  </DL>
  <DL>
  <DT><B>curosr = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='curosr' Line='curosr = ""'>
  <DD>Cursor input file.  If a cursor file is not given then the standard graphics
  cursor is read.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Cursor keys</H3>
  <! BeginSection: 'CURSOR KEYS'>
  <UL>
  <P>
  <PRE>
             ECIDENTIFY CURSOR KEY AND COLON COMMAND SUMMARY
  <P>
  ?  Help                   a  Affect all features     c  Center feature(s)
  d  Delete feature(s)      f  Fit dispersion          g  Fit zero point shift
  i  Initialize             j  Go to previous order    k  Go to next order
  l  Match coordinate list  m  Mark feature            n  Next feature
  o  Go to specified order  p  Pan graph               q  Quit
  r  Redraw graph           s  Shift feature           t  Reset position
  u  Enter user coordinate  w  Window graph            x  Crosscorrelate peaks
  y  Find peaks             z  Zoom graph              .  Nearest feature
  +  Next feature           -  Previous feature        I  Interrupt
  <P>
  :show [file]              :features [file]           :coordlist [file]
  :cradius [value]          :threshold [value]         :database [file]
  :ftype [type]             :fwidth [value]            :image [image]
  :labels [type]            :match [value]             :maxfeatures [value]
  :minsep [value]           :read [image]              :write [image]
  :zwidth [value]
  <P>
  <P>
         ECHELLE DISPERSION FUNCTION FITTING COMMAND SUMMARY
  <P>
  ?  Help             c  Print coordinates             d  Delete point
  f  Fit dispersion   o  Fit with fixed order offset   q  Quit
  r  Redraw graph     u  Undelete point                w  Window graph
  x  Set ordinate     y  Set abscissa                  I  Interrupt
  <P>
  :show               :function [value]   :highreject [value]   :lowreject [value]
  :niterate [value]   :xorder [value]     :yorder [value]
  <P>
  </PRE>
  <P>
              ECIDENTIFY CURSOR KEYS AND COLON COMMANDS
  <DL>
  <DT><B>?</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line='?'>
  <DD>Clear the screen and print a menu of cursor and colon commands.
  </DD>
  </DL>
  <DL>
  <DT><B>a</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='a' Line='a'>
  <DD>Apply next (c)enter or (d)elete operation to (a)ll features
  </DD>
  </DL>
  <DL>
  <DT><B>c</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='c' Line='c'>
  <DD>(C)enter the feature nearest the cursor.  Used when changing the position
  finding parameters or when features are defined from a previous feature list.
  May be used in combination with the (a)ll key.
  </DD>
  </DL>
  <DL>
  <DT><B>d</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='d' Line='d'>
  <DD>(D)elete the feature nearest the cursor.  (D)elete all features when preceded
  by the (a)ll key.  This does not affect the dispersion function.
  </DD>
  </DL>
  <DL>
  <DT><B>f</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='f' Line='f'>
  <DD>(F)it a function of the pixel coordinates and aperture numbers to the user
  coordinates.  This enters an interactive function fitting package.
  </DD>
  </DL>
  <DL>
  <DT><B>g</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='g' Line='g'>
  <DD>Fit a zero point shift to the user coordinates by minimizing the difference
  between the user and fitted coordinates.  The coordinate dispersion function
  is not changed.
  </DD>
  </DL>
  <DL>
  <DT><B>i</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='i' Line='i'>
  <DD>(I)nitialize (delete features and dispersion function fit).
  </DD>
  </DL>
  <DL>
  <DT><B>j</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='j' Line='j'>
  <DD>Go to the next aperture in decreasing line number in the echelle format image.
  Wrap around to the last line from the first line.
  </DD>
  </DL>
  <DL>
  <DT><B>k</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='k' Line='k'>
  <DD>Go to the next aperture in increasing line number in the echelle format image.
  Wrap around to the first line from the last line.
  </DD>
  </DL>
  <DL>
  <DT><B>l</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='l' Line='l'>
  <DD>(L)ocate features in the coordinate list.  A coordinate function must be
  defined or at least four features in more than one aperture must have user
  coordinates from which a coordinate function can be determined by an
  initial automatic function fit.
  </DD>
  </DL>
  <DL>
  <DT><B>m</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='m' Line='m'>
  <DD>(M)ark a new feature using the cursor position as the initial position
  estimate.
  </DD>
  </DL>
  <DL>
  <DT><B>n</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='n' Line='n'>
  <DD>Move the cursor or zoom to the (n)ext feature (same as +).
  </DD>
  </DL>
  <DL>
  <DT><B>o</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='o' Line='o'>
  <DD>Go to a specific aperture (related to an echelle (o)rder).  The user
  is queried for the aperture number.
  </DD>
  </DL>
  <DL>
  <DT><B>p</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='p' Line='p'>
  <DD>(P)an to the original window after (z)ooming on a feature.
  </DD>
  </DL>
  <DL>
  <DT><B>q</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='q' Line='q'>
  <DD>(Q)uit and continue with next image.
  </DD>
  </DL>
  <DL>
  <DT><B>r</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='r' Line='r'>
  <DD>(R)edraw the graph.
  </DD>
  </DL>
  <DL>
  <DT><B>s</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='s' Line='s'>
  <DD>(S)hift the fit coordinates relative to the pixel coordinates.  The
  user specifies the desired coordinate at the position of the cursor
  and a zero point shift to the fit coordinates is applied.  If features
  are defined then they are recentered and the shift is the average shift.
  The shift in pixels, user coordinates, and z (fractional shift) is printed.
  The user shift is for the fundamental order and the shift for each order
  is then given by this shift divided by the order number.
  </DD>
  </DL>
  <DL>
  <DT><B>t</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='t' Line='t'>
  <DD>Reset the current feature to the position of the cursor.  The feature
  is <I>not</I> recentered.  This is used to mark an arbitrary position.
  </DD>
  </DL>
  <DL>
  <DT><B>u</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='u' Line='u'>
  <DD>Enter a new (u)ser coordinate for the current feature.
  When (m)arking a new feature the user coordinate is also requested.
  </DD>
  </DL>
  <DL>
  <DT><B>w</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='w' Line='w'>
  <DD>(W)indow the graph.  A window prompt is given and a number of windowing
  options may be given.  For more help type <TT>'?'</TT> to the window prompt or
  see help under <I>gtools</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>x</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='x' Line='x'>
  <DD>Crosscorrelate features with the data peaks and reregister.  This is
  generally used with a feature list from a different image.
  The mean shift in user coordinates, mean shift in pixels, and the fractional
  shift in user coordinates is printed.  The user shift is scaled to the
  fundamental order.
  </DD>
  </DL>
  <DL>
  <DT><B>y</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='y' Line='y'>
  <DD>Up to <I>maxfeatures</I> emission peaks are found automatically (in order of
  peak intensity) and, if a dispersion solution is defined, the peaks are
  identified from the coordinate list.
  </DD>
  </DL>
  <DL>
  <DT><B>z</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='z' Line='z'>
  <DD>(Z)oom on the feature nearest the cursor.  The width of the zoom window
  is determined by the parameter <I>zwidth</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>.</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line='.'>
  <DD>Move the cursor or zoom window to the feature nearest the cursor.
  </DD>
  </DL>
  <DL>
  <DT><B>+</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line='+'>
  <DD>Move the cursor or zoom window to the (n)ext feature.
  This does not automatically move to the next aperture.
  </DD>
  </DL>
  <DL>
  <DT><B>-</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line='-'>
  <DD>Move the cursor or zoom window to the previous feature.
  This does not automatically move to the next aperture.
  </DD>
  </DL>
  <DL>
  <DT><B>I</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='I' Line='I'>
  <DD>Interrupt the task immediately.  The database is not updated.
  </DD>
  </DL>
  <P>
  Parameters are shown or set with the following "<TT>colon commands</TT>", which may be
  abbreviated.  To show the value of a parameter type the parameter name alone
  and to set a new value follow the parameter name by the value.
  <DL>
  <DT><B>:show file</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':show file'>
  <DD>Show the values of all the parameters.  If a file name is given then the
  output is appended to that file.  If no file is given then the terminal
  is cleared and the output is sent to the terminal.
  </DD>
  </DL>
  <DL>
  <DT><B>:features file</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':features file'>
  <DD>Print the feature list and the fit rms.  If a file name is given then the
  output is appended to that file.  If no file is given then the terminal
  is cleared and the output is sent to the terminal.
  </DD>
  </DL>
  <DL>
  <DT><B>:coordlist file</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':coordlist file'>
  <DD>Set or show the coordinate list file.
  </DD>
  </DL>
  <DL>
  <DT><B>:cradius value</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':cradius value'>
  <DD>Set or show the centering radius in pixels.
  </DD>
  </DL>
  <DL>
  <DT><B>:threshold value</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':threshold value'>
  <DD>Set or show the detection threshold for centering.
  </DD>
  </DL>
  <DL>
  <DT><B>:database name</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':database name'>
  <DD>Set or show the database for recording feature records.
  </DD>
  </DL>
  <DL>
  <DT><B>:ftype value</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':ftype value'>
  <DD>Set or show the feature type (emission or absorption).
  </DD>
  </DL>
  <DL>
  <DT><B>:fwidth value</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':fwidth value'>
  <DD>Set or show the feature width in pixels.
  </DD>
  </DL>
  <DL>
  <DT><B>:image imagename</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':image imagename'>
  <DD>Set a new image or show the current image.
  </DD>
  </DL>
  <DL>
  <DT><B>:labels value</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':labels value'>
  <DD>Set or show the feature label type (none, index, pixel, or user).
  </DD>
  </DL>
  <DL>
  <DT><B>:match value</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':match value'>
  <DD>Set or show the coordinate list matching distance.
  </DD>
  </DL>
  <DL>
  <DT><B>:maxfeatures value</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':maxfeatures value'>
  <DD>Set or show the maximum number of features automatically found.
  </DD>
  </DL>
  <DL>
  <DT><B>:minsep value</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':minsep value'>
  <DD>Set or show the minimum separation allowed between features.
  </DD>
  </DL>
  <DL>
  <DT><B>:read name</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':read name'>
  <DD>Read a record from the database.  The record name defaults to the image name.
  </DD>
  </DL>
  <DL>
  <DT><B>:threshold value</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':threshold value'>
  <DD>Set or show the centering threshold.
  </DD>
  </DL>
  <DL>
  <DT><B>:write name</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':write name'>
  <DD>Write a record to the database.  The record name defaults to the image name.
  </DD>
  </DL>
  <DL>
  <DT><B>:zwidth value</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':zwidth value'>
  <DD>Set or show the zoom width in user units.
  </DD>
  </DL>
  <P>
  <P>
                DISPERSION FUNCTION FITTING COMMANDS
  <DL>
  <DT><B>?</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line='?'>
  <DD>Page help information.
  </DD>
  </DL>
  <DL>
  <DT><B>c</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='c' Line='c'>
  <DD>Print input and fitted coordinates of point nearest the cursor.
  </DD>
  </DL>
  <DL>
  <DT><B>d</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='d' Line='d'>
  <DD>Delete the nearest undeleted point to the cursor.
  </DD>
  </DL>
  <DL>
  <DT><B>f</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='f' Line='f'>
  <DD>Fit a dispersion function including determining the order offset.
  </DD>
  </DL>
  <DL>
  <DT><B>o</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='o' Line='o'>
  <DD>Fit a dispersion function with the order offset fixed.  The user is queried
  for the order offset.  This is faster than the interactive fit to also
  determine the order.
  </DD>
  </DL>
  <DL>
  <DT><B>q</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='q' Line='q'>
  <DD>Quit and return to the spectrum display.
  </DD>
  </DL>
  <DL>
  <DT><B>r</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='r' Line='r'>
  <DD>Redraw the graph.
  </DD>
  </DL>
  <DL>
  <DT><B>u</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='u' Line='u'>
  <DD>Undelete the nearest deleted point to the cursor (which may be outside the
  graph window).
  </DD>
  </DL>
  <DL>
  <DT><B>w</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='w' Line='w'>
  <DD>Window the graph (type ? to the window prompt for more help).
  </DD>
  </DL>
  <DL>
  <DT><B>x</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='x' Line='x'>
  <DD>Set the quantity plotted along the ordinate (x axis).
  </DD>
  </DL>
  <DL>
  <DT><B>y</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='y' Line='y'>
  <DD>Set the quantity plotted along the abscissa (y axis).
  </DD>
  </DL>
  <DL>
  <DT><B>I</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='I' Line='I'>
  <DD>Interrupt the task immediately.  No information is saved in the database.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>:function [value]</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':function [value]'>
  <DD>Print or set the function type (chebyshev|legendre).
  </DD>
  </DL>
  <DL>
  <DT><B>:show</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':show'>
  <DD>Print current function and orders.
  </DD>
  </DL>
  <DL>
  <DT><B>:niterate [value], :lowreject [value], :highreject [value]</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':niterate [value], :lowreject [value], :highreject [value]'>
  <DD>Print or set the iterative rejection parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>:xorder [value]</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':xorder [value]'>
  <DD>Print or set the order for the dispersion dependence.
  </DD>
  </DL>
  <DL>
  <DT><B>:yorder [value]</B></DT>
  <! Sec='CURSOR KEYS' Level=0 Label='' Line=':yorder [value]'>
  <DD>Print or set the order for the echelle order dependence.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'CURSOR KEYS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Emission and absorption features in echelle format spectra (see <I>apsum</I>)
  are identified interactively and from a line list and a dispersion
  function is determined.  The results of the line identifications and
  dispersion function are stored in a database for further reference and
  for use with the tasks <B>ecreidentify</B> and <B>ecdispcor</B>.  Also
  the reference spectrum keyword REFSPEC is added to the image header.
  This is used by <B>refspectra</B> and <B>ecdispcor</B>.
  <P>
  Each spectrum in the input list is identified in turn.  Initially the
  order in the first image line is graphed.  The user may change the
  displayed order with the <TT>'j'</TT>, <TT>'k'</TT>, and <TT>'o'</TT> keys.  The initial feature
  list and dispersion function are read from the database if an entry
  exists.  The features are marked on the graph.  The image coordinates
  are in pixels unless a dispersion function is defined, in which case
  they are in user coordinate units (usually wavelength in Angstroms).
  The aperture number, pixel coordinate, coordinate function value, and
  user coordinate for the current feature are displayed on the status
  line.
  <P>
  For consistency the orders are always identified by their aperture
  numbers in this task and all other tasks.  These are the
  identifications assigned when extracting the orders using the task
  <I>apsum</I>.  If the user has assigned true order numbers as the
  aperture numbers then there is no distinction between aperture and
  order number.  However, it is often the case that the aperture numbers
  are simply assigned sequentially and the true order numbers may not
  even be known.  Initially the orders are the same as the apertures
  numbers but after fitting a dispersion function the true order numbers
  will be determined.  This information is also recorded in the database
  and indicated in the graph titles but selecting an order to be graphed
  with <TT>'o'</TT> and the status line information is always in terms of the
  aperture number.
  <P>
  The graphics cursor is used to select features and perform various
  functions.  A menu of the keystroke options and functions is printed
  with the key <TT>'?'</TT>.  The cursor keys and their functions are defined in
  the CURSOR KEYS sections and described further below.  The standard
  cursor mode keys are also available to window and redraw the graph and
  to produce hardcopy "<TT>snaps</TT>".
  <P>
  There are two types of feature selection functions;  defining new
  features and selecting previously defined features.  The key <TT>'m'</TT> marks
  a new feature nearest the cursor position.  The feature position is
  determined by the feature centering algorithm (see help for
  <B>center1d</B>).  The type of feature, emission or absorption, is set
  by the <I>ftype</I> parameter.  If the new position is within a distance
  given by the parameter <I>minsep</I> of a previous feature it is
  considered to be the same feature and replaces the old feature
  (normally the position of the new feature will be exactly the same as
  the original feature).  The coordinate list is searched for a match
  between the coordinate function value (when defined) and a user
  coordinate in the list.  If a match is found it becomes the default
  user coordinate which the user may override.  The new feature is marked
  on the graph and it becomes the current feature.  The redefinition of a
  feature which is within the minimum separation may be used to set the
  user coordinate from the coordinate list.  The key <TT>'t'</TT> allows setting
  the position of a feature to other than that found by the centering
  algorithm.
  <P>
  The <TT>'y'</TT> key applies a peak finding algorithm and up to the maximum
  number of features (<I>maxfeatures</I>) are found.  If there are more
  peaks only the strongest are kept.  The peaks are then matched against
  the coordinate list to find user coordinate values.
  <P>
  To select a different feature as the current feature the keys <TT>'.'</TT>, <TT>'n'</TT>,
  <TT>'+'</TT>, and <TT>'-'</TT> are used.  The <TT>'.'</TT> selects the feature nearest the cursor,
  the <TT>'n'</TT> and <TT>'+'</TT> select the next feature, and the <TT>'-'</TT> selects the
  previous feature relative to the current feature in the feature list as
  ordered by pixel coordinate.  These keys are useful when redefining the
  user coordinate with the <TT>'u'</TT> key and when examining features in zoom
  mode.  To change apertures (orders) the <TT>'j'</TT>, <TT>'k'</TT>, and <TT>'o'</TT> keys are
  used.
  <P>
  If four or more features are identified spanning the range of the data
  (in pixel coordinates and in order number) or if a coordinate function
  is defined then the <TT>'l'</TT> key may be used to identify additional features
  from a coordinate list.  If a coordinate function is not defined the
  default function is fit to the user coordinates of the currently
  defined features.  Then for each coordinate value in the coordinate
  list the pixel coordinate is determined and a search for a feature at
  that point is made.  If a feature is found (based on the parameters
  <I>ftype, fwidth</I>, <I>cradius</I>, and <B>threshold</B>) its user
  coordinate value based on the coordinate function is determined.  If
  the coordinate function value matches the user coordinate from the
  coordinate list within the error limit set by the parameter <I>match</I>
  then the new feature is entered in the feature list.  Up to a maximum
  number of features, set by the parameter <I>maxfeatures</I>, may be
  defined in this way.  A new user coordinate function is fit to all the
  located features.  Finally, the graph is redrawn in user coordinates
  with the additional features found from the coordinate list marked.
  <P>
  The <TT>'f'</TT> key fits a two dimensional function of the pixel coordinates
  and aperture number to the user coordinates.  The type of function and
  the orders are initially set with the parameters <I>function</I>,
  <I>xorder</I>, and <I>yorder</I>.  The value of the function for a
  particular pixel coordinate is called the function coordinate and each
  feature in the feature list has a function coordinate value.  The
  fitted function also is used to convert pixel coordinates to user
  coordinates in the graph.  Depending on the orders of the function
  four or more features are required covering at least two orders.
  A description of the dispersion function fitting is given the section
  ECHELLE DISPERSION FUNCTION FITTING.
  <P>
  If a zero point shift is desired without changing the coordinate function
  the user may specify the coordinate of a point in the spectrum with
  the <TT>'s'</TT> key from which a shift is determined.  The <TT>'g'</TT> key also
  determines a shift by minimizing the difference between the user
  coordinates and the fitted coordinates.  This is used when a previously
  determined coordinate function is applied to a new spectrum having
  fewer or poorer lines and only a zero point shift can reasonably be
  determined.  Note that the zero point shift is in user coordinates
  for the fundamental order.  The shift for any particular order is then
  the zero point shift divided by the order number.
  <P>
  Features may be delete with the key <TT>'d'</TT>.  All features are deleted when
  the <TT>'a'</TT> key immediately precedes the delete key.  Deleting the features
  does not delete the coordinate function.  To delete both the features
  and the dispersion function the initialize key <TT>'i'</TT> is used.  Note
  features deleted during dispersion function fitting also are removed
  from the feature list upon exiting the fitting package.
  <P>
  It is common to transfer the feature identifications and coordinate
  function from one image to another.  When a new image without a
  database entry is examined, such as when going to the next image in the
  input list or selecting a new image with the "<TT>:image</TT>" command, the
  current feature list and coordinate function are kept.  Alternatively,
  a database record from a different image may be read with the "<TT>:read</TT>"
  command.  When transferring feature identifications between images the
  feature coordinates will not agree exactly with the new image feature
  positions and several options are available to reregister the feature
  positions.  The key <TT>'c'</TT> centers the feature nearest the cursor using
  the current position as the starting point.  When preceded with the <TT>'a'</TT>
  key all the features are recentered (the user must refit the coordinate
  function if desired).  As an aside, the recentering function is also
  useful when the parameters governing the feature centering algorithm
  are changed.
  <P>
  The (c)entering function is applicable when the shift between the
  current and true feature positions is small.  Larger shifts may be
  determined automatically with the <TT>'x'</TT> function which correlates
  features in the image with the feature list.  The features are then
  recentered.  A zero point shift may also be given interactively with
  the <TT>'s'</TT> key by using the cursor to indicate the coordinate of a point
  in the spectrum.  If there are no features then the shift is exactly as
  marked by the cursor but if there are features the approximate shift is
  applied and then the features are recentered.  The shift is then the
  mean shift of the features after recentering.  The shift is used as a
  zero point offset added to the dispersion function.  The shift is
  computed in user coordinates for the fundamental order.  Shifts for
  each order are given by scaling of this shift.
  <P>
  In addition to the single keystroke commands there are commands
  initiated by the key <TT>':'</TT> (colon commands).  As with the keystroke
  commands there are a number of standard graphics features available
  begining with "<TT>:.</TT>" (type "<TT>:.help</TT>" for these commands).  The colon
  commands allow the task parameter values to be listed and to be reset
  within the task.  A parameter is listed by typing its name.  The colon
  command "<TT>:show</TT>" lists all the parameters.  A parameter value is reset
  by typing the parameter name followed by the new value; for example
  "<TT>:match 10</TT>".  Other colon commands display the feature list
  (:features), control reading and writing records to the database (:read
  and :write), and set the graph display format.
  <P>
  The feature identification process for an image is completed by typing
  <TT>'q'</TT> to quit.  Attempting to quit an image without explicitly recording
  changes in the feature database produces a warning message and an
  opportunity to record the information in the database.  As an immediate
  exit the <TT>'I'</TT> interrupt key may be used.  This does not save the feature
  information.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Echelle dispersion function fitting</H3>
  <! BeginSection: 'ECHELLE DISPERSION FUNCTION FITTING'>
  <UL>
  If a minimum of four features over at least two orders, depending on
  the default function orders, have been identified a dispersion function
  relating the user coordinates to the extracted pixel coordinate and
  aperture number may be fit.  However, more features are preferable to
  determine changes in the dispersion as a function of position and
  order.
  <P>
  The form of the function fit explicitly includes the basic order number
  dependence of echelle spectra; namely the wavelength of a particular
  point along the dispersion direction in different orders varies as the
  reciprocal of the order number.  Because of distortions, the differing
  extraction paths through the two dimensional image, and rotations of
  the spectra relative to the axis of constant dispersion (i.e. aligning
  the orders with the image columns or lines instead of aligning the
  emission and absorption features) there will be residual dependancies on
  the extracted pixel positions and orders.  These residual dependancies
  are fit by a two dimensional polynomial of arbitrary order including
  cross terms.  Because the basic order number dependence has been
  removed the orders should be relatively low.  Currently the functions
  are bi-dimensional chebyshev and legendre polynomials though other
  function may be added in the future.
  <P>
  Since the true order number may not be known initially a linear
  relation between the aperture numbers and the order numbers is also
  determined which minimizes the residuals.  This relation allows an
  unknown offset and possible a reversed direction of increasing order.
  The fitted function is then represented as:
  <P>
  <PRE>
  		y = offset +/- aperture
  <P>
  		wavelength = f (x, y) / y
  </PRE>
  <P>
  where y is the order number and x is the extracted pixel coordinate along the
  dispersion.
   
  If the order offset is known initially or as a result of previous the <TT>'o'</TT>
  fit may be used.  The dispersion minimization for the order offset is
  then not done.  This will, therefore, be faster than using the full
  fit, key <TT>'f'</TT>, to also determine the order offset.
  <P>
  The fitting is done interactively as a submode of <B>ecidentify</B> with its
  own set of cursor commands.  It is entered using the <TT>'f'</TT> key and exited using
  the <TT>'q'</TT> key.  The list of commands is given the CURSOR KEY section and is
  available from the fitting mode with <TT>'?'</TT>.  The functionality of this fitting
  is fairly simple; the function and orders may be changed, points may be deleted
  and undeleted, and the results of the fit may be displayed in various formats
  by selecting quantities to be plotted along either axis.  Generally one
  changes plotting of the pixel coordinate, order number, and wavelength
  along the x axis and residuals or radial velocity errors along the y axis.
  One switches between increasing the x order and the y order while switching
  between plotting verses x positions and order number until the residuals
  have been reduced to remove all systematic trends.
  </UL>
  <! EndSection:   'ECHELLE DISPERSION FUNCTION FITTING'>
  <H3>Database records</H3>
  <! BeginSection: 'DATABASE RECORDS'>
  <UL>
  The database specified by the parameter <I>database</I> is a directory of
  simple text files.  The text files have names beginning with 'ec' followed
  by the entry name, usually the name of the image.  The database text files
  consist of a number of records.  A record begins with a line starting with the
  keyword "<TT>begin</TT>".  The rest of the line is the record identifier.  Records
  read and written by <B>ecidentify</B> have "<TT>ecidentify</TT>" as the first word of the
  identifier.  Following this is a name which may be specified following the
  "<TT>:read</TT>" or "<TT>:write</TT>" commands.  If no name is specified then the image name
  is used.  The lines following the record identifier contain
  the feature information and dispersion function coefficients.
  </UL>
  <! EndSection:   'DATABASE RECORDS'>
  <H3>Echelle dispersion functions</H3>
  <! BeginSection: 'ECHELLE DISPERSION FUNCTIONS'>
  <UL>
  The fitted echelle dispersion functions are evaluated as described in
  this section.  The basic equations are
  <P>
  <PRE>
      (1)  w = (f(x,o) + shift) / o
      (2)  o = ap * slope + offset
  </PRE>
  <P>
  where w is the wavelength, x is the pixel coordinate along the order, o is
  the order, and ap is the aperture number.  The database parameter "<TT>shift</TT>"
  provides a wavelength zero point shift and the parameters "<TT>slope</TT>" and
  "<TT>offset</TT>" provide the transformation between aperture number and order.
  Note that the function f(x,o) and the shift are in terms of first order
  wavelengths.
  <P>
  The database entries contain "<TT>parameter value</TT>" pairs.  This includes the
  parameters "<TT>shift</TT>", "<TT>offset</TT>", and "<TT>slope</TT>" defined above.  The default
  values for these if they are absent are 0, 0, and 1 respectively.  The
  "<TT>coefficients</TT>" parameter specifies the number of coefficients that follow
  and define the first order wavelength dispersion function.  The
  coefficients and functions are described below.
  <P>
  The numerical values following the "<TT>coefficients</TT>" parameter, shown in
  the order in which they appear, have the following meaning.
  <P>
  <PRE>
      type	Function type: 1=chebychev, 2=legendre
      xpow	Highest power of x
      opow	Highest power of o
      xterms	Type of cross terms: Always 1 for echelle functions
      xmin	Minimum x for normalization
      xmax	Maximum x for normalization
      omin	Minimum o for normalization
      omax	Maximum o for normalization
      Cmn		Coefficients: m=0-xpow, n=0-opow, m varies first
  </PRE>
  <P>
  The functions are evaluated by a sum over m and n up to the specified
  highest powers.
  <P>
  <PRE>
      (3)  f(x,o) = sum {Cmn * Pm * Pn}	m=0-xpow, n=0-opow
  </PRE>
  <P>
  The Cmn are the coefficients of the polynomial terms Pm and Pn which
  are defined as follows.
  <P>
  <PRE>
      Chebyshev:
  	xnorm = (2 * x - (xmax + xmin)) / (xmax - xmin)
  	P0 = 1.0
  	P1 = xnorm
  	Pm+1 = 2.0 * xnorm * Pm - Pm-1 
  <P>
  	onorm = (2 * o - (omax + omin)) / (omax - omin)
  	P0 = 1.0
  	P1 = onorm
  	Pn+1 = 2.0 * onorm * Pn - Pn-1 
  <P>
      Legendre:
  	xnorm = (2 * x - (xmax + xmin)) / (xmax - xmin)
  	P0 = 1.0
  	P1 = xnorm
  	Pm+1 = ((2m + 1) * xnorm * Pm - m * Pm-1)/ (m + 1)   
  <P>
  	onorm = (2 * o - (omax + omin)) / (omax - omin)
  	P0 = 1.0
  	P1 = onorm
  	Pn+1 = ((2n + 1) * onorm * Pn - n * Pn-1)/ (n + 1)   
  </PRE>
  <P>
  Note that the polynomial terms are obtained by first normalizing the x and
  o values to the range -1 to 1 and then iteratively evaluating them.
  </UL>
  <! EndSection:   'ECHELLE DISPERSION FUNCTIONS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  Because this task is interactive it is difficult to provide an actual
  example.  The following describes a typical usage on arc spectra.
  <P>
  	cl&gt; ecidentify arc1.ec,arc2.ec
  <P>
  <DL>
  <DT><B>(1)</B></DT>
  <! Sec='EXAMPLES' Level=0 Label='' Line='(1)'>
  <DD>The database is searched for an entry for arc1.ec.  None is found and
  the first order is plotted as a function of pixel coordinate.
  </DD>
  </DL>
  <DL>
  <DT><B>(2)</B></DT>
  <! Sec='EXAMPLES' Level=0 Label='' Line='(2)'>
  <DD>Using a line identification chart or vast experience one of the
  emission lines is identified and marked with the <TT>'m'</TT> key.  Using the
  cursor position a center is found by the centering algorithm.  The
  aperture number, pixel position, wavelength (which is currently the
  same as the pixel position), and a prompt for the true value with the
  default value INDEF is printed.  The true wavelength is typed in and the
  status line is redrawn with the information for the feature.
  </DD>
  </DL>
  <DL>
  <DT><B>(3)</B></DT>
  <! Sec='EXAMPLES' Level=0 Label='' Line='(3)'>
  <DD>The orders are changed with the <TT>'j'</TT>, <TT>'k'</TT>, or <TT>'o'</TT> key and further lines are
  identified with the <TT>'m'</TT> key.
  </DD>
  </DL>
  <DL>
  <DT><B>(4)</B></DT>
  <! Sec='EXAMPLES' Level=0 Label='' Line='(4)'>
  <DD>After a number of lines have been marked spanning the full range of the orders
  and pixel coordinates the key <TT>'l'</TT> is typed.  The program now fits a preliminary
  dispersion solution using the current function and function orders.  Using this
  function it examines each line in the line list and checks to see if there is
  an emission line at that point.  With many orders and lots of lines this may
  take some time.  After additional lines have been identified (up to
  <I>maxfeatures</I> lines) the function is refit.  Finally the current order
  is regraphed in user coordinates.
  </DD>
  </DL>
  <DL>
  <DT><B>(5)</B></DT>
  <! Sec='EXAMPLES' Level=0 Label='' Line='(5)'>
  <DD>Again we look at some orders and see if the automatic line identifications
  make sense.
  </DD>
  </DL>
  <DL>
  <DT><B>(6)</B></DT>
  <! Sec='EXAMPLES' Level=0 Label='' Line='(6)'>
  <DD>We next enter the dispersion function fitting mode with <TT>'f'</TT>.  A plot of the
  residuals vs. pixel position is drawn.  Some obvious misidentifications may
  be deleted with the <TT>'d'</TT> key.  One way to proceed with determining the
  function orders is to start at the lowest orders (xorder = 2 for linear
  and yorder = 1 for no order dependence beyond the basic dependence).  We then
  increase each order one at a time.  The x axis is changed between order
  number and pixel position using the <TT>'x'</TT> key to see the dependence on each
  dimension.  The orders are increased until there are no systematic trends
  apparent.  Normally the y order (for the aperture or order number dependence)
  is low such as 2 to 4 while the x order (for the dispersion direction) is
  whatever is needed to account for distortions.  Also one can prune deviant
  points with the <TT>'d'</TT> key.  Note that the order offset derived from the
  aperture number is given in the title block along with the RMS.  When done
  we exit with <TT>'q'</TT>.
  </DD>
  </DL>
  <DL>
  <DT><B>(7)</B></DT>
  <! Sec='EXAMPLES' Level=0 Label='' Line='(7)'>
  <DD>The new function fit is then evaluated for all orders and the current order
  is redrawn based on the new dispersion.  Note also that the status line
  information for the current feature has both the fitted wavelength and the
  user identified wavelength.  We can add or delete lines and iterate with the
  fitting until we are happy with the feature list and dispersion function.
  </DD>
  </DL>
  <DL>
  <DT><B>(8)</B></DT>
  <! Sec='EXAMPLES' Level=0 Label='' Line='(8)'>
  <DD>Typing <TT>'q'</TT> exits the graph and prints a query about saving the information
  in the database.  We answer yes to this query.  Note that information can
  also be saved while still in the graphics loop using "<TT>:write</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>(9)</B></DT>
  <! Sec='EXAMPLES' Level=0 Label='' Line='(9)'>
  <DD>The next image in the list is then graphed but the last dispersion solution
  and feature list is maintained.  If the shift is small for the new arc we
  type <TT>'a'</TT> <TT>'c'</TT> to recenter all the features.  This does not refit the dispersion
  automatically so we then do <TT>'f'</TT>.  Alternatively, we could use the <TT>'s'</TT> or <TT>'x'</TT>
  keys to determine a large shift and do the recentering.
  </DD>
  </DL>
  <DL>
  <DT><B>(10)</B></DT>
  <! Sec='EXAMPLES' Level=0 Label='' Line='(10)'>
  <DD>Finally we can exit with <TT>'q'</TT> or examine further images with the "<TT>:image</TT>"
  command.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>ECIDENTIFY V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='ECIDENTIFY' Line='ECIDENTIFY V2.11'>
  <DD>The dispersion units are now determined from a user parameter,
  the coordinate list, or the database entry.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  apsum, center1d, gtools, ecreidentify, identify
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'CURSOR KEYS' 'DESCRIPTION' 'ECHELLE DISPERSION FUNCTION FITTING' 'DATABASE RECORDS' 'ECHELLE DISPERSION FUNCTIONS' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
