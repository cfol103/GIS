# Geographic Information System (GIS)

This java program implements a Geographic Information System (GIS)
that stores the location of a geographic feature along with its other attributes.  The input to the system is a GIS record obtained from a 
website like the the USGS Board on Geographic Names (geonames.usgs.gov).

# Features
This system indexes and provides search features for multiple GIS
records. Additionally, this project includes my implementation of several 
in-memory index data structures that allow for:
* Importing new GIS records into the database file
* Retrieving data for all GIS records matching given geographic coordinates
* Retrieving data for all GIS records matching a given feature name and state
* Retrieving data for all GIS records that fall within a given (rectangular) geographic region
* Displaying the in-memory indices in a human-readable manner

# Operating the GIS program

The java program can be run from the command line with three arguments: a database file name, a command script file name, and a log file name.  The database file will store the records in the GIS format , the command script file is the user commands to query the database, and the log file will store the results of the user commands.

The program will take the names of three files from the command line, like this: 
java GIS <database file name> <command script file name> <log file name>


# Data Structures

Seeing as the GIS works with record files that contain many data points that correspond to hundreds of different locations, I have provided my own implementation of a few data-structures to improve performance.

* Hash-Table
My implementation of a hash-table will be used for the name index where 
the GIS records will be indexed by the Feature Name and State (abbreviation) fields. This name index will support finding offsets of GIS records that match a given feature name and state abbreviation.
* Buffer-Pool
My implementation of a Buffer-Pool is capable of buffering up to 20 records and will use a LRU replacement strategy in order to improve performance.

# Command File

* The commands that this sytem can process are outlined below:

world<tab><westLong><tab><eastLong><tab><southLat><tab><northLat>
what_is_in<tab>-l<tab><geographic coordinate><tab><half-height><tab><half-width>