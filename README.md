you will need to install PyJWT and the Google Python Client modules

More relevant to the normal user is what comes next. This is where we put the configuration, so adjust this section as needed

Config file 
Line 2-5 must be filled with the client data you create in the Adobe IO console. It is used to connect to the Adobe Analytics API. At the bottom of the config block, put in your private key to the Adobe IO account at line 18.
Line 6 holds the property from the Google Search Console. This is the property that your data will be imported from. Usually, it is equal to your website URL.
Line 7 contains the name of the Data Source you create in Adobe Analytics. Make sure this value matches the name exactly. In line 8 we define the Report Suite ID where we want our data to be imported. To better recognize your imported files, Line 9 demands a prefix of the imported filenames.
The lookback window we define in Line 10 limits how far back the imported data should be. This value is in days and starts with today. The script keeps track of what data has been imported already, so a long window only leads to a longer import on the first run.

Line 11 trough 17 are most important for what data gets actually imported. This is where we define which Dimensions and Events will be used. If you don’t want to use a certain dimension, you can leave the value empty. At minimum, we need the type eVar and one Event. The script determines what should be imported by the variables we define.

Connecting to the APIs
To differentiate between import types, the type eVar describes what was imported in the current query. In the next section of the code, we create a list of dates to query and check if the configuration regarding the dimensions and events is valid.

Receiving completed Data Source import jobs from Adobe Analytics
Now that we are connected and have our Access Token, we can query the Adobe Analytics API to receive a list of Data Sources for the configured Report Suite. If it matches the name we have chosen in the configuration we continue with the Data Source ID

Query Search Console data and upload to Adobe Analytics
Now to the main gig. Now that we know what dates we need to import, we can start pulling data from Google day by day and create an import jobs for the Adobe Analytics Data Source

