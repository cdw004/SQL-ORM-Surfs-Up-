

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
file1 = "hawaii_measurements.csv"
file2 = "hawaii_stations.csv"
```


```python
file_one_df = pd.read_csv(file1, encoding = "ISO-8859-1") 
```


```python
file_two_df=pd.read_csv(file2)
```


```python
file_one_df.head()
```




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
      <th>station</th>
      <th>date</th>
      <th>prcp</th>
      <th>tobs</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>USC00519397</td>
      <td>2010-01-01</td>
      <td>0.08</td>
      <td>65</td>
    </tr>
    <tr>
      <th>1</th>
      <td>USC00519397</td>
      <td>2010-01-02</td>
      <td>0.00</td>
      <td>63</td>
    </tr>
    <tr>
      <th>2</th>
      <td>USC00519397</td>
      <td>2010-01-03</td>
      <td>0.00</td>
      <td>74</td>
    </tr>
    <tr>
      <th>3</th>
      <td>USC00519397</td>
      <td>2010-01-04</td>
      <td>0.00</td>
      <td>76</td>
    </tr>
    <tr>
      <th>4</th>
      <td>USC00519397</td>
      <td>2010-01-06</td>
      <td>NaN</td>
      <td>73</td>
    </tr>
  </tbody>
</table>
</div>




```python
file_two_df.head()
```




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
      <th>station</th>
      <th>name</th>
      <th>latitude</th>
      <th>longitude</th>
      <th>elevation</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>USC00519397</td>
      <td>WAIKIKI 717.2, HI US</td>
      <td>21.2716</td>
      <td>-157.8168</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>USC00513117</td>
      <td>KANEOHE 838.1, HI US</td>
      <td>21.4234</td>
      <td>-157.8015</td>
      <td>14.6</td>
    </tr>
    <tr>
      <th>2</th>
      <td>USC00514830</td>
      <td>KUALOA RANCH HEADQUARTERS 886.9, HI US</td>
      <td>21.5213</td>
      <td>-157.8374</td>
      <td>7.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>USC00517948</td>
      <td>PEARL CITY, HI US</td>
      <td>21.3934</td>
      <td>-157.9751</td>
      <td>11.9</td>
    </tr>
    <tr>
      <th>4</th>
      <td>USC00518838</td>
      <td>UPPER WAHIAWA 874.3, HI US</td>
      <td>21.4992</td>
      <td>-158.0111</td>
      <td>306.6</td>
    </tr>
  </tbody>
</table>
</div>




```python
#File2 is clean; no NaN's therefore no drops necessary
#blank data in FileOne is far & inbetween - intention to drop the rows.
```


```python
file_one_df.dropna()
```




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
      <th>station</th>
      <th>date</th>
      <th>prcp</th>
      <th>tobs</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>USC00519397</td>
      <td>2010-01-01</td>
      <td>0.08</td>
      <td>65</td>
    </tr>
    <tr>
      <th>1</th>
      <td>USC00519397</td>
      <td>2010-01-02</td>
      <td>0.00</td>
      <td>63</td>
    </tr>
    <tr>
      <th>2</th>
      <td>USC00519397</td>
      <td>2010-01-03</td>
      <td>0.00</td>
      <td>74</td>
    </tr>
    <tr>
      <th>3</th>
      <td>USC00519397</td>
      <td>2010-01-04</td>
      <td>0.00</td>
      <td>76</td>
    </tr>
    <tr>
      <th>5</th>
      <td>USC00519397</td>
      <td>2010-01-07</td>
      <td>0.06</td>
      <td>70</td>
    </tr>
    <tr>
      <th>6</th>
      <td>USC00519397</td>
      <td>2010-01-08</td>
      <td>0.00</td>
      <td>64</td>
    </tr>
    <tr>
      <th>7</th>
      <td>USC00519397</td>
      <td>2010-01-09</td>
      <td>0.00</td>
      <td>68</td>
    </tr>
    <tr>
      <th>8</th>
      <td>USC00519397</td>
      <td>2010-01-10</td>
      <td>0.00</td>
      <td>73</td>
    </tr>
    <tr>
      <th>9</th>
      <td>USC00519397</td>
      <td>2010-01-11</td>
      <td>0.01</td>
      <td>64</td>
    </tr>
    <tr>
      <th>10</th>
      <td>USC00519397</td>
      <td>2010-01-12</td>
      <td>0.00</td>
      <td>61</td>
    </tr>
    <tr>
      <th>11</th>
      <td>USC00519397</td>
      <td>2010-01-14</td>
      <td>0.00</td>
      <td>66</td>
    </tr>
    <tr>
      <th>12</th>
      <td>USC00519397</td>
      <td>2010-01-15</td>
      <td>0.00</td>
      <td>65</td>
    </tr>
    <tr>
      <th>13</th>
      <td>USC00519397</td>
      <td>2010-01-16</td>
      <td>0.00</td>
      <td>68</td>
    </tr>
    <tr>
      <th>14</th>
      <td>USC00519397</td>
      <td>2010-01-17</td>
      <td>0.00</td>
      <td>64</td>
    </tr>
    <tr>
      <th>15</th>
      <td>USC00519397</td>
      <td>2010-01-18</td>
      <td>0.00</td>
      <td>72</td>
    </tr>
    <tr>
      <th>16</th>
      <td>USC00519397</td>
      <td>2010-01-19</td>
      <td>0.00</td>
      <td>66</td>
    </tr>
    <tr>
      <th>17</th>
      <td>USC00519397</td>
      <td>2010-01-20</td>
      <td>0.00</td>
      <td>66</td>
    </tr>
    <tr>
      <th>18</th>
      <td>USC00519397</td>
      <td>2010-01-21</td>
      <td>0.00</td>
      <td>69</td>
    </tr>
    <tr>
      <th>19</th>
      <td>USC00519397</td>
      <td>2010-01-22</td>
      <td>0.00</td>
      <td>67</td>
    </tr>
    <tr>
      <th>20</th>
      <td>USC00519397</td>
      <td>2010-01-23</td>
      <td>0.00</td>
      <td>67</td>
    </tr>
    <tr>
      <th>21</th>
      <td>USC00519397</td>
      <td>2010-01-24</td>
      <td>0.01</td>
      <td>71</td>
    </tr>
    <tr>
      <th>22</th>
      <td>USC00519397</td>
      <td>2010-01-25</td>
      <td>0.00</td>
      <td>67</td>
    </tr>
    <tr>
      <th>23</th>
      <td>USC00519397</td>
      <td>2010-01-26</td>
      <td>0.04</td>
      <td>76</td>
    </tr>
    <tr>
      <th>24</th>
      <td>USC00519397</td>
      <td>2010-01-27</td>
      <td>0.12</td>
      <td>68</td>
    </tr>
    <tr>
      <th>25</th>
      <td>USC00519397</td>
      <td>2010-01-28</td>
      <td>0.00</td>
      <td>72</td>
    </tr>
    <tr>
      <th>27</th>
      <td>USC00519397</td>
      <td>2010-01-31</td>
      <td>0.03</td>
      <td>67</td>
    </tr>
    <tr>
      <th>28</th>
      <td>USC00519397</td>
      <td>2010-02-01</td>
      <td>0.01</td>
      <td>66</td>
    </tr>
    <tr>
      <th>30</th>
      <td>USC00519397</td>
      <td>2010-02-04</td>
      <td>0.01</td>
      <td>69</td>
    </tr>
    <tr>
      <th>31</th>
      <td>USC00519397</td>
      <td>2010-02-05</td>
      <td>0.00</td>
      <td>67</td>
    </tr>
    <tr>
      <th>32</th>
      <td>USC00519397</td>
      <td>2010-02-06</td>
      <td>0.00</td>
      <td>67</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>19513</th>
      <td>USC00516128</td>
      <td>2017-07-17</td>
      <td>0.39</td>
      <td>72</td>
    </tr>
    <tr>
      <th>19514</th>
      <td>USC00516128</td>
      <td>2017-07-18</td>
      <td>2.40</td>
      <td>77</td>
    </tr>
    <tr>
      <th>19515</th>
      <td>USC00516128</td>
      <td>2017-07-19</td>
      <td>0.27</td>
      <td>74</td>
    </tr>
    <tr>
      <th>19516</th>
      <td>USC00516128</td>
      <td>2017-07-20</td>
      <td>0.70</td>
      <td>75</td>
    </tr>
    <tr>
      <th>19517</th>
      <td>USC00516128</td>
      <td>2017-07-21</td>
      <td>0.10</td>
      <td>72</td>
    </tr>
    <tr>
      <th>19518</th>
      <td>USC00516128</td>
      <td>2017-07-22</td>
      <td>4.00</td>
      <td>72</td>
    </tr>
    <tr>
      <th>19519</th>
      <td>USC00516128</td>
      <td>2017-07-23</td>
      <td>0.80</td>
      <td>78</td>
    </tr>
    <tr>
      <th>19520</th>
      <td>USC00516128</td>
      <td>2017-07-24</td>
      <td>0.84</td>
      <td>77</td>
    </tr>
    <tr>
      <th>19521</th>
      <td>USC00516128</td>
      <td>2017-07-25</td>
      <td>0.30</td>
      <td>79</td>
    </tr>
    <tr>
      <th>19522</th>
      <td>USC00516128</td>
      <td>2017-07-26</td>
      <td>0.30</td>
      <td>73</td>
    </tr>
    <tr>
      <th>19523</th>
      <td>USC00516128</td>
      <td>2017-07-27</td>
      <td>0.00</td>
      <td>75</td>
    </tr>
    <tr>
      <th>19524</th>
      <td>USC00516128</td>
      <td>2017-07-28</td>
      <td>0.40</td>
      <td>73</td>
    </tr>
    <tr>
      <th>19525</th>
      <td>USC00516128</td>
      <td>2017-07-29</td>
      <td>0.30</td>
      <td>77</td>
    </tr>
    <tr>
      <th>19526</th>
      <td>USC00516128</td>
      <td>2017-07-30</td>
      <td>0.30</td>
      <td>79</td>
    </tr>
    <tr>
      <th>19527</th>
      <td>USC00516128</td>
      <td>2017-07-31</td>
      <td>0.00</td>
      <td>74</td>
    </tr>
    <tr>
      <th>19529</th>
      <td>USC00516128</td>
      <td>2017-08-02</td>
      <td>0.25</td>
      <td>80</td>
    </tr>
    <tr>
      <th>19530</th>
      <td>USC00516128</td>
      <td>2017-08-03</td>
      <td>0.06</td>
      <td>76</td>
    </tr>
    <tr>
      <th>19533</th>
      <td>USC00516128</td>
      <td>2017-08-07</td>
      <td>0.05</td>
      <td>78</td>
    </tr>
    <tr>
      <th>19534</th>
      <td>USC00516128</td>
      <td>2017-08-08</td>
      <td>0.34</td>
      <td>74</td>
    </tr>
    <tr>
      <th>19535</th>
      <td>USC00516128</td>
      <td>2017-08-09</td>
      <td>0.15</td>
      <td>71</td>
    </tr>
    <tr>
      <th>19536</th>
      <td>USC00516128</td>
      <td>2017-08-10</td>
      <td>0.07</td>
      <td>75</td>
    </tr>
    <tr>
      <th>19538</th>
      <td>USC00516128</td>
      <td>2017-08-12</td>
      <td>0.14</td>
      <td>74</td>
    </tr>
    <tr>
      <th>19540</th>
      <td>USC00516128</td>
      <td>2017-08-14</td>
      <td>0.22</td>
      <td>79</td>
    </tr>
    <tr>
      <th>19541</th>
      <td>USC00516128</td>
      <td>2017-08-15</td>
      <td>0.42</td>
      <td>70</td>
    </tr>
    <tr>
      <th>19542</th>
      <td>USC00516128</td>
      <td>2017-08-16</td>
      <td>0.42</td>
      <td>71</td>
    </tr>
    <tr>
      <th>19543</th>
      <td>USC00516128</td>
      <td>2017-08-17</td>
      <td>0.13</td>
      <td>72</td>
    </tr>
    <tr>
      <th>19545</th>
      <td>USC00516128</td>
      <td>2017-08-19</td>
      <td>0.09</td>
      <td>71</td>
    </tr>
    <tr>
      <th>19547</th>
      <td>USC00516128</td>
      <td>2017-08-21</td>
      <td>0.56</td>
      <td>76</td>
    </tr>
    <tr>
      <th>19548</th>
      <td>USC00516128</td>
      <td>2017-08-22</td>
      <td>0.50</td>
      <td>76</td>
    </tr>
    <tr>
      <th>19549</th>
      <td>USC00516128</td>
      <td>2017-08-23</td>
      <td>0.45</td>
      <td>76</td>
    </tr>
  </tbody>
</table>
<p>18103 rows × 4 columns</p>
</div>




```python
file_one_df.to_csv("clean_hiMeasurements.csv", index=False)
```


```python
file_two_df.to_csv("clean_hiStations.csv", index=False)
```
