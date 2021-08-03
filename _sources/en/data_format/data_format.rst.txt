Data format description
============================
This section describes the directory structure of the EDE SSD and the format of the binary data.

Directory structure
----------------------

The SSD attached to EDE unit are a 128 GigaBytes drive with two partitions.
Only 32 GigaBytes of this SSD is used for storage in partition named :code:`MTDAT` and the other unused partition is named :code:`SCRATCH`.

.. figure:: /images/dir1.png
    :align: center

    Example of  SSD partitions names

The data is stored in the root directory of the :code:`MTDAT` partition as will as two config files. 
The first file :code:`auto_init.cfg` is used for suppling the job list in automatic mode. While the file :code:`init.cfg` contaons
the last used configuration (frequency, Ex dipole and Ey dipole) in Manual mode.

.. figure:: /images/dir2.png
    :align: center

    Example of root directory structure

Each recording directory contains one header file, kml file contains the location alongside the data from one continuous run. 
The data is distributed among equally time range files depending of the sampling frequency 
i.e. in a 256 Hz run one file holds the data from one hour and in a 64 Hz run one files holds the data from 24 hours recording.  

.. figure:: /images/dir3.png
    :align: center

    Example of header and data files inside one run folder

--------------------------------------------------

Header file
--------------------

.. warning:: 
    
   The following tuturial has been carried out using *VERSION: Apr 12 2021*. May looks slightly different in other versions.

The following is an example of the header file containing all the recording parameters for each run.

.. code:: c++

 EDE: 115
 VERSION: Apr 12 2021
 TYPE: E
 SAMPLECOUNTER: 1
 LSB: 1.164153218e-6 mV
 GAIN: 10 
 LP: 1
 
 LONGITUDE: 650.414612
 LATITUDE: 5211.215332
 SYSTEMSTARTTIME: 18 46 22
 SYSTEMSTARTDATE: 2021 07 14
 PPSDELAY: 46 us
 SAMPLERATE: 256
 Ex: 59.5 m
 Ey: 54.5 m
 STARTTIME: 18 48 00 000
 STARTDATE: 14 07 2021
 STOPTIME: 09 06 16 000
 STOPDATE: 16 07 2021 
 STOPFILENUMBER: 010
 NSAMPLES: 35301376 


--------------------


Data file
------------------
The data files are stored in a binary format with the extension :code:`.ets` (EDE time seires). The binary file structure contains no header bytes and the EDE stores three values at each sample.
 -  **Sample Counter** as int32    
 -  **Ex** as int32
 -  **Ey** as int32
  
To get the measured data in mV, the values in the binary file must be multiplied by the *LSB* and divided by the *Gain* from the header file.

.. figure:: /images/dir4.png
    :align: center

    Example of data file structure