# iTrackingMailer Tracking Automation  
i - *a powerful automation script* to send mailer with attachments using Python.  
It send's mail to all customers configured by fetching tickets logged in Defect tracking System

It also Form pie chart and shows the in email body as well as generated excel attachment for easy overall view for customer.  

*We recommend that you open and Read this **PREREQUISITE** before proceeding or using the rTrackMailer package anywhere*

Main Features
-------------
Here are just a few of the things that iTrackingMailer does well:

  - Easy to Call and use it
  - Powerful enough to connect DB as in config.ini and get data and geneerate excel 
  - Generated excel wil be sent to customers as in DataFiles Master json File
  - Generated File wil moved to back as mentioned in config 
  - Files split according to customer wise will be saved in separate folder described by user year/Period/Customer wise
  
---

### Prerequisites :   

Need **PYTHON** installed in machine .
Minimum requirement is * **Python 3.7** *  

Before Using rTrackMailer package , user need to install few python packages as in below.  
1.XLWT  
2.xlsxwriter  
3.pyodbc  
4.matplotlib  

---  

### Installing  

iTrackingMailer Package Can be installed to any python framework enabled machine using below command 

python -m pip install rTrackMailer-1.0.0.4.tar.gz


**Pre-Requisite Python Packaged to be installed in machine before importing rTrackMailer Package in any code**

In command line run below scrits to install all dependent packages:  
python –m pip install xlwt  
python –m pip install xlsxwriter  
python –m pip install pyodbc  
python –m pip install matplotlib  

---

## Configure The Package 

Once installed **rTrackMailer** package and pre-requisite packages mentioned above,can import rTrackMailer package for further use.  
User will need certain pre-defined folders to be defined in machine where this will be deployed & 
the same needs to be configured in config.ini file .


**config.ini** file should be always named as * **iTrackingMailer_config.ini** * & can be generated using given config Generator python file sepertely named as config_generator.py

### Config Generator Process:  
  * **config_generator.py** file can be used to generate rTrackMailer_config.ini File depending on requirement.    
  * #### Sections in Config Generator :  
      * [mssql]   
	  * [SMTP]  
	  * [Process] 
  * Values to be passed in config can be seen in [Help_config_generator.MD](Help_config_generator.MD) .  
  

---

## Master Files and Folders Need to be Defined before proceeding:  
Below folders need to be created before running the package .
Same should be configured in rTrackMailer_config.ini also using generator script.

*  **Data Files** is mandatory and to be placed in folder and folder should be configured in app_datafiles_folder node in rTrackMailer_config.ini
    *- customer_Master.json ,where all details about customers will be maintained as data source
    *- Escalation_Matrix_Details.json is file where escalation matrix <-> employee details mapping kept  
*  **Sql File** is next file required to run package if excel needed to be generated from DB ,this is mandatory is file_gen_from_db is set to **True** in config.ini File.  
*  **excel_input** is next field to be mentioned . Path in which Input Excel file will be placed or file wil generated from DB goes here.
*  **excel_output** this path is provided for processing the above input excel file and saving the same customer-wise .Its saved year->Month->customer wise excel file
*  **error_log** - The path in which Error log (*.txt) file will be saved for each and every run .
*  **Backup** - Backup of path to which main generator/Place file in Input Path .After Processing file wil be moved for future reference .
*  **Mail_template** - Path in which mail template HTML with placeholders wil be placed(optional)& any folder can be used and same to configured mainly in customer_Master Master data
*  **mailer_contains_cid** - Boolean alue to tell embedded image in mail body for the template html .
    If Set to Default path for images to be placed in same as inside Template folder as in customer master.
    Folder should be named as  **Images** inside folder where template will be placed as defined in customerMaster.Json 


---


## Importing the iTrackingMailer Package and using in one line python script to automate the task.

*from iTrackingMailer import excel_Read as xls* ,Where iTrackingMailer is overall solution package,
excel_Read is main file which we will call to execute the logic for rTrack Mailer automation process

Once above line is done next is:
*xls.main(“config file.ini path goes here”)*,where **xls** is *alise name* given to iTrackingMailer package in first import statement as in above.

*Final Code(for Example)*:  
from iTrackingMailer import excel_Read as xls
xls.main('D:\foldername\')

## Built With  
* [Python](https://www.python.org/) - Framework in which tool is built
* [Pandas](https://pandas.pydata.org/) - Excel Manipulator
* [Numpy](http://www.numpy.org/) - Numpy for processing
* [MatPlotLib](https://matplotlib.org/) - Used to generate pie charts as attachment body in mailer sent to customer

## Versioning

We use [SemVer](http://semver.org/) for versioning.  

## Authors

* **Arvind.K** - *Author work* - [AK](https://github.com/arvindkannan)
* **VenkadaBalaji.S** - *Contributor/Co-Author*

## License

This project is licensed under the MIT/GNU License.

