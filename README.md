EiffelStudio Debian package
===========================



Building the package
--------------------

  * I use Linux Ubuntu to build the package.
  * First download the EiffelStudio PorterPackage from http://sourceforge.net/projects/eiffelstudio/files/ .
  * Install packages packaging-dev and dh-make
  * Be sure that the Bazaar (command bzr) is correctly set. See http://developer.ubuntu.com/packaging/html/getting-set-up.html#configure-bazaar .
  * Use the following command line to build :

***

	bzr dh-make eiffelstudio14.05 14.05.9.5220 PorterPackage_14.05_95220_gpl.tar # Using "m" for multiple binary
	cp -rp debian/* eiffelstudio14.05/debian/
	cp -rp patches eiffelstudio14.05/
	bzr add eiffelstudio14.05/patches
	cd eiffelstudio14.05/debian
	rm *.ex *.EX
	bzr add postinst
	bzr add prerm
	bzr builddeb -- -us -uc

***

To send to PPA
--------------

***

	bzr builddeb -S # Changing the changelog file to send in another series (precise, trusty, etc.)
	cd ../../build-area
	dput ppa:eiffelstudio-team/ppa eiffelstudio14.05_14.05.9.5220-0ubuntu1~trusty1_source.changes

***

