# tutorial

This tutorial describes the use of the distributed GPU compute platform.

We have modified a publicly [avaliable](https://agray3.github.io/2016/11/29/Demystifying-Data-Input-to-TensorFlow-for-Deep-Learning.html) tensor flow based training [example](https://agray3.github.io/files/shapesorter.py) such that it could run on our platform. 

There are few requirements that needs to be adhered by the main python script that is uploaded to the greenedge.io website. 

* archive (example zip) all other python scripts (referenced by the main python script), data and parameter files

* upload the archive to a file sharing webhost (example: Dropbox, Google Drive, Your own webserver)

* Download and extract the archive from the main python script

For more clarity you could follow the example script provided.

The script was modified with two main functions

* download_zip(url): given the URL of the zip (archive) file, this method downloads the file using the requests library provided by python. 

* extract_zip(file_path, directory_path="."): given the path to a zip file (file_path) this method extracts the zip archive to a given directory (directory_path). if no directory path (directory_path) is given the extraction will be done in the current directory

Before the execution of the training we simply used these two methods to download the data needed for the script. 

Please not that if you are using a dropbox link to modify the link as given below.

original link provided: "https://www.dropbox.com/[something]/[filename]?dl=0"

change "dl=0" to "dl=1"

modification: "https://www.dropbox.com/[something]/[filename]?dl=1" 












