***

	equivs-build --full ns-control
	dpkg-source -x eiffelstudio_*.dsc
	cp -p changelog eiffelstudio-*/debian
	cd eiffelstudio-*
	debuild -S # Change the changelog file to send in another series (precise, trusty, etc.)
	cd ..
	dput ppa:eiffelstudio-team/ppa eiffelstudio_18.01-0ubuntu1~trusty1_source.changes

***
