Installation
===============
* **Complete GUI version**
	No installation required.
* **Light GUI version**
 	Required command line version SASTBX has been exist on your machine.
* **command line version**
 	No installation required.
* **source code**
 	If you want to manually compile the command line version software form source code. The installation is required. (For developers who add the new command or change the C++ code. The changes in python script can take effect immediately when executing.)


Manually compile from source code on Ubuntu
--------------------------------------------
*Attention:
For developers who add the new command or change the C++ code, manually compiling is necessary.
For developers who only change the  python script, recommend you using command version without compiling.*

soure code can be downloaded on http://liulab.csrc.ac.cn/dokuwiki/doku.php?id=sastbx


*In the flowing procedure, the lines that are in the block are what you will type in command line.*

* **step1  Unpack the compressed SASTBX file** ::

	tar -xjvf source_code_ubuntu.tar.gz 

* **step2  Configure the environment variables** 

 The installation procedure should be executed in another directory, so make an empty directory to execute the installation. ::

	cd SASTBX_PATH/
	mkdir build

 Recommend you organize the directory like this: ::

	SASTBX_PATH(the directory saved source code and executed space)
    	* build
    	* modules

 *Attention :* ::

	SASTBX_PATH
 
 is the path where the sastbx file exit, change it to your own path

 *example:* ::

 	cd /usr/test/Documents/software/sastbx/build

 ``usr/test/Documents/software/sastbx``  is the *SASTBX_PATH* in the example
 
 Then generate the environment variables: ::

 	/your/choice/bin/python ../modules/libtbx/configure.py sastbx

 A list of files will generate in build directory Then configure the environment variables. Then make the environment variables take effect.
 To compiler enter: ::

 	make
 
 If you want to use multiple CPUs, you can specify the number of CPU, for example, enter: ::

 	make -j 4
 
* **step3: vertify**

 Type: ::

 	sastbx.python
 
 in the command line, if you can enter the python process, the installation is success.


Manually building from sources under MacOS
--------------------------------------------
*Attention:
For developers who add the new command or change the C++ code, manually compiling is necessary.
For developers who only change the  python script, recommend you using command version without compiling.*

soure code can be downloaded on http://liulab.csrc.ac.cn/dokuwiki/doku.php?id=sastbx

*In the flowing procedure, the lines that are in the block are what you will type in command line.*

* **step1  Unpack the compressed SASTBX file** ::

	tar -xjvf source_code_ubuntu.tar.gz 

* **step2  Configure the environment variables** 

 The installation procedure should be executed in another directory, so make an empty directory to execute the installation. ::

	cd SASTBX_PATH/
	mkdir build

 Recommend you organize the directory like this: ::

	SASTBX_PATH(the directory saved source code and executed space)
    	* build
    	* modules

 *Attention :* ::

	SASTBX_PATH
 
 is the path where the sastbx file exit, change it to your own path

 *example:* ::

 	cd /usr/test/Documents/software/sastbx/build

 ``usr/test/Documents/software/sastbx``  is the *SASTBX_PATH* in the example

 Then generate the environment variables: ::

 	/your/choice/bin/python ../modules/cctbx_project/libtbx/configure.py sastbx

 A list of files will generate in build directory Then configure the environment variables. Then make the environment variables take effect.
 To compiler enter: ::

 	make
 
 If you want to use multiple CPUs, you can specify the number of CPU, for example, enter: ::

 	make -j 4

* **step3: vertify**

 Type: ::

 	sastbx.python
 
 in the command line, if you can enter the python process, the installation is success.










 


 

