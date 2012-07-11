witty-codegen
=============

A code generator tool for building Witty C++ web apps: http://webtoolkit.eu

Todo:

 + See what else is out there, check out:
   + http://sourceforge.net/projects/proghelp/
   + http://pypi.python.org/pypi/locales-test/1.4.0

 + Decide on use of c++11:
   + Use gcc 4.7.1 compat c++11 and ignore other compilers
         - faster to code, not so socially nice, but could be converted to support
         - others later by people who care
   + Stick with c++98 - Should run on anyone's computer
   + Support both through compiler pre-processing - more work
 + Decide on a project template layout. I like it something like this:
   + myproject/
     + src/
       + main.cpp
       + MainWindow.hpp
       + MainWindow.cpp
       + App.hpp
       + App.cpp
       + db/
         + User.cpp
     + messages/
       + common.xml
       + MainWindow.xml
     + static/
       + images/
         + (all default wt images go here)
       + css/
         + (all default wt css goes here)
       + js/
         + (all default wt js goes here, including the editor source)
     + etc/
       + wt-config.xml
     + resources/
       + Any other files that the app needs to run, but aren't served go here
 
 + Decide on and add features:
   + Definite Features:
     + New Project - asks  for the app name and stuff, generates you a main.cpp,
                   - a MainWindow.?pp CMakeLists.txt, and builds and runs it for you,
                   - so you can get into witty quickly.
     + Gen tests   - Creates a tests dir, CMakeLists file (with a nice 'addTest'
                   - function that you can use), and an initial test using boost
                   - test framework
     + Gen DB      - Generates a db directory, CMakeLists.txt, and a User model,
                   - and source code for a DB reset/repopulate util app
     + reset DB    - compiles and runs the app from the line above

   + Up for discussion:
     + Gen Form    - Parses a model source file, and generates a form for it,
                   - just choosing the simplest widgets it can.
     + Sync messages - This scans the 'messages' folder and the C++ code for
                     - translation messages (WString::tr) and assists in
                     - adding to xml files strings found in the code
                     - removing from xml files strings not found in the code
     + Gen Auth      - Generates auth files that just does password auth,
                     - or possibly allows different forms of auth
     + Make Deploy  - Builds a .tgz package ready for deployment, can be
                    - extracted to / on a server or used to make .deb or .rpm
                    - etc.
     + nginx        - Generates an nginx config file to proxy to your app
                    - and to serve the static files straight out
     + ha-proxy     - Generates an ha-proxy config file for your app
