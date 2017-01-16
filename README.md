# ddd
#### Date: 21-10-2016
#### Description: This document aims to define the Bluemix Tone Analyzer API coding 


#### The Folder Structure is as follows:
   
   
   Root Directory | Sub Directory | Sub Directory 
------------ | ------------- | -------------
index.php | | |
Global | DBmongo(Mongo Connection),DBmysql(MySQL Connection), BlueMixToneAnalyzerAPI(Tone Analyzer Connection)  | 
Lib | Smarty,Common functions | |
Modules | BluemixToneAnalyzer | Tone Analyzer Controller, Tone Analyzer Action, Tone Analyzer MySql, Tone Analyzer View, Tone Analyzer API Call, Tone Analyzer DB Mongo|
Views | BluemixToneAnalyzer | header.tpl, footer.tpl(Common files), masterList.tpl,detailList.tpl|

#### Code Flows as follows:
   * To insert or get data from DB code flows.. index.php -> Controller -> Action -> MySql.
   * To view the data code flows.. index.php -> Controller -> View.
   
 
#### Step 1:
  Add the created Url, Username and Password in the config.php under bluemix2.0 folder.we can get the Tone Analyzer API Username and password by logging into IBM Bluemix. 
	
**_Code:_**
	
```
	
	$GLOBALS['bluemix_toneanalyzer_username']='xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx';
	$GLOBALS['bluemix_toneanalyzer_password']='xxxxxxxxxxxx';
	$GLOBALS['bluemix_toneanalyzer_url']='https://gateway.watsonplatform.net/tone-analyzer/api/v3/tone?version=2016-05-19';
	
```
	
  
#### Step 2:
  Create a module name as 'toneAnalyzer' in index.php and respective actions will be performed accordingly.
  
**_Code:_**

```
<?php
if($_REQUEST['module']=='toneAnalyzer'){  
    switch ($_REQUEST['action']){
	    case 'GetList':
        {
          $bluemixToneAnalyzerController = BluemixToneAnalyzerController::getInstance();
          $bluemixToneAnalyzerController->getMasterDataFromMySQL();
          break;
        }
        case 'DetailList':
        {
          $bluemixToneAnalyzerController = BluemixToneAnalyzerController::getInstance();
          $bluemixToneAnalyzerController->getChildDataFromMySQL($_REQUEST);
          break;
