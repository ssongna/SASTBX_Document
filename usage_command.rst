Command Line Document
==============================

Using SASTBX with console.


List of command line
---------------------------

+---------------------------+---------------------------+----------------------------------+
|     Command Line          | Command Line              |  Command Line                    |
+===========================+===========================+==================================+
|  sastbx.superpose         | sastbx.collect_c2_results |  sastbx.generate_c2_parameters   |
+---------------------------+---------------------------+----------------------------------+
| sastbx.build_db           |  sastbx.fit_c2            |  sastbx.gpu_c2                   |              
+---------------------------+---------------------------+----------------------------------+
|   sastbx.buildmap         | sastbx.fxs_she            |  sastbx.image_simulator          |
+---------------------------+---------------------------+----------------------------------+ 
| sastbx.build_lookup_table | sastbx.fxs_znk            | sastbx.pr                        |
+---------------------------+---------------------------+----------------------------------+
|  sastbx.pregxs            |  sastbx.python            | sastbx.refine_i                  |
+---------------------------+---------------------------+----------------------------------+
|   sastbx.refine_pr        |   sastbx.refine_rb        |     sastbx.retrieval             |
+---------------------------+---------------------------+----------------------------------+
|   sastbx.run_c2_jobs      |    sastbx.sdp             |      sastbx.shapeup              |
+---------------------------+---------------------------+----------------------------------+
| sastbx.she                |   sastbx.show_build_path  |      sastbx.show_dist_paths      |
+---------------------------+---------------------------+----------------------------------+


Intensity Calculation (sastbx.she)
-----------------------------------

Obtain one-dimensional scattering curves of intensity versus scattering vector (I-q curves) from protein models.

Usage: ::

	sastbx.she model=mymodel structure=mystructure.pdb 
		experimental_data=myexperimentaldata.qis  
		pdblist=pdblist.txt  q_start=q_start q_stop=q_stop n_step=n_step output=outputfile

	Required arguments:
	 mystructure             the PDB file to be evaluated (must be provided)
 	Optional arguments:
	    mymodel                   default she        
	                              the model type to be used, it should be either debye or she 
	    myexperimentaldata.qis    default None       
	                              the sas profile, columns are q, I(q), and std
	    q_start                   default 0          
	                              start of Q array
	    q_stop                    default 0.5        
	                              end of Q arry
	    n_step                    defalut 51         
	                              Bin size 
	    outputfile                default output.iq  
	                              the file used to store computed sas profile and could be overwritten

*examples:* ::
	
	sastbx.she structure=/usr/test/Documents/mystructure.pdb
	sastbx.she structure=/usr/test/Documents/mystructure.pdb output=/usr/test/Documents/mystructure_she.iq

change the the file path `/usr/test/Documents/mystructure.pdb` to your own file path


P(r) Estimation(sastbx.pregxs)
----------------------------------

Pair-distance distribution function determination

Usage: ::

	sastbx.pregxs data=data_file d_max=dmax scan=True/False output=output_prefix

parameters: ::

	required arguments:
    	data      q-intensity sigma
	Optional arguments:
	    d_max     default None                  Maximun distance in particle
	    scan      default False                 When True, a dmax scan will be preformed
	    output    default best.pr best.qii    

Model Superposition(sastbx.superpose)
-----------------------------------------

Align models.

Usage: ::

	sastbx.superpose fix=fixed_file typef=type [pdb | nlm | map ] mov=moving_file typem=type nmax=nmax

parameters: ::

	required arguments:
     fix      default  None    pickle Cnlm coef of the fixed object
     mov      default  None    pickle Cnlm coef of the moving object
	optional arguments:
	 
	 typef     default PDB      fixed model type: pdb or nlm or map
	   
	 typem     default PDB      moving model type: pdb or nlm or map 
	 
	 num_grid  default 41       number of point in each euler angle dimension
	 rmax      default None     maxium radial distance to the C.o.M. (before the scaling)
	 nmax      default 20       maximum order of zernike polynomial:fixed for the existing database
	 topn      default 10       top N alignments will be further refined if required
	 refine    default True     Refine the initial alignments or not
	 write_map default False    write xplor map to file

example: ::

	sastbx.superpose fix=a.pdb mov=b.pdb


Generate Database(sastbx.build_db)
------------------------------------

Creat database with a directory of PDB files.

Build your own database The default database used in the software is compiled using this script based on 10,733 models chosen from PISA

Usage: ::

	sastbx.python build_db.py path=path nmax=nmax fix_dx=True/False

parameters: ::
	path           default None          path of pdb files
	nmax           default 20            maximum order of zernike expansion
	fix_dx         default True          Whether keeping default dx=0.7A or not
	np             default 50            number of point covering [0,1]
	nprocess   	   default 4             number of processes
	prefix         defualt myDB      	 the prefix of pickle file names


*Attention:*
The *path* should be a directory that contains **only PDB files**.


examples:

For example, if there is a directory named pdb_models which contains 3D models in pdb format, and now I want to generate a database for these models. If I want the data to be stored in the database directory ( suppose that both the directories are in `/usr/test/Documents/`) and nmax=30, then I will write a command like this: ::
	
	sastbx.python path=/usr/test/Documents/pdb_models nmax=30

*result* ::
	
	myDB.codes 
	myDB.nlm 
	myDB.nn 
	myDB.rmax

or if you want to name the return files as “models”, then you can enter: ::

	sastbx.python build_db.py path=/usr/test/Documents/pdb_models prefix=/usr/test/Desktop/database/models

*result:* ::
	
	models.codes 
	models.nlm 
	models.nn 
	models.rmax

* .codes file records the PDB file’s name used in the database genetation.
* .nlm file records the Zernike moments coeffcients.
* .nn file recoed the Hnn coeffcients.
* .rmax file contains the largest radius of each structure.

Data stored in these files are all in list format, and information for a specific model can be accessed with the same index.

Shape Search Engine(sastbx.shapeup)
-------------------------------------

Fast Retrieve 3D models for the given saxs experimental profile within 1 minite.

Usage: ::
	
	sastbx.shapeup target=myquery.dat rmax=estimated_rmax dbpath=path_of_database

Parameters: ::

	required arguments:
    	target    the intensity profile
	optional arguments:
	    rmax      default guessed from Rg    
	              radius of the molecule (default: guessed from Rg)
	    nmax      default 10                 
	              maximum order of the zernike polynomial expansion (<=20 for precomputed database)
	    qmax      default 0.20               
	              maximum q value, beyond which the intensity profile will not be considered 
	    path      default None               
	              path to the database (this MUST be correct to execute the searching)
	    buildmap  default True               
	              build electron density map in xplor format, all the map will be aligned
	    pdb       default None               
	              any pdb model to be compared, and the maps will be aligned to the first pdb file
	    prefix    the output prefix

returns:
The atomic models match the SAS profile (default 10 models in ccp4 format) You can observe the models in pymol.

If you creat a database by using sastbx.build_db, you can search with the new database: ::
	
	sastbx.shapeup target=myquery.dat rmax=estimated_rmax dbpath=path_of_database
















