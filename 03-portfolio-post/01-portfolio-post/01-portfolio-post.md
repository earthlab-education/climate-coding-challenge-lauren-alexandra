# Climate coding challenge, Part 6

Getting your own data

## There are more Earth Observation data online than any one person could ever look at

[NASA’s Earth Observing System Data and Information System (EOSDIS)
alone manages over 9PB of
data](https://www.earthdata.nasa.gov/learn/articles/getting-petabytes-people-how-eosdis-facilitates-earth-observing-data-discovery-and-use).
1 PB is roughly 100 times the entire Library of Congress (a good
approximation of all the books available in the US). It’s all available
to **you** once you learn how to download what you want.

Here we’re using the NOAA National Centers for Environmental Information
(NCEI) [Access Data
Service](https://www.ncei.noaa.gov/support/access-data-service-api-user-documentation)
application progamming interface (API) to request data from their web
servers. We will be using data collected as part of the Global
Historical Climatology Network daily (GHCNd) from their [Climate Data
Online library](https://www.ncdc.noaa.gov/cdo-web/datasets) program at
NOAA.

For this example we’re requesting [daily summary data in
**Boulder, CO** (station ID
**USC00050848**)](https://www.ncdc.noaa.gov/cdo-web/datasets/GHCND/stations/GHCND:USC00050848/detail).

> ** Your task:**
>
> 1.  Research the [**Global Historical Climatology Network -
>     Daily**](https://www.ncei.noaa.gov/metadata/geoportal/rest/metadata/item/gov.noaa.ncdc:C00861/html)
>     data source.
> 2.  In the cell below, write a 2-3 sentence description of the data
>     source.
> 3.  Include a citation of the data (**HINT:** See the ‘Data Citation’
>     tab on the GHCNd overview page).
>
> Your description should include:
>
> -   who takes the data
> -   where the data were taken
> -   what the maximum temperature units are
> -   how the data are collected

**YOUR DATA DESCRIPTION AND CITATION HERE** 🛎️

##### Data Description

The Global Historical Climatology Network daily dataset contains observations collected by land-based weather stations in the World Meteorological Organization, Cooperative, and CoCoRaHS networks. If observed, the dataset will include maximum and minimum temperatures (F), total precipitation (in), and snowfall and snow depth (in). 

##### Data Citation

Menne, Matthew J., Imke Durre, Bryant Korzeniewski, Shelley McNeill, Kristy Thomas, Xungang Yin, Steven Anthony, Ron Ray, Russell S. Vose, Byron E.Gleason, and Tamara G. Houston (2012): Global Historical Climatology Network - Daily (GHCN-Daily), Version 3. [GHCND:USC00050848]. NOAA National Climatic Data Center. doi:10.7289/V5D21VHZ [09/15/2024].

## Access NCEI GHCNd Data from the internet using its API 🖥️ 📡 🖥️

The cell below contains the URL for the data you will use in this part
of the notebook. We created this URL by generating what is called an
**API endpoint** using the NCEI [API
documentation](https://www.ncei.noaa.gov/support/access-data-service-api-user-documentation).

> **Note**
>
> An **application programming interface** (API) is a way for two or
> more computer programs or components to communicate with each other.
> It is a type of software interface, offering a service to other pieces
> of software ([Wikipedia](https://en.wikipedia.org/wiki/API)).

First things first – you will need to import the `pandas` library to
access NCEI data through its URL:

> **Your task:**
>
> 1.  Pick an expressive variable name for the URL.
> 2.  Reformat the URL so that it adheres to the [79-character PEP-8
>     line
>     limit](https://peps.python.org/pep-0008/#maximum-line-length). You
>     should see two vertical lines in each cell - don’t let your code
>     go past the second line.
> 3.  At the end of the cell where you define your url variable, **call
>     your variable (type out its name)** so it can be tested.




    'https://www.ncei.noaa.gov/access/services/data/v1?dataset=daily-summaries&dataTypes=TOBS,PRCP&stations=USC00050848&startDate=1893-10-01&endDate=2023-09-30'



------------------------------------------------------------------------

## **Download and get started working with NCEI data**

Just like you did with the practice data, go ahead and use pandas to
import data from your API URL into Python. If you didn’t do it already,
you should import the pandas library **at the top of this notebook** so
that others who want to use your code can find it easily.




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>STATION</th>
      <th>DATE</th>
      <th>PRCP</th>
      <th>TOBS</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>USC00050848</td>
      <td>1893-10-01</td>
      <td>239.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>USC00050848</td>
      <td>1893-10-02</td>
      <td>0.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>USC00050848</td>
      <td>1893-10-03</td>
      <td>0.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>USC00050848</td>
      <td>1893-10-04</td>
      <td>10.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>USC00050848</td>
      <td>1893-10-05</td>
      <td>0.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>


