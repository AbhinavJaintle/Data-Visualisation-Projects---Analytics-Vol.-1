# Data-Visualisation-Projects---Analytics-Vol.-1

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
