# Interactive Map For Single and Double Storey Terraced Property Sale For 2022 In Melaka

## Project Overview 
Given the current market dynamics, this project proposes the development of an interactive map that will provide comprehensive data on every single storey and double storey terraced property sold in Melaka in 2022. This unique tool will empower housing developers to formulate effective pricing and business strategies for future developments in Melaka.   

Property sales for single and double storey terraced in Melaka recorded at RM869,477,476.00 with 2870 transactions in 2022. These transactions represent freehold and leasehold terraced houses covering 457 scheme name/areas located in 3 districts namely Melaka Tengah, Alor Gajah and Jasin.

The state’ property market is expected to continue its growth momentum with future developments projects are expected to create positive impact on the state’s property market such Melaka Waterfront Economic Zone (MWEZ) by 2035 and on-going contruction of Harbour City Melaka by Hatten Land Ltd.

![MWEZ.png](https://lh6.googleusercontent.com/u3S4EjKsun7Jt-ps9r-lcqcxqUaZU_ivDgh3LXEvsizJRh9AQ5GxMCVMOOpPoznHfpnCPnAHyP4jsPEH667fTL2Kq877bu0YduAXCWbptZ-6_uCgzvZhQ2We_Son0_FRQiFDOybG)

## Terraced Property Outlook

Single and double storey terraced residentials will be the property segments to watch as Scientex Berhad had launched new project which is Scientex Durian Tunggal 2 on 202 acres land while Parkland Group had launched Bandar Botani Parkland in Jasin.

These two major residentials will be new offerings for future home buyers looking for single or double storey terraced property in Melaka.

![SCIENTEX.png](https://scientex.com.my/wp-content/uploads/2021/09/Aerial-View-Photo.jpeg)

## Code and Resources Used

* __Jupyter Notebook Version__: 6.5.4
* __Packages__: pandas, numpy, scipy, matplotlib, seaborn, plotly express
* __Dataset Source__: https://napic2.jpph.gov.my/ms/data-transaksi?category=36&id=241

## Dataset Information

[_**'dataset_2022.csv'**_](https://github.com/wafiesa/Codes/blob/master/dataset_2022.csv) contains data from National Property Information Centre (NAPIC).<br>
[_**'latlong.csv'**_](https://github.com/wafiesa/Codes/blob/master/latlong.csv) contains latitude and longitude information for scheme name/area. This lat and long information were built from https://postcode.my/location/melaka/ based on scheme name/area from dataset_2022.<br>
[_**'melaka_terraced_property_sales_2022.csv'**_](https://github.com/wafiesa/Codes/blob/master/melaka_terraced_property_sales_2022.csv) contains data generated from Jupyter Notebook following cleaning processes.

## [1. Exploratory Analysis](https://github.com/wafiesa/Codes/blob/master/Melaka_Terraced_Property_Sales_2022.ipynb)

In this part, we will begin our exploratory data analysis (EDA) by viewing the dataset_2022.csv.

#### Dataset overview

|	|Property Type				|District	|Mukim				 |Scheme Name/Area			|Month, Year of Transaction Date	|Tenure		|Land Area	|Unit	|Main Floor Area	|Transaction Price|
|---|---------------------------|-----------|------------------- |---------------------------|----------------------------------|-----------|-----------|-------|-------------------|-----------------|
|0	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Bdr Alor Gajah	     |TAMAN SERI BAYU	         |October 2022	                    |Leasehold	|143.0	    |sq.m	|85.84	            |200000           |
|1	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Bdr Masjid Tanah	 |TAMAN BKT INDAH			 |July 2022							|Freehold	|143.0		|sq.m	|76.64				|173000			  |
|2	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Bdr Masjid Tanah	 |TAMAN BKT INDAH			 |September 2022					|Freehold	|143.0	    |sq.m	|77.01				|210000           |
|3	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Belimbing			 |TAMAN BELIMBING HARMONI	 |October 2022						|Leasehold	|232.0	    |sq.m	|75.72				|361111           |
|4	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Belimbing			 |TAMAN VISTA BELIMBING	     |January 2022						|Freehold	|128.0	    |sq.m	|83.61				|230000           |

🔶 Insights: The data contains 2870 rows with 10 columns.  

We can observe that the dataset_2022.csv gives us the information of property type, district, mukim, scheme name/area, month, year of transcation date, tenure, land area, unit, main floor area and transaction price. It is quite detailed for record of property transactions.

However, we notice that the dataset uses square meter (sq.meter) to represent the 'Land Area' and 'Main Floor Area'. Although this is sufficient to perform EDA but the most common nomenclature used in the market to represent the built size is in square feet measurement.

Thus we can convert the Land Area and Main Floor Area to square feet (sq.ft). Also we can rename the Land Area to Land Size while the Main Floor Area to Build Size. 

Additionally, we have set column 'Month, Year of Transaction Date' to a date column. 

|	|Property Type				|District	|Mukim				 |Scheme Name/Area			 |Month, Year of Transaction Date	|Tenure		|Land Size	|Unit	|Build Size	|Transaction Price|
|---|---------------------------|-----------|------------------- |---------------------------|----------------------------------|-----------|-----------|-------|-------------------|-----------------|
|0	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Bdr Alor Gajah	     |TAMAN SERI BAYU	         |2022-10-01	                    |Leasehold	|1539.2377  |sq.ft	|923.9731	        |200000           |
|1	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Bdr Masjid Tanah	 |TAMAN BKT INDAH			 |2022-07-01							|Freehold	|1539.2377	|sq.ft	|824.9453			|173000			  |
|2	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Bdr Masjid Tanah	 |TAMAN BKT INDAH			 |2022-09-01					|Freehold	|1539.2377  |sq.ft	|828.9279			|210000           |
|3	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Belimbing			 |TAMAN BELIMBING HARMONI	 |2022-10-01						|Leasehold	|2497.2248  |sq.ft	|815.0425			|361111           |
|4	|1 - 1 1/2 Storey Terraced	|Alor Gajah	|Belimbing			 |TAMAN VISTA BELIMBING	     |2022-01-01						|Freehold	|1377.7792	|sq.ft	|899.9697			|230000           |

🔶 Insights: We have renamed a few columns and converted values for Land Size and Build Size to square feet measurement. 

#### Latitude and Longitude Positions

Before an interactive map can be plotted, we must first obtain the approximate latitude and longitude positions for every scheme name/area. Since the dataset does not list the latitude and longitude positions, we can obtain the information from the portal postcode.my. The portal has an integration API with Google Maps.

Ultimately, 457 scheme name/areas are available from the portal and we can generate the positions. However, we need to combine latitude and longitude positions into the original dataset.

|	|Scheme Name/Area			|Lat	    |Long		|
|---|---------------------------|-----------|-----------|
|0	|TAMAN SERI BAYU	        |2.384740   |102.212509 |
|1	|TAMAN BKT INDAH			|2.350550	|102.103860 |
|2	|TAMAN BKT INDAH			|2.350550   |102.103860 |
|3	|TAMAN BELIMBING HARMONI	|2.335506	|102.266894 |
|4	|TAMAN VISTA BELIMBING   	|2.328142	|102.266958 |
