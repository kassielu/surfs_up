# surfs_up

## Project Overview
In this module we'll be using SQLite and SQLAlchemy to run analytics on a weather data set for the island of Oahu. The purpose of our analysis is present weather analysis to our investor, W.Avy, for Oahu where we hope to open up a Surf & Shake shop. We will be using Flask to present our final analysis on the web in real-time to our potential investors.

### Resources
- Data Sources: [hawaii.sqlite](hawaii.sqlite)
- Result Files: [climate_analysis.ipynb](climate_analysis.ipynb), [SurfsUp_Challenge.ipynb](SurfsUp_Challenge.ipynb), [app.py](app.py)
- Image Files: [december_temp.png](december_temp.png), [june_temp.png](june_temp.png), [compare.png](compare.png)
- Software: Python 3.7.6, Anaconda 4.8.3, Jupyter Notebook 6.0.3, SQLite, SQLAlchemy

## Results
Our anlysis indicated the following difference for weather in June vs. December:
- Average Weather: the average weather in June, which is 75 degress, is about 4 degrees higher than December, which is 71 degrees.
- Minimum Weather: the minimum weather in June is 64, which is 8 degrees higher than December.
- Maximum Weather: the maximum weather in June is 85, which is 2 degrees higher than December.

To see additional information on both data set refer to [Compare PNG](compare.png) file.

## Summary
To gather more weather data for June and December, we'd recommend running the following 2 queries:
- The following query will generate weather data for the month of June with station temperatures.
```
pd.read_sql("""SELECT station, count(station) as count, min(tobs) as min,max(tobs) as max,avg(tobs) as avg 
                FROM Measurement where strftime('%m', Measurement.date) = '06' group by station 
                order by count desc""", engine)
```

- The following query will generate weather data for the month of December with station temperatures.
```
pd.read_sql("""SELECT station, count(station) as count, min(tobs) as min,max(tobs) as max,avg(tobs) as avg 
                FROM Measurement where strftime('%m', Measurement.date) = '12' group by station 
                order by count desc""", engine)
```

