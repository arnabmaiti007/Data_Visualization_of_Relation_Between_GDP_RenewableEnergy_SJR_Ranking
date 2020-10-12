# Data Visualization of Relation Between GDP, %Renewable Energy and SJR Ranking:
## Introduction:
Here I have written a code using Python, Pandas, Matplotlib to visualize the data and setting up a relation between GDP, %Renewable Energy and SJR Ranking. This is a bubble chart showing % Renewable vs. Rank. The size of the bubble corresponds to the countries'  2014 GDP, and the color corresponds to the continent.

# Description:
1. I have loaded the energy data from the file `Energy Indicators.xls`, which is a list of indicators of [energy supply and renewable electricity production](Energy%20Indicators.xls) from the [United Nations](http://unstats.un.org/unsd/environment/excel_file_tables/2013/Energy%20Indicators.xls) for the year 2013, and has been put into a DataFrame with the variable name of **energy**.

2. I exclude the footer and header information from the datafile. The first two columns are unneccessary, so I get rid of them, and changed the column labels so that the columns are:

`['Country', 'Energy Supply', 'Energy Supply per Capita', '% Renewable']`

3. Then Converted `Energy Supply` to Gigajoules (there are 1,000,000 gigajoules in a petajoule). For all countries which have missing data (e.g. data with "..."), It is reflected as `np.NaN` values.

4. Renaming the following list of countries:

"Republic of Korea": "South Korea",
"United States of America": "United States",
"United Kingdom of Great Britain and Northern Ireland": "United Kingdom",
"China, Hong Kong Special Administrative Region": "Hong Kong"

5. There are also several countries with numbers and/or parenthesis in their name. So I rename these as following, 

e.g. 

'Bolivia (Plurinational State of)'` should be `'Bolivia'`, 

`'Switzerland17'` should be `'Switzerland'.


6. Next, I load the GDP data from the file `world_bank.csv`, which is a csv containing countries' GDP from 1960 to 2015 from [World Bank](http://data.worldbank.org/indicator/NY.GDP.MKTP.CD). Called this DataFrame **GDP**. 

7. I skip the header, and rename the following list of countries:

"Korea, Rep.": "South Korea", 
"Iran, Islamic Rep.": "Iran",
"Hong Kong SAR, China": "Hong Kong"


8. Finally, I load the [Sciamgo Journal and Country Rank data for Energy Engineering and Power Technology](http://www.scimagojr.com/countryrank.php?category=2102) from the file `scimagojr-3.xlsx`, which ranks countries based on their journal contributions in the aforementioned area. Call this DataFrame **ScimEn**.

9. At last, I join the three datasets: GDP, Energy, and ScimEn into a new dataset (using the intersection of country names). And used only the last 10 years (2006-2015) of GDP data and only the top 15 countries by Scimagojr 'Rank' (Rank 1 through 15). 

10. The index of this is the name of the country, and the columns are ['Rank', 'Documents', 'Citable documents', 'Citations', 'Self-citations',
       'Citations per document', 'H index', 'Energy Supply',
       'Energy Supply per Capita', '% Renewable', '2006', '2007', '2008',
       '2009', '2010', '2011', '2012', '2013', '2014', '2015'].
