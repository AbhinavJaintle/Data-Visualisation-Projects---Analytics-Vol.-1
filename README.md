# Data-Visualisation-Projects---Analytics-Vol.-1

## 1. Top 5 Cryptocurrencies over the years visualization:

```python
import pandas as pd
import numpy as np
```


```python
crypto_table = pd.read_csv('D:\Documents\crypto_project.csv')
```


```python
crypto_table.head()
```




<div>



<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Year</th>
      <th>Cryptocurrency</th>
      <th>Marekt Cap</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2013</td>
      <td>Bitcoin</td>
      <td>1.488567e+09</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2013</td>
      <td>Litecoin</td>
      <td>7.463702e+07</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2013</td>
      <td>Peercoin</td>
      <td>7.250187e+06</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2013</td>
      <td>Namecoin</td>
      <td>5.995997e+06</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2013</td>
      <td>Terracoin</td>
      <td>1.503099e+06</td>
    </tr>
  </tbody>
</table>
</div>




```python
crypto_table = crypto_table[['Year', 'Cryptocurrency', 'Marekt Cap']]
crypto_table.head()
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Year</th>
      <th>Cryptocurrency</th>
      <th>Marekt Cap</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2013</td>
      <td>Bitcoin</td>
      <td>1.488567e+09</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2013</td>
      <td>Litecoin</td>
      <td>7.463702e+07</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2013</td>
      <td>Peercoin</td>
      <td>7.250187e+06</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2013</td>
      <td>Namecoin</td>
      <td>5.995997e+06</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2013</td>
      <td>Terracoin</td>
      <td>1.503099e+06</td>
    </tr>
  </tbody>
</table>
</div>




```python
df = crypto_table
```


```python
df = df.set_index('Year')
```


```python
print(df)
```

         Cryptocurrency    Marekt Cap
    Year                             
    2013        Bitcoin  1.488567e+09
    2013       Litecoin  7.463702e+07
    2013       Peercoin  7.250187e+06
    2013       Namecoin  5.995997e+06
    2013      Terracoin  1.503099e+06
    ...             ...           ...
    2022       Litecoin  0.000000e+00
    2022   Bitcoin Cash  0.000000e+00
    2022            XRP  0.000000e+00
    2022   Binance Coin  0.000000e+00
    2022       Polkadot  0.000000e+00
    
    [160 rows x 2 columns]
    


```python
df.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Cryptocurrency</th>
      <th>Marekt Cap</th>
    </tr>
    <tr>
      <th>Year</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013</th>
      <td>Bitcoin</td>
      <td>1.488567e+09</td>
    </tr>
    <tr>
      <th>2013</th>
      <td>Litecoin</td>
      <td>7.463702e+07</td>
    </tr>
    <tr>
      <th>2013</th>
      <td>Peercoin</td>
      <td>7.250187e+06</td>
    </tr>
    <tr>
      <th>2013</th>
      <td>Namecoin</td>
      <td>5.995997e+06</td>
    </tr>
    <tr>
      <th>2013</th>
      <td>Terracoin</td>
      <td>1.503099e+06</td>
    </tr>
  </tbody>
</table>
</div>




```python
>>> new = df.reset_index().groupby(['Year', 'Cryptocurrency'])['Marekt Cap'].aggregate('first').unstack()
```


```python
new.head()
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Cryptocurrency</th>
      <th>BNB</th>
      <th>Binance Coin</th>
      <th>Bitcoin</th>
      <th>Bitcoin Cash</th>
      <th>Bitshares</th>
      <th>Dash</th>
      <th>Dogecoin</th>
      <th>Ethereun</th>
      <th>Litecoin</th>
      <th>Namecoin</th>
      <th>Peercoin</th>
      <th>Polkadot</th>
      <th>Terracoin</th>
      <th>Tether</th>
      <th>USD Coin</th>
      <th>XRP</th>
    </tr>
    <tr>
      <th>Year</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.488567e+09</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.000000e+00</td>
      <td>0.0</td>
      <td>0.000000e+00</td>
      <td>7.463702e+07</td>
      <td>5995997.19</td>
      <td>7250186.65</td>
      <td>0.0</td>
      <td>1503099.4</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.000000e+00</td>
    </tr>
    <tr>
      <th>2014</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>5.808862e+09</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.000000e+00</td>
      <td>31183528.2</td>
      <td>0.000000e+00</td>
      <td>3.172562e+08</td>
      <td>0.00</td>
      <td>39686572.39</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>6.447170e+07</td>
    </tr>
    <tr>
      <th>2015</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.654266e+09</td>
      <td>0.0</td>
      <td>14634629.73</td>
      <td>2.193979e+07</td>
      <td>0.0</td>
      <td>0.000000e+00</td>
      <td>6.447478e+07</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>2.788408e+08</td>
    </tr>
    <tr>
      <th>2016</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>6.477833e+09</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>4.436945e+07</td>
      <td>0.0</td>
      <td>9.147598e+08</td>
      <td>1.474841e+08</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>2.583910e+08</td>
    </tr>
    <tr>
      <th>2017</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.791198e+10</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>4.110192e+08</td>
      <td>0.0</td>
      <td>4.404480e+09</td>
      <td>3.907957e+08</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>2.294349e+09</td>
    </tr>
  </tbody>
</table>
</div>




```python
new.sort_values(list(new.columns),inplace=True)
new = new.sort_index()
```


```python
new.head()
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Cryptocurrency</th>
      <th>BNB</th>
      <th>Binance Coin</th>
      <th>Bitcoin</th>
      <th>Bitcoin Cash</th>
      <th>Bitshares</th>
      <th>Dash</th>
      <th>Dogecoin</th>
      <th>Ethereun</th>
      <th>Litecoin</th>
      <th>Namecoin</th>
      <th>Peercoin</th>
      <th>Polkadot</th>
      <th>Terracoin</th>
      <th>Tether</th>
      <th>USD Coin</th>
      <th>XRP</th>
    </tr>
    <tr>
      <th>Year</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.488567e+09</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.000000e+00</td>
      <td>0.0</td>
      <td>0.000000e+00</td>
      <td>7.463702e+07</td>
      <td>5995997.19</td>
      <td>7250186.65</td>
      <td>0.0</td>
      <td>1503099.4</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.000000e+00</td>
    </tr>
    <tr>
      <th>2014</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>5.808862e+09</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.000000e+00</td>
      <td>31183528.2</td>
      <td>0.000000e+00</td>
      <td>3.172562e+08</td>
      <td>0.00</td>
      <td>39686572.39</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>6.447170e+07</td>
    </tr>
    <tr>
      <th>2015</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.654266e+09</td>
      <td>0.0</td>
      <td>14634629.73</td>
      <td>2.193979e+07</td>
      <td>0.0</td>
      <td>0.000000e+00</td>
      <td>6.447478e+07</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>2.788408e+08</td>
    </tr>
    <tr>
      <th>2016</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>6.477833e+09</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>4.436945e+07</td>
      <td>0.0</td>
      <td>9.147598e+08</td>
      <td>1.474841e+08</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>2.583910e+08</td>
    </tr>
    <tr>
      <th>2017</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.791198e+10</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>4.110192e+08</td>
      <td>0.0</td>
      <td>4.404480e+09</td>
      <td>3.907957e+08</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>2.294349e+09</td>
    </tr>
  </tbody>
</table>
</div>




```python
import bar_chart_race as bcr
```


```python
# for col in new:
#         new[col]=new[col].convert_dtypes()
```


```python
new.head()
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Cryptocurrency</th>
      <th>BNB</th>
      <th>Binance Coin</th>
      <th>Bitcoin</th>
      <th>Bitcoin Cash</th>
      <th>Bitshares</th>
      <th>Dash</th>
      <th>Dogecoin</th>
      <th>Ethereun</th>
      <th>Litecoin</th>
      <th>Namecoin</th>
      <th>Peercoin</th>
      <th>Polkadot</th>
      <th>Terracoin</th>
      <th>Tether</th>
      <th>USD Coin</th>
      <th>XRP</th>
    </tr>
    <tr>
      <th>Year</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.488567e+09</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.000000e+00</td>
      <td>0.0</td>
      <td>0.000000e+00</td>
      <td>7.463702e+07</td>
      <td>5995997.19</td>
      <td>7250186.65</td>
      <td>0.0</td>
      <td>1503099.4</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.000000e+00</td>
    </tr>
    <tr>
      <th>2014</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>5.808862e+09</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>0.000000e+00</td>
      <td>31183528.2</td>
      <td>0.000000e+00</td>
      <td>3.172562e+08</td>
      <td>0.00</td>
      <td>39686572.39</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>6.447170e+07</td>
    </tr>
    <tr>
      <th>2015</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>3.654266e+09</td>
      <td>0.0</td>
      <td>14634629.73</td>
      <td>2.193979e+07</td>
      <td>0.0</td>
      <td>0.000000e+00</td>
      <td>6.447478e+07</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>2.788408e+08</td>
    </tr>
    <tr>
      <th>2016</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>6.477833e+09</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>4.436945e+07</td>
      <td>0.0</td>
      <td>9.147598e+08</td>
      <td>1.474841e+08</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>2.583910e+08</td>
    </tr>
    <tr>
      <th>2017</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>1.791198e+10</td>
      <td>0.0</td>
      <td>0.00</td>
      <td>4.110192e+08</td>
      <td>0.0</td>
      <td>4.404480e+09</td>
      <td>3.907957e+08</td>
      <td>0.00</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>2.294349e+09</td>
    </tr>
  </tbody>
</table>
</div>




```python


bcr.bar_chart_race(df = new.head(12), 
                   n_bars = 5, 
                   sort='desc',
                   dpi=300,
                   title='Top 5 Cryptocurrencies Over the Years',
                   period_length=500,
                   figsize = (5,5))


```

    C:\Users\imabh\anaconda3\lib\site-packages\bar_chart_race\_make_chart.py:286: UserWarning: FixedFormatter should only be used together with FixedLocator
      ax.set_yticklabels(self.df_values.columns)
    C:\Users\imabh\anaconda3\lib\site-packages\bar_chart_race\_make_chart.py:287: UserWarning: FixedFormatter should only be used together with FixedLocator
      ax.set_xticklabels([max_val] * len(ax.get_xticks()))
    




https://user-images.githubusercontent.com/86119205/178377863-44f1d0d0-49fe-4e26-be5d-0a317f50d7df.mp4








```python

```


```python

```




## 2. Histogram for Data Analytics of News Agregation Project:

```python
import pandas as pd
import numpy as np
from matplotlib.pyplot import hist
import math
```


```python
df = pd.DataFrame({"No_of_Words": [2534, 4054, 2256, 2100, 3401, 2873, 1978, 954, 2940, 2582, 2245, 1518, 1525, 1286, 5725, 2818, 3784, 1009, 1206, 1769, 1768, 1603, 1622, 1865, 3173, 2947, 2459, 1102, 2498, 3740, 1223, 1274, 1581, 1683, 770, 2658, 2250, 1851, 1366, 2285, 2806, 1031, 2828, 1808, 1192, 2713, 1259, 805, 1602, 3671, 2195, 3220, 1937, 2342, 1839, 3095, 1714, 1922, 2188, 1793, 2457, 1818, 8044, 4846, 2867, 4563, 3359, 2598, 3699, 2811, 2087, 1725, 2882, 3085, 2664, 2001, 9838, 1925, 2538, 2296, 3770, 2623, 2477, 2339, 3240, 2104, 3006, 1683, 1281, 3132, 2150, 2057, 3024, 11526, 2182, 1541, 1253, 1607, 2467, 3188, 1223], "Log_of_words": [11, 11, 11, 11, 11, 11, 10, 9, 11, 11, 11, 10, 10, 10, 12, 11, 11, 9, 10, 10, 10, 10, 10, 10, 11, 11, 11, 10, 11, 11, 10, 10, 10, 10, 9, 11, 11, 10, 10, 11, 11, 10, 11, 10, 10, 11, 10, 9, 10, 11, 11, 11, 10, 11, 10, 11, 10, 10, 11, 10, 11, 10, 12, 12, 11, 12, 11, 11, 11, 11, 11, 10, 11, 11, 11, 10, 13, 10, 11, 11, 11, 11, 11, 11, 11, 11, 11, 10, 10, 11, 11, 11, 11, 13, 11, 10, 10, 10, 11, 11, 10], "No_of_LNE": [4, 9, 5, 3, 6, 7, 2, 5, 6, 11, 2, 6, 3, 3, 7, 6, 3, 0, 0, 0, 9, 3, 2, 4, 10, 12, 8, 4, 5, 5, 3, 2, 2, 5, 4, 14, 7, 3, 5, 9, 8, 4, 12, 3, 4, 11, 5, 1, 9, 13, 8, 1, 5, 10, 3, 7, 1, 3, 4, 3, 5, 5, 34, 20, 14, 15, 20, 12, 18, 10, 6, 4, 8, 11, 13, 9, 25, 5, 5, 8, 6, 10, 5, 6, 16, 14, 2, 6, 4, 11, 6, 9, 9, 32, 9, 4, 8, 6, 6, 9, 4], "Most_Frequent_LNE": [1, 4, 6, 1, 3, 5, 1, 2, 3, 4, 2, 1, 1, 1, 1, 6, 5, 0, 0, 0, 1, 1, 1, 3, 3, 2, 4, 1, 3, 1, 2, 1, 1, 2, 2, 3, 3, 2, 1, 5, 5, 1, 2, 1, 1, 5, 4, 1, 1, 5, 6, 1, 7, 1, 1, 5, 1, 1, 1, 1, 1, 2, 7, 4, 5, 4, 2, 4, 3, 2, 2, 2, 3, 6, 4, 5, 23, 4, 3, 3, 10, 9, 2, 2, 2, 4, 1, 1, 1, 3, 4, 5, 9, 14, 4, 2, 2, 2, 2, 2, 2], "LNE_Density": [0.36363636363636365, 0.8181818181818182, 0.45454545454545453, 0.2727272727272727, 0.5454545454545454, 0.6363636363636364, 0.2, 0.5555555555555556, 0.5454545454545454, 1.0, 0.18181818181818182, 0.6, 0.3, 0.3, 0.5833333333333334, 0.5454545454545454, 0.2727272727272727, 0.0, 0.0, 0.0, 0.9, 0.3, 0.2, 0.4, 0.9090909090909091, 1.0909090909090908, 0.7272727272727273, 0.4, 0.45454545454545453, 0.45454545454545453, 0.3, 0.2, 0.2, 0.5, 0.4444444444444444, 1.2727272727272727, 0.6363636363636364, 0.3, 0.5, 0.8181818181818182, 0.7272727272727273, 0.4, 1.0909090909090908, 0.3, 0.4, 1.0, 0.5, 0.1111111111111111, 0.9, 1.1818181818181819, 0.7272727272727273, 0.09090909090909091, 0.5, 0.9090909090909091, 0.3, 0.6363636363636364, 0.1, 0.3, 0.36363636363636365, 0.3, 0.45454545454545453, 0.5, 2.8333333333333335, 1.6666666666666667, 1.2727272727272727, 1.25, 1.8181818181818181, 1.0909090909090908, 1.6363636363636365, 0.9090909090909091, 0.5454545454545454, 0.4, 0.7272727272727273, 1.0, 1.1818181818181819, 0.9, 1.9230769230769231, 0.5, 0.45454545454545453, 0.7272727272727273, 0.5454545454545454, 0.9090909090909091, 0.45454545454545453, 0.5454545454545454, 1.4545454545454546, 1.2727272727272727, 0.18181818181818182, 0.6, 0.4, 1.0, 0.5454545454545454, 0.8181818181818182, 0.8181818181818182, 2.4615384615384617, 0.8181818181818182, 0.4, 0.8, 0.6, 0.5454545454545454, 0.8181818181818182, 0.4]}
)
print(df)
```

         No_of_Words  Log_of_words  No_of_LNE  Most_Frequent_LNE  LNE_Density
    0           2534            11          4                  1     0.363636
    1           4054            11          9                  4     0.818182
    2           2256            11          5                  6     0.454545
    3           2100            11          3                  1     0.272727
    4           3401            11          6                  3     0.545455
    ..           ...           ...        ...                ...          ...
    96          1253            10          8                  2     0.800000
    97          1607            10          6                  2     0.600000
    98          2467            11          6                  2     0.545455
    99          3188            11          9                  2     0.818182
    100         1223            10          4                  2     0.400000
    
    [101 rows x 5 columns]
    


```python
ax = df.plot.hist(y="No_of_Words")
ax = df.plot.hist(y="Log_of_words")
ax = df.plot.hist(y="No_of_LNE")
ax = df.plot.hist(y="Most_Frequent_LNE")
ax = df.plot.hist(y="LNE_Density")
```


![output_2_0](https://user-images.githubusercontent.com/86119205/178457651-98ad9475-b3ec-4414-840a-27d7635b148c.png)    
![output_2_1](https://user-images.githubusercontent.com/86119205/178457655-306fd02f-d9f3-4050-a7a9-b60ab97be801.png)
![output_2_2](https://user-images.githubusercontent.com/86119205/178457665-a4c19961-d27e-49dc-871c-0ce692763faa.png)
![output_2_3](https://user-images.githubusercontent.com/86119205/178457673-a306d583-dac7-42e7-895e-776682dad3c1.png)
![output_2_4](https://user-images.githubusercontent.com/86119205/178457681-d55c987d-ad0a-4088-8500-a2ab4ea67b7c.png)

```python

```


## 3. RoI on Various Investments over the years:

```python
import pandas as pd
import numpy as np
import matplotlib.animation as animation
from IPython import display
```


```python
investment_table = pd.read_csv('D:\Documents\Investment_increase1.csv')
```


```python
investment_table.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Year</th>
      <th>Investment</th>
      <th>Increase</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2019</td>
      <td>Nifty 50 Index</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2020</td>
      <td>Nifty 50 Index</td>
      <td>-19.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2021</td>
      <td>Nifty 50 Index</td>
      <td>62.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2022</td>
      <td>Nifty 50 Index</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2019</td>
      <td>Gold</td>
      <td>12.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
df = investment_table
```


```python
df = df.set_index('Year')
```


```python
print(df)
```

              Investment  Increase
    Year                          
    2019  Nifty 50 Index      11.0
    2020  Nifty 50 Index     -19.0
    2021  Nifty 50 Index      62.0
    2022  Nifty 50 Index       5.0
    2019            Gold      12.0
    2020            Gold      38.0
    2021            Gold       0.1
    2022            Gold       8.0
    2019          Silver      -5.0
    2020          Silver      23.0
    2021          Silver      49.0
    2022          Silver     -21.0
    2019        Yes Bank     -53.0
    2020        Yes Bank     -83.0
    2021        Yes Bank     -53.0
    2022        Yes Bank      10.0
    


```python
new = df.reset_index().groupby(['Year', 'Investment'])['Increase'].aggregate('first').unstack()
```


```python
new.head()
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Investment</th>
      <th>Gold</th>
      <th>Nifty 50 Index</th>
      <th>Silver</th>
      <th>Yes Bank</th>
    </tr>
    <tr>
      <th>Year</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2019</th>
      <td>12.0</td>
      <td>11.0</td>
      <td>-5.0</td>
      <td>-53.0</td>
    </tr>
    <tr>
      <th>2020</th>
      <td>38.0</td>
      <td>-19.0</td>
      <td>23.0</td>
      <td>-83.0</td>
    </tr>
    <tr>
      <th>2021</th>
      <td>0.1</td>
      <td>62.0</td>
      <td>49.0</td>
      <td>-53.0</td>
    </tr>
    <tr>
      <th>2022</th>
      <td>8.0</td>
      <td>5.0</td>
      <td>-21.0</td>
      <td>10.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
new.sort_values(list(new.columns),inplace=True)
new = new.sort_index()
```


```python
new.head()
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Investment</th>
      <th>Gold</th>
      <th>Nifty 50 Index</th>
      <th>Silver</th>
      <th>Yes Bank</th>
    </tr>
    <tr>
      <th>Year</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2019</th>
      <td>12.0</td>
      <td>11.0</td>
      <td>-5.0</td>
      <td>-53.0</td>
    </tr>
    <tr>
      <th>2020</th>
      <td>38.0</td>
      <td>-19.0</td>
      <td>23.0</td>
      <td>-83.0</td>
    </tr>
    <tr>
      <th>2021</th>
      <td>0.1</td>
      <td>62.0</td>
      <td>49.0</td>
      <td>-53.0</td>
    </tr>
    <tr>
      <th>2022</th>
      <td>8.0</td>
      <td>5.0</td>
      <td>-21.0</td>
      <td>10.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
import bar_chart_race as bcr
```


```python
anim = bcr.bar_chart_race(df = new, 
                   n_bars = 4, 
                   sort='desc',
                   dpi=300,
                   title='Percentage Return',
                   period_length=2500,
                   figsize = (4,4))
```

    C:\Users\imabh\anaconda3\lib\site-packages\bar_chart_race\_make_chart.py:286: UserWarning: FixedFormatter should only be used together with FixedLocator
      ax.set_yticklabels(self.df_values.columns)
    C:\Users\imabh\anaconda3\lib\site-packages\bar_chart_race\_make_chart.py:287: UserWarning: FixedFormatter should only be used together with FixedLocator
      ax.set_xticklabels([max_val] * len(ax.get_xticks()))
    


```python
# writervideo = animation.FFMpegWriter(fps=60)
# anim.save('increasingStraightLine.mp4', writer=writervideo)

# html = display.HTML(anim)
  
# draw the animation
display.display(anim)
```



https://user-images.githubusercontent.com/86119205/178460290-9e261a16-257c-4465-a77f-b84b45bae7df.mp4





```python

```



## 4. Major Indian Banking Stocks Market Cap Comparison Analysis:

```python
import pandas as pd
import numpy as np
```


```python
import seaborn as sns
import matplotlib.pyplot as plt
```


```python
stocks_table = pd.read_csv('D:\Documents\stock market cap.csv')
```


```python
stocks_table.head()
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Month</th>
      <th>Stock</th>
      <th>Open</th>
      <th>Shares</th>
      <th>Market Cap</th>
      <th>Unnamed: 5</th>
      <th>Unnamed: 6</th>
      <th>Unnamed: 7</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2021-01</td>
      <td>Equitas Holdings Limited</td>
      <td>68.1</td>
      <td>4,22,894</td>
      <td>28799081.4</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2021-02</td>
      <td>Equitas Holdings Limited</td>
      <td>72.1</td>
      <td>7,08,589</td>
      <td>51089266.9</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2021-03</td>
      <td>Equitas Holdings Limited</td>
      <td>86</td>
      <td>9,02,446</td>
      <td>77610356.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2021-04</td>
      <td>Equitas Holdings Limited</td>
      <td>87.3</td>
      <td>4,76,932</td>
      <td>41636163.6</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>21-Jan</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2021-05</td>
      <td>Equitas Holdings Limited</td>
      <td>81</td>
      <td>3,46,666</td>
      <td>28079946.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2021-01</td>
    </tr>
  </tbody>
</table>
</div>




```python
stocks_table = stocks_table[['Month', 'Stock', 'Market Cap']]
stocks_table.head()
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Month</th>
      <th>Stock</th>
      <th>Market Cap</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2021-01</td>
      <td>Equitas Holdings Limited</td>
      <td>28799081.4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2021-02</td>
      <td>Equitas Holdings Limited</td>
      <td>51089266.9</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2021-03</td>
      <td>Equitas Holdings Limited</td>
      <td>77610356.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2021-04</td>
      <td>Equitas Holdings Limited</td>
      <td>41636163.6</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2021-05</td>
      <td>Equitas Holdings Limited</td>
      <td>28079946.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
df = stocks_table
```


```python
df = df.set_index('Month')
```


```python
print(df)
```

                                    Stock  Market Cap
    Month                                            
    2021-01      Equitas Holdings Limited  28799081.4
    2021-02      Equitas Holdings Limited  51089266.9
    2021-03      Equitas Holdings Limited  77610356.0
    2021-04      Equitas Holdings Limited  41636163.6
    2021-05      Equitas Holdings Limited  28079946.0
    ...                               ...         ...
    2022-01  Suryodaya Small Finance Bank   8414133.0
    2022-02  Suryodaya Small Finance Bank   3749942.0
    2022-03  Suryodaya Small Finance Bank   2799312.0
    2022-04  Suryodaya Small Finance Bank  36078712.0
    2022-05  Suryodaya Small Finance Bank  13988565.0
    
    [68 rows x 2 columns]
    


```python
new = df.reset_index().groupby(['Month', 'Stock'])['Market Cap'].aggregate('first').unstack()
```


```python
new.head()
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Stock</th>
      <th>AU Small Finance Bank</th>
      <th>Equitas Holdings Limited</th>
      <th>Suryodaya Small Finance Bank</th>
      <th>Ujjivan Small Finance Bank</th>
    </tr>
    <tr>
      <th>Month</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2021-01</th>
      <td>3.253061e+08</td>
      <td>28799081.4</td>
      <td>0.0</td>
      <td>18714680.0</td>
    </tr>
    <tr>
      <th>2021-02</th>
      <td>1.284589e+09</td>
      <td>51089266.9</td>
      <td>0.0</td>
      <td>51222058.8</td>
    </tr>
    <tr>
      <th>2021-03</th>
      <td>5.142770e+08</td>
      <td>77610356.0</td>
      <td>0.0</td>
      <td>32713532.8</td>
    </tr>
    <tr>
      <th>2021-04</th>
      <td>2.804738e+08</td>
      <td>41636163.6</td>
      <td>18529260.0</td>
      <td>37162325.2</td>
    </tr>
    <tr>
      <th>2021-05</th>
      <td>2.540412e+09</td>
      <td>28079946.0</td>
      <td>32791806.0</td>
      <td>18195425.6</td>
    </tr>
  </tbody>
</table>
</div>




```python
print(new)
```

    Stock    AU Small Finance Bank  Equitas Holdings Limited  \
    Month                                                      
    2021-01           3.253061e+08                28799081.4   
    2021-02           1.284589e+09                51089266.9   
    2021-03           5.142770e+08                77610356.0   
    2021-04           2.804738e+08                41636163.6   
    2021-05           2.540412e+09                28079946.0   
    2021-06           1.237163e+08                86020184.0   
    2021-07           2.440552e+08                34210736.0   
    2021-08           6.723441e+08               224714562.0   
    2021-09           1.194545e+09                88079040.0   
    2021-10           2.918398e+08                51150451.0   
    2021-11           2.392134e+08                41357160.0   
    2021-12           2.715716e+08                50002875.0   
    2022-01           4.329208e+08               321263526.0   
    2022-02           7.199038e+08                32780990.0   
    2022-03           4.628563e+08                24587115.0   
    2022-04           6.816730e+08                23079686.0   
    2022-05           6.030724e+08                36069228.0   
    
    Stock    Suryodaya Small Finance Bank  Ujjivan Small Finance Bank  
    Month                                                              
    2021-01                           0.0                  18714680.0  
    2021-02                           0.0                  51222058.8  
    2021-03                           0.0                  32713532.8  
    2021-04                    18529260.0                  37162325.2  
    2021-05                    32791806.0                  18195425.6  
    2021-06                    11281387.0                  22511160.0  
    2021-07                     8854365.0                  21603797.6  
    2021-08                     8810672.0                  60503628.0  
    2021-09                     8756037.0                  33159416.4  
    2021-10                     5346900.0                  32969434.4  
    2021-11                     4182360.0                  49840807.5  
    2021-12                     6427768.0                   8988872.5  
    2022-01                     8414133.0                  20353961.4  
    2022-02                     3749942.0                   9206173.0  
    2022-03                     2799312.0                  11688122.4  
    2022-04                    36078712.0                  28435550.8  
    2022-05                    13988565.0                   6447402.5  
    


```python
new.sort_values(list(new.columns),inplace=True)
new = new.sort_index()
```


```python
new.head()
```




<div>

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Stock</th>
      <th>AU Small Finance Bank</th>
      <th>Equitas Holdings Limited</th>
      <th>Suryodaya Small Finance Bank</th>
      <th>Ujjivan Small Finance Bank</th>
    </tr>
    <tr>
      <th>Month</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2021-01</th>
      <td>3.253061e+08</td>
      <td>28799081.4</td>
      <td>0.0</td>
      <td>18714680.0</td>
    </tr>
    <tr>
      <th>2021-02</th>
      <td>1.284589e+09</td>
      <td>51089266.9</td>
      <td>0.0</td>
      <td>51222058.8</td>
    </tr>
    <tr>
      <th>2021-03</th>
      <td>5.142770e+08</td>
      <td>77610356.0</td>
      <td>0.0</td>
      <td>32713532.8</td>
    </tr>
    <tr>
      <th>2021-04</th>
      <td>2.804738e+08</td>
      <td>41636163.6</td>
      <td>18529260.0</td>
      <td>37162325.2</td>
    </tr>
    <tr>
      <th>2021-05</th>
      <td>2.540412e+09</td>
      <td>28079946.0</td>
      <td>32791806.0</td>
      <td>18195425.6</td>
    </tr>
  </tbody>
</table>
</div>




```python
import bar_chart_race as bcr
```


```python


bcr.bar_chart_race(df = new, 
                   n_bars = 4, 
                   sort='desc',
                   dpi=300,
                   title='Banking Stocks Market Cap',
                   period_length=800,
                   figsize = (2.5,2.5))


```


https://user-images.githubusercontent.com/86119205/178462474-f882a1df-a9dd-4c16-9314-3bada0778e46.mp4




    C:\Users\imabh\anaconda3\lib\site-packages\bar_chart_race\_make_chart.py:286: UserWarning: FixedFormatter should only be used together with FixedLocator
      ax.set_yticklabels(self.df_values.columns)
    C:\Users\imabh\anaconda3\lib\site-packages\bar_chart_race\_make_chart.py:287: UserWarning: FixedFormatter should only be used together with FixedLocator
      ax.set_xticklabels([max_val] * len(ax.get_xticks()))
    





```python
plots = sns.barplot(x="Stock", y="Market Cap", data=df)
```

    

![output_15_0](https://user-images.githubusercontent.com/86119205/178462224-61420d18-485e-47e3-92f3-82753e359eb6.png)


```python

```


