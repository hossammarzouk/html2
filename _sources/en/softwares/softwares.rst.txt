.. _joblist_editor:

Softwares
===================

Job list Editor
--------------------------
The EDE job list editor is a windows program that allows the user to make a job list file meeting all the criteria required by the EDE unit. The program prevents any errors from the user
and will not submit any job unless it is compatible with the EDE

.. figure:: /images/joblist1.png
    :align: center

    User inerface of Job list editor

Steps tp creat a job list file:
1. Enter the Ex and Ey dipole lengths
2. Specify the sampling frequency
3. Select the desired start and stop time for the job
4. Press *submit job* button which writes the job parameters into the table view
5. Repeat steps 2:4 till you reach the desired number of jobs
6. Press the *Write Job File* button and select the :code:`MTDAT` partition of the EDE's SSD   

.. admonition:: Hint 
    
  All data in the table view are editable, which means the user can delete raws and edit cells after submitting jobs but be cautious because no error checking here! 


TS plotter
----------------------------

TS plotter is available for Windows64 and MacOs machines. It is a simple program to quickly view the recorded electric field vs the sample counter of one run. Simply drag and drop the measurements run folder to the program 
and it will read all data and plot it. The user can choose to plot one file or all the files from top menu.

.. figure:: /images/tsplotter1.png
    :align: center

    User inerface of TS plotter