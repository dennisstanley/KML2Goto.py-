# KML2Goto.py-
python script for converting paths created in google earth or OpenCPN into files used by slocum ocean gliders for navigation 
the initial implementation as it stands is used by me to generate files for University of Western Australia's fleet of slocum gliders and hence
works on my specific piloting directory structure although the code should be well commented enough that a new user
can adapt it to their structure

A weakness in the code is that its not very robust in handing the kml in terms of locating the contents of the "linestring" a linestring is a data structure in the kml that contains a series of 3 dimentional points (lat,Long,elevation) which, for the basis of the glider path, one is 
wishing to decode. this code just takes the last element in the KML as the linestring because that just happens to be in common between KML's generated by google earth and OpenCPN. this could be done in a more robust way

secondly runtime configuration (source file destination file etc) is done through asking the user for input. if you wish to make the script machine callable
then it may be better to implement this through the use of command line arguments

the procedure for creating a KML from an OpenCPN path is to; 1 create the path in open cpn 2. select the path by highlighting it (hover over and right click) 3. copy KML (to clipboard) 4. select standard KML when asked (now you have the contents of the desired KMLfile on the clipboard) 5. use a text editor to create (or modify the existing contents of) an arbitary text file. You then direct the python script to this text file. The default text file is “goto.kml” your file, or if you use the default, must be reachable in the path where you run the script from 

the default directory structure I use for piloting is

desktop/piloting/000   #default glider directory
                 /209
                 /210
                 /xxx    #other gliders 
                 /Python  #this directory holds the script and the source goto.kml file  


I have, on purpose, written the script such that the relevant glider directory  MUST EXIST for the script to access it it (ie it will not create a new glider directory) this is to prevent typo’s going unnoticed. 
