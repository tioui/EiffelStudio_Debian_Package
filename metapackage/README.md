***

	mkdir source
	tar cvfz eiffelstudio_19.05.orig.tar.gz source
	equivs-build --full ns-control
	dpkg-source -x eiffelstudio_*.dsc
	cp -p changelog eiffelstudio-*/debian
	cd eiffelstudio-*
	debuild -S # Change the changelog file to send in another series (precise, trusty, etc.)
	cd ..
	dput ppa:eiffelstudio-team/ppa eiffelstudio_19.05-0ubuntu1~xenial1_source.changes

***
