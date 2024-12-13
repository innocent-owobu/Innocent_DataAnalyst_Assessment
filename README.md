# Innocent_DataAnalyst_Project
In this project, I used a lead dataset on Google Sheets, integrated it into Python via API, cleaned it on Python, then downloaded the cleaned dataset to PostgreSQL, updated some missing fields and finally visualised the data using Power BI. All the files and scripts are attached.


**1. Google Sheets API Setup and Integration to Pandas**

To integrate Google Sheets with Pandas, I first set up the Google Sheets API on the Google Cloud Console by creating a project, enabling the API, and generating credentials (OAuth 2.0 client). After setting up the Google Sheets API and generating the credentials, Google provides a service account email containing a credential in a .json format. Then I shared the email with the Google Sheet to grant access to the Google Sheet to allow the API to interact with it. The credentials file is then stored locally for authentication in the Python script. Using the gspread and oauth2client libraries, I authenticate and access the sheet data as seen under the code section in the "Assignment-DA.ipynb".



**2. Data Merging**

After integration of the Google Sheet to the pandas data frame via the API, I then uploaded the four(4) sheets to the data frame. To streamline analysis and ensure all data was captured in a single dataset, I merged these sheets into one data frame using the pandas.concat() function. 
df_combined = pd.concat([df1, df2, df3, df4], ignore_index=True)



**3. Data Cleaning: Phone Numbers**

After merging the data, one of the critical steps was to clean and standardize the phone number format. The country_code column had some inconsistencies, such as missing country code or incorrect formats. This section took the bulk of the time. I used regex and other pandas functions to clean the data, ensure that each country has the correct country_code and remove unwanted strings from the phone numbers. All the codes can be found in the attached "Assignment-DA.ipynb" file. There were two countries with a single lead (Italy and the UK), but since our focus was on the DACH region comprising DE, AT and CH, I discarded the Italy and UK countries.




**4. Database Setup and Integration:**
After a successful connection to the provided database instance, I created the "lead_data" table and imported the "lead_data_cleaned.csv" file. Subsequently, I identified a record with the "firma" name "t" where the "street", "plz", and "city" were missing. I updated these fields, as reflected in the current database record compared to the data in the "old data cleanup assignment.xlsx" file.

UPDATE lead_data
SET street = 'Dortmund Street 100',
    plz = '44227',
    city = 'Dortmund'
WHERE firma = 't' AND local_phone_number = '3601408922300';


**Exploratory Analysis with Power BI**

Finally, I explored the cleaned dataset using Power BI and visualized the data to see interesting insights. Some quick insights from the exploratory analysis:
** Total number of leads - 4106 
** DE accounts for 90% of the leads with 3708 leads. This is followed by AT 6% (a total of 253 leads) and CH 4% (145 leads)
** The leads covered 1872 cities and 2666 postal code areas
** In the city analysis of German cities, Berlin has the highest lead (162), followed by Hamburg and Munich, 106 and 81, respectively.
The Power BI .pbix file is also attached (innocent_exam).pbix

If you need any clarification on any of the sections, kindly reach out to me.

Thank you.
Innocent.
