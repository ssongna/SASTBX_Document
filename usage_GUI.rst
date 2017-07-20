GUI Document
=======================

Download the GUI Version

 .. image:: picture/molecule.png
 	:height: 100px
	:width: 100 px
	:scale: 50 %
	
Open the Application by double clicking the icons above.

Project Location
-------------------

Set the project directory in the homepage:

 .. image:: picture/project_location.png
	:scale: 40 %

All the result will located in the directory you selected, and for each function, there will generate a subdirectory with the same name of the project.

Preference
--------------

*For light GUi version*
Set SASTBX location, a directory contain module and build directory of SASTBX

Set the pymol location in the preference page.

 .. image:: picture/preference_light.png
	:scale: 40 %

*For complete GUI version*
Set the pymol location in the preference page.

 .. image:: picture/preference_complete.png
 	:scale: 40 %

*Note:*

* pymol path: 

 the path of MacPymol application or the pymol executable file.
 
* SASTBX path:

 the directory which contains the source code directory named “modules” and compile directory named “build”.

Here are some examples of pymol path: ::

 	/Applications/MacPymol.app

 	/usr/bin/pymol

The example of SASTBX path: ::

 	/Applications/SASTBX/

Functions
-----------------

After setting the project location and the preference, you can begin to use the funciton you need. The following part will introduce how to use these funcions in GUI version.

Model Superposition
>>>>>>>>>>>>>>>>>>>>>>>>>>

Superpose models at low resolutions.
The required inputs are 2 protein models or maps, all the other parameters are optional.

 .. image:: picture/superpose_input.png
  :scale: 40 %

The the program will start with clicking 'run' button.
And the log can be seen in the widget.

 .. image:: picture/superpose_log.png
 	:scale: 40 %

The result can be seen in the result tab:

 .. image:: picture/superpose_result.png
 	:scale: 40 %

You can explore the content of each result file by seen the content or show in pymol.

 .. image:: picture/superpose_show.png
	:scale: 30 %

You can seen the superpose result by click “pymol” button in the toolbar.

 .. image:: picture/superpose_result_show.png
	:scale: 30 %

Two protein are superposed.

Shape Search Engine
>>>>>>>>>>>>>>>>>>>>>>>>>>

Fast retrieval 3D models for the given says experimental profile.

The instruction tab explain every parameters of the input tab.

 .. image:: picture/shapeup_introduction.png
	:scale: 40 %

Input the file and parameters:

 .. image:: picture/shapeup_input.png
	:scale: 40 %

The the program will start with clicking 'run' button.
And the log can be seen in the widget.

 .. image:: picture/shapeup_log.png
	:scale: 40 %

The result can be seen in the result tab:

 .. image:: picture/shapeup_result.png
	:scale: 40 %

These 10 maps are the best results that match the input SAXS file in the database.

You can explore the content of each result file by looking through the content or show it in pymol.

 .. image:: picture/shapeup_result_click.png
	:scale: 40 %

You can seen the result by click “pymol” button in the toolbar.

 .. image:: picture/shapeup_result_pymol.png
	:scale: 40 %

Intensity Calculation
>>>>>>>>>>>>>>>>>>>>>>>>>>

Compute theoretical scattering intensity curve for the given PDB models.
The instruction tab explain every parameters of the input tab.

 .. image:: picture/she_introduction.png
	:scale: 40 %

Input the file and parameters:

 .. image:: picture/she_input.png
	:scale: 40 %

The real time log file:

 .. image:: picture/she_log.png
	:scale: 40 %

The intensity curve can be seen in the summary tab:

 .. image:: picture/she_curve.png
	:scale: 40 %

P(r) Estimation
>>>>>>>>>>>>>>>>>>>

Using Parametic Formula to determinate the pair distance distribution function of saxs file.

The input parameters:

 .. image:: picture/pr_input.png
	:scale: 40 %

The real time log file:

 .. image:: picture/pr_log.png
	:scale: 40 %

The pair distance curve can be seen in the summary tab:

 .. image:: picture/pr_curve_1.png
	:scale: 40 %

The original intensity curve of saxs file and the best intensity file curve:

 .. image:: picture/pr_curve_2.png
	:scale: 40 %

Get Help
-------------
You can get help of the principle of each function and the tutorial of how to use the application whenever you click the help button:

 .. image:: picture/help.png
	:scale: 20 %

And you can see:

 .. image:: picture/help_main.png
	:scale: 40 %

The SASTBX Functions link:

  .. image:: picture/help_function.png
	:scale: 40 %

shows the principle of each function.

The Tutorial and Examples link:

 .. image:: picture/help_tu.png
	:scale: 40 %









 
















