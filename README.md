EiffelStudio Debian package
===========================



Building the package
--------------------

  * I use Linux Ubuntu to build the package.
  * First download the EiffelStudio PorterPackage from http://sourceforge.net/projects/eiffelstudio/files/ .
  * Install packages packaging-dev and dh-make
  * Be sure that the Bazaar (command bzr) is correctly set. See: http://packaging.ubuntu.com/html/getting-set-up.html .
  * Use the following command line to build :

***

	bzr dh-make eiffelstudio15.12 15.12.9.8308 PorterPackage_15.12_98308.tar # Using "m" for multiple binary
	cp -rp debian/* eiffelstudio15.12/debian/
	cp -rp patches eiffelstudio15.12/
	bzr add eiffelstudio15.12/patches
	cd eiffelstudio15.12/debian
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
	dput ppa:eiffelstudio-team/ppa eiffelstudio15.12_15.12.9.8308-0ubuntu1~trusty1_source.changes

***

