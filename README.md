Project Birds of Ireland Data Analysis
Overview
This project focuses on visualizing the geographic distribution and concentration of bird populations across Ireland. It involves developing an interactive map that allows users to explore bird concentration patterns spatially, along with implementing filtering capabilities based on year, month, and bird species for flexible temporal and taxonomic analysis. The analysis is based on comprehensive bird observation data from the Irish Spatial Data Exchange (ISDE).
Data Source
The bird observation data was downloaded from the Irish Spatial Data Exchange (ISDE) on August 6, 2025.
• Data Source URL: https://www.isde.ie/geonetwork/srv/eng/catalog.search#/metadata/ie.nbdc.dataset.BirdsOfIreland
• Data Coverage: The dataset covers the period from January 1, 1970, with the majority of records collected from 2011 onwards.
• Extensibility: The project is designed to be extensible and can be updated with new data in future releases as the dataset is ongoing.
Project Objectives & Key Features
• Geographic Distribution and Concentration: Visualize where bird populations are distributed and concentrated across Ireland.
• Interactive Map: Develop a map that enables users to explore these patterns spatially.
• Flexible Analysis: Implement filtering options by year, month, and bird species to support temporal and taxonomic analysis.
Data Preprocessing Steps
Thorough data preprocessing was conducted to ensure data quality and consistency:
• Handling Unnamed Columns: Several unnamed columns were identified during initial inspection. These were found to be fragmented text fields, likely due to improper CSV delimiter enclosure. These unnamed columns were merged with the "Activity" column to reconstruct complete text fields and preserve data integrity.
• Date Field Validation: Reviewed 'Date' and 'StartDate' fields for completeness. It was determined that the 'StartDate' field could not be reliably used to supplement missing 'Date' values due to invalid content (e.g., 'False').
• Feature Selection and Removal: An initial review identified columns for removal based on criteria such as irrelevance, redundancy, or poor data quality. Columns removed include:
    ◦ SurveyKey, SampleKey
    ◦ StartDate, EndDate
    ◦ Recorder, Determiner, ZeroAbundance, UnderValidation, Determiner name, Survey name
    ◦ Site description, Source
    ◦ Habitat code (Fossitt, 2000) (due to being empty/nearly empty and not relevant for analysis)
    ◦ SiteKey, ImagePath (as empty fields)
• Coordinate System Unification: To ensure consistency, latitude and longitude fields were created. Records with 'WGS84' projection directly used their North and East values, while records with 'OSI' projection were transformed from Irish Grid (OSI) to WGS84 coordinates.
• Date Standardization: For records where DateType was 'O' (Observation type), dates like "Jul 2007" and "Nov 2010" were standardized to "15/07/2007" and "15/11/2010", respectively. This approximation does not impact the project's analytical outcomes.
• Handling Missing Latitude/Longitude: Rows with null values in the 'latitude' field were removed to ensure all observations have geographic coordinates.
• Imputing Common Name: Missing entries in the 'Common name' column were filled by referencing non-null values from rows sharing the same 'TaxonName', improving the completeness of bird identification data.
• Filling County and Vice-county: Missing values in 'County' and 'Vice-county' were filled by referencing valid entries from rows with matching 'SiteName' identifiers, significantly reducing nulls in these geographic fields. Remaining null records were retained due to valuable geolocation data.
• Removing Year-Only Dates: Rows where the 'Date' field was null, corresponding to entries with only a year and no specific month, were removed as they did not align with project requirements.
• Final Dataset Preparation: The processed dataset was exported to a CSV file (birds_processed.csv) for further visualization and analysis.
Exploratory Data Analysis (EDA)
The EDA phase involved visualizing key aspects of the dataset to understand its structure, identify patterns, and detect anomalies.
• Most Frequently Observed Species (Ireland-wide): Analysis revealed that Buteo buteo (Common Buzzard) is the most frequently recorded bird species in Ireland, followed by Erithacus rubecula (European Robin) and Turdus merula (Common Blackbird).
• Localized Species Distribution (Cork County Example): The project provides localized insights by examining the distribution of species within a specific county, using Cork as an example. This analysis also included data filtered for the year 2024.
• Annual Trends for Buteo buteo: Observation trends for Buteo buteo over the last 10 years were analyzed, showing yearly counts.
• Monthly Trends for Buteo buteo: Monthly observation trends for Buteo buteo were analyzed to identify seasonal patterns and variations, providing insights into when this species is most frequently observed throughout the year.
• Monthly and Annual Heatmap: A heatmap was created to visualize the monthly and annual observation patterns of Buteo buteo over the last 10 years, offering a comprehensive view of its presence across time.
Technologies and Tools
• Python: Used for data loading, preprocessing, and exploratory data analysis.
    ◦ pandas: For data manipulation and analysis.
    ◦ numpy: For numerical operations.
    ◦ datetime: For date and time handling.
    ◦ matplotlib.pyplot: For creating static visualizations.
    ◦ seaborn: For enhanced data visualizations, especially heatmaps.
    ◦ pyproj: For geographic coordinate transformations (OSI to WGS84).
• LibreOffice Calc: Used for initial dataset inspection.
• Tableau: Utilized for creating interactive visualizations and dashboards.
How to Explore
The interactive visualizations are available on the Tableau dashboard, providing a dynamic way to explore the bird observation data.
• Tableau Dashboard: Birds of Ireland Dashboard (Please insert the actual link to your Tableau dashboard here, as per source)
