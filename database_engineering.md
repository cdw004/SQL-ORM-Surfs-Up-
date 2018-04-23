

```python
import pandas as pd
import matplotlib
matplotlib.use('nbagg')
from matplotlib import style
style.use('seaborn')
import matplotlib.pyplot as plt
import csv
```


```python
file1 = "clean_hiMeasurements.csv"
file2 = "clean_hiStations.csv"
```


```python
measurements = pd.read_csv(file1, encoding = "ISO-8859-1") 
stations=pd.read_csv(file2)
```


```python
from sqlalchemy import create_engine, Column, Integer, String, Date, Float
from sqlalchemy.ext.declarative import declarative_base
Base = declarative_base()
```


```python
class Measurements(Base):
    __tablename__="measurements"
    m_id= Column(Integer, primary_key=True)
    station = Column(String(255))
    date = Column(Date)
    prcp = Column(Float)
    tobs = Column(Integer)

#Add Float to engine to allow for Float in class.
```


```python
class Stations(Base):
    __tablename__="stations"
    s_id = Column(Integer, primary_key=True)
    station = Column(String(255))
    name = Column(String(255))
    latitude = Column(Float)
    longitude = Column(Float)
    elevation = Column(Float)
```


```python
engine = create_engine("sqlite:///hawaii.sqlite")
```


```python
Base.metadata.create_all(engine) 
```


```python
measurements.to_sql('measurements', engine, if_exists="append", index=False)
```


```python
stations.to_sql('stations', engine, if_exists="append", index=False)
```
