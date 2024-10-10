# Innocent_DataAnalyst_Assessment
task on lead data


**Google Sheets API Setup and Integration to Pandas**
To integrate Google Sheets with Pandas, I first set up the Google Sheets API on the Google Cloud Console by creating a project, enabling the API, and generating credentials (OAuth 2.0 client). After setting up the Google Sheets API and generating the credentials, Google provides a service account email in the credentials.json file. Then I shared the email with the Google Sheet to grant access to the Google Sheet to allow the API to interact with it. The credentials file is then stored locally for authentication in the Python script. Using the gspread and oauth2client libraries, I authenticate and access the sheet data as seen under the code section in the "Assignment-DA.ipynb".


**Data Merging**
After integration of the Google Sheet to the pandas data frame via the API, I then uploaded the four(4) sheets to the data frame. To streamline analysis and ensure all data was captured in a single dataset, I merged these sheets into one data frame using the pandas.concat() function. 
df_combined = pd.concat([df1, df2, df3, df4], ignore_index=True)


**Data Cleaning: Phone Numbers**
After merging the data, one of the critical steps was to standardize the phone number format. The country_code column had some inconsistencies, such as missing values or incorrect formats, and phone numbers without the country dialing code. This section took the bulk of the time. I used regex and other pandas functions to cleaned the data, ensure that each country has the correct country_code and remove unwanted strings from the phone numbers. All the codes can be found in the "Assignment-DA.ipynb" file. There were two countries with a single lead (Italy and the UK), I assumed the focus was on the three main countries, hence I discarded their records.


**Database Setup and Integration**
The Postgres database originally provisioned could not connect due to a private network. I will talk more about that via the email correspondence. However, I had to set it up locally on my system and the snapshots are in the zip file names "Database setup and update.zip"


**Exploratory Analysis with Power**
Finally, I explored the cleaned dataset using Power BI and visualized the data to see interesting insights. Some quick insights from the exploratory analysis:
** Total number of leads is about 4106 
** DE accounts for 90% of the leads with a total of 3708 leads. This is followed by AT 6% (a total of 253 leads) and CH 4% (45 leads)
** The leads covered 1872 cities and 2666 postal code areas
** From the city analysis, German cities, Berlin has the highest leads (162) followed by Hamburg and Munich 106 and 81 respectively.
The Poer BI .pbix file is also attached (innocent_exam).pbix

If you need any clarification on any of the sections, kindly reach out to me.

Thank you.
Innocent.
