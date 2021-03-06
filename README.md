# Data Transfer
A tutorial about data transfer with OLCF systems

Usually, a user wants to transfer data either between the OLCF systems, either to our archive system or from another source outside. We are going to present how to use Globus to transfer files, options to use Globus if your organization does not provide Globus and how to use tools for our archiving system, HPSS

## Globus

Globus provides a secure, unified interface to your research data. Use Globus to start high-performance data transfers between systems within and across organizations while there is no need to be available until the transfer ends.

* Visit the web page https://www.globus.org and click on the login button

<div style="text-align:center"><img src="https://github.com/olcf-tutorials/Data_Transfer/blob/master/figures/globus_first_page.png?raw=true" width="65%"/></div>

* If you organization is in your list, please choose it. This is the organization that you belong, not the one that you are using the resources.

<div style="text-align:center"><img src="https://github.com/olcf-tutorials/Data_Transfer/blob/master/figures/choose_organization.png?raw=true" width="65%"/></div>

* Use your credential to logins (it depends on the institution that you work for). IF AND ONLY IF your organization is not the list and you still want to use Globus, then install it on a system and declare an endpoint, use the instructions from https://www.globus.org/globus-connect-personal

<div style="text-align:center"><img src="https://github.com/olcf-tutorials/Data_Transfer/blob/master/figures/credentials.png?raw=true" width="55%"/></div>


* Search for the OLCF DTN endpoint

<div style="text-align:center"><img src="https://github.com/olcf-tutorials/Data_Transfer/blob/master/figures/search_endpoint.png?raw=true" width="75%"/></div>


<div style="text-align:center"><img src="https://github.com/olcf-tutorials/Data_Transfer/blob/master/figures/search_endpoint2.png?raw=true" width="75%"/></div>

* Declare the path

<div style="text-align:center"><img src="https://github.com/olcf-tutorials/Data_Transfer/blob/master/figures/declare_path1.png?raw=true" width="75%"/></div>

<div style="text-align:center"><img src="https://github.com/olcf-tutorials/Data_Transfer/blob/master/figures/declare_path2.png?raw=true" width="75%"/></div>

* Open a second panel to declare where your files would like to be transferred, select if you want an encrypt transfer, select your file/folder and click start

<div style="text-align:center"><img src="https://github.com/olcf-tutorials/Data_Transfer/blob/master/figures/panels.png?raw=true" width="75%"/></div>

<div style="text-align:center"><img src="https://github.com/olcf-tutorials/Data_Transfer/blob/master/figures/transfer_options.png?raw=true" width="75%"/></div>

<div style="text-align:center"><img src="https://github.com/olcf-tutorials/Data_Transfer/blob/master/figures/encrypt_start.png?raw=true" width="75%"/></div>

* Then an activity report will appear and you can click on it to see the status. When the transfer is finished or failed, you will receive an email

<div style="text-align:center"><img src="https://github.com/olcf-tutorials/Data_Transfer/blob/master/figures/activity1.png?raw=true" width="75%"/></div>

<div style="text-align:center"><img src="https://github.com/olcf-tutorials/Data_Transfer/blob/master/figures/activity2.png?raw=true" width="75%"/></div>

## HPSS with Globus

If you want to use the archiving system, HPSS with Globus, the only difference with above, is to declare a path on HPSS, and for example the archive of your project on HPSS, is under /proj/projid/username. Everythign else, as procedure is similar to above.

<div style="text-align:center"><img src="https://github.com/olcf-tutorials/Data_Transfer/blob/master/figures/globus_hpss_4_options.png?raw=true" width="75%"/></div>

## HPSS Tools

Currently, **HSI** and **HTAR** are offered for archiving data into HPSS or retrieving data from the HPSS archive. For better performance connect to DTN and execute the hsi/htar commands from there.

For optimal transfer performance, we recommend sending a file of 768 GB or larger to HPSS. The minimum file size that we recommend sending is 512 MB. HPSS will handle files between 0K and 512 MB, but write and read performance will be negatively affected. For files smaller than 512 MB we recommend bundling them with HTAR to achieve an archive file of at least 512 MB.

When retrieving data from a tar archive larger than 1 TB, we recommend that you pull only the files that you need rather than the full archive. Examples of this will be given in the htar section below.

On HPSS, we save generic files in /home/username and project related to /proj/projectid/username

Go to the hpss folder

```
cd hpss
```

### HSI

Examples of **hsi** command:

* List your files

```
hsi ls
```
* Put the fille **smallfile.txt** on HPSS

```
hsi put smallfile.txt
```

You will see in the output something like:
put  'smallfile.txt' : '/home/gmarkoma/smallfile.txt' ( 4 bytes, 1.3 KBS (cos=11))
This means that it was successful.

* Get the file

```
hsi get smallfile.txt
```

* Delete the file from the HPSS

```
hsi rm smallfile.txt
```

* Create a directroty called testing

```
hsi mkdir testing
```

* Put the fille **smallfile.txt** in the testing folder

```
hsi “cd testing; put smallfile.txt”
```

* Check the contents of the folder testing

```
hsi ls /home/$USER/testing/
```

* To transfer the directory forhpss to HPSS

```
hsi put -R forhpss
```

* To retrieve the file called file.txt from /home/$USER/forhpss

```
hsi get /home/$USER/forhpss/file.txt
```

* Get a directory from HPSS to your current folder

```
hsi get -R forhpss
```

* Delelte the directory forhpss

```
hsi rm -R forhpss
```

Similar commands will be used if you have files in the /proj/projID/$USER, just adapt the path

### HTAR 

The htar is used when there are many files to be compressed and interact with HPSS. When you have thousands files it is better to use htar than hsi as hsi will handle a bunch of files each time.

* For example to compress folder forhpss and send it to HPSS

```
htar -cvf forhpss.tar forhpss/*
``` 

Now a file forhpss.tar is created and saved in HPSS.

* Uncompress the forhpss.tar

```
htar -xvf forhpss.tar 
```
## SCP

When you want to transfer files from or to outside the OLCF systems and there is no Globus, you can use the **scp** command. Always, use it from outside the OLCF resources in order to work

* In order to transfer the file file.txt from your remote home folder to your local system, execute from your local system, while you declare your OLCF username:

```
scp username@dtn.ccs.ornl.gov:/ccs/home/username/file.txt .
```

To transfer from your local system to your remote home, execute from your local system:

```
scp file.txt username@dtn.ccs.ornl.gov:/ccs/home/username/
```
