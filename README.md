# Data Transfer
A tutorial about data transfer on OLCF systems

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

If you want to use the archiving system, HPSS with Globus, the only difference with above, is to declare a path on HPSS, and for example the archive of your project on HPSS, is under /proj/projid/username

<div style="text-align:center"><img src="https://github.com/olcf-tutorials/Data_Transfer/blob/master/figures/globus_hpss_4_options.png?raw=true" width="75%"/></div>

