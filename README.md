# DATA SCIENCE LIFE CYCLE

{ A PYTHON PROJECT ON AUTOLIB SCHEME TO UNDERSTAND ELECTRIC CAR USAGE}

{BY DUNCAN KARIUKI} {ON APRIL 2020}

## DESCRIPTION
  Investigating the most popular time where electrical vehicles operated by Autolib are highered and returned.
  
## EXPERIMENTAL DESIGN

### i) BUSINESS UNDERSTADING
       
       BUSINESS OBJECTIVES
       
The objective of this report is to draw an understanding from a 9days dataset collected from various areas serviced by Autolib scheme in France. This information will give us a view of the electric car usage over time.

      BUSINESS SUCCESS CRITERIA
      
To determine the most popular times of the day where electric cars are used.
        
 ### ii) DATA UNDERSTANDING
 
 Autolib dataset [http://bit.ly/autolib_dataset] -  it contains information of electric cars in the autolib scheme,the stations where they are packed ,charging slots available,their location,there postal codes and addresses and time and date they were highered and returned for a period of nine days.

WE CHECK FOR INFORMATION ABOUT OUR DATASET

autolib.info()

autolib.describe()

 ### iii) DATA PREPARATION
#REMOVE WHITE SAPCES IN OUR CLUMNS

autolib.columns.str.replace(" "," ")        

REMOVE THE COLUMNS THAT ARE NOT NECCESARY FOR OUR ANALYSIS

EXPLANATION: WE WILL REMOVE'Address','Cars','Charge Slots','Charging Status','Displayed comment','Geo point','Scheduled at','Subscription status','Station type' as they are not neccessary for our analysis
auto = autolib.drop(['Address','Cars','Charge Slots','Charging Status','Displayed comment','Geo point','Scheduled at','Subscription status','Station type'], axis=1)
auto.head(5)

we will the remove white spaces from our rows of typre string

Explanation :This is to avoid syntax errors

auto['City']=auto['City'].str.strip()
auto['ID']= auto['ID'].str.strip()
auto['Kind']=auto['Kind'].str.strip()
auto['Public name']=auto['Public name'].str.strip()
auto['Rental status']=auto['Rental status'].str.strip()
auto['Status']=auto['Status'].str.strip()
auto.head(4)

 WE WLLL THEN FILTER THE ROWS THAT WE NEED
 
 WE WILL FILTER STATIONS SINCE WE HAVE BEEN TASKED WITH PROCESSING STATIONS DATA
auto = auto[auto['Kind']=="STATION"]
auto.head(3)

WE WILL THEN FILTER OUR DATA INORDER TO GET ONLY THE OPERATIONAL STATIONS

auto = auto[auto['Rental status']=="operational"]
auto.head(3)

 ### iv) Analysis 
 Which is  the most popular hour of the day for picking up a shared electric car (Bluecar) in the city of Paris over the month of April 2018?
 
 Here we are going to assume if the number of slots is greater than the number of BLUECAR COUNTER then the cars have been highed out.
 
auto_paris = auto[auto['CITY']=="Paris"]
auto_paris    

We are going to assume that all of the UTILIB COUNTER	,UTILIB 1.4 COUNTER were hired out

auto_higher = auto_paris[auto_paris['SLOTS'] >( auto_paris['BLUECAR COUNTER'])]
auto_higher= auto_higher.groupby(['HOUR'])['HOUR'].count()
auto_higher.sort_values(ascending=False).head(1)

### v) RECOMMEBDATIONS
Following our analysis the following recommendations were made:
The efficiency of the autolib scheme should be improved in order to ensure availability of vehicles to subscribers on request.

### vi)EVALUATION
We have been able to determine the most popular times of the day were electric car usage is at its maximum from our Business Success Criteria based on insights from our analysis.

#### SETUP REQUIREMENTS
  GITHUB
  GOOGLE COLLABOLATORY
  PANDAS LIBRALY
  
#### KNOWN BUGS
  {THERE WERE NO KNOWN BUGS}

#### TECHNOLOGIES USED
  {PYTHON}
  
#### SUPPORT AND CONTACT DETAILS
    {Any additions are highly encouraged}
  
  

        
