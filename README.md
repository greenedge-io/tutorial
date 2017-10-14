# Tutorial: How to use FoG API in TensorFlow

This tutorial describes the use of FoG, the distributed GPU computing platform from greenedge.io.

We have modified a publicly [avaliable](https://agray3.github.io/2016/11/29/Demystifying-Data-Input-to-TensorFlow-for-Deep-Learning.html) TensorFlow based training [example](https://agray3.github.io/files/shapesorter.py) such that it could be run on our platform.

There are few requirements that need to be adhered by the main Python script that is uploaded to the fog.greenedge.io website:

* archive (example zip) all other Python scripts (referenced by the main Python script), data and parameter files

* upload the archive to a file sharing webhost (example: Dropbox, Google Drive, your own webserver)

* Download and extract the archive from the main Python script

* in case you want to save the output in binary format, zip it and upload it using FoG API.

FoG allows you to upload your output to Google Drive. In addition, we automatically save `stdout` and `stderr` to Drive as `out.log` and `err.log`, respectively. To upload a file from your Python script, just call:
```
from google_drive import upload_file
...
upload_file(file_name)
``` 

For more clarity, you can follow the example script provided. The script was modified by adding three main functions:

* `download_zip(url)`: given the URL of the zip (archive) file, this method downloads the file using the requests library provided by Python. 

* `extract_zip(file_path, directory_path=".")`: given the path to a zip file (file_path) this method extracts the zip archive to a given directory (directory_path). if no directory path (directory_path) is given the extraction will be done in the current directory

* `create_zip(zip_name, files)`: creates a zip from a list of files.

Before the execution of the training we simply used the first two methods to download the data needed for the script. At the end, we save the model and create a zip file with model output files. You can read more about saving and restoring a model in TensorFlow here: https://www.tensorflow.org/programmers_guide/saved_model. 

Once the program completes execution you could save any other file you need. It is preferable to have the file in the same working directory. Once the file is written, simply call `upload_function(file_name)` in your Python script. We will be placing a Python script in your working directory that has the `upload_function(file_name)` already implemented.

You would get a Google Drive link on your web console once your program has completed execution. Use that link to access the files you uploaded. You would
also get two files that show the standard output and standard error.

Please note that if you are using a Dropbox link, you have to modify the link as bellow:

original link provided: `https://www.dropbox.com/[something]/[filename]?dl=0`

change the link to `https://www.dropbox.com/[something]/[filename]?dl=1` (chane `dl=0` to `dl=1`)

### Thank you for joining FoG community!

