
## 1. Bitcoin. Cryptocurrencies. So hot right now.
<p>Since the <a href="https://newfronttest.bitcoin.com/bitcoin.pdf">launch of Bitcoin in 2008</a>, hundreds of similar projects based on the blockchain technology have emerged. We call these cryptocurrencies (also coins or cryptos in the Internet slang). Some are extremely valuable nowadays, and others may have the potential to become extremely valuable in the future<sup>1</sup>. In fact, on the 6th of December of 2017, Bitcoin has a <a href="https://en.wikipedia.org/wiki/Market_capitalization">market capitalization</a> above $200 billion. </p>
<p><center>
<img src="https://assets.datacamp.com/production/project_82/img/bitcoint_market_cap_2017.png" style="width:500px"> <br> 
<em>The astonishing increase of Bitcoin market capitalization in 2017.</em></center></p>
<p>*<sup>1</sup> <strong>WARNING</strong>: The cryptocurrency market is exceptionally volatile and any money you put in might disappear into thin air.  Cryptocurrencies mentioned here <strong>might be scams</strong> similar to <a href="https://en.wikipedia.org/wiki/Ponzi_scheme">Ponzi Schemes</a> or have many other issues (overvaluation, technical, etc.). <strong>Please do not mistake this for investment advice</strong>. *</p>
<p>That said, let's get to business. As a first task, we will load the current data from the <a href="https://api.coinmarketcap.com">coinmarketcap API</a> and display it in the output.</p>


```python
# Importing pandas
import pandas as pd

# Importing matplotlib and setting aesthetics for plotting later.
import matplotlib.pyplot as plt
%matplotlib inline
%config InlineBackend.figure_format = 'svg' 
plt.style.use('fivethirtyeight')

# Reading in current data from coinmarketcap.com
current = pd.read_json("https://api.coinmarketcap.com/v1/ticker/")

# Printing out the first few lines
current.head(10)
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
      <th>24h_volume_usd</th>
      <th>available_supply</th>
      <th>id</th>
      <th>last_updated</th>
      <th>market_cap_usd</th>
      <th>max_supply</th>
      <th>name</th>
      <th>percent_change_1h</th>
      <th>percent_change_24h</th>
      <th>percent_change_7d</th>
      <th>price_btc</th>
      <th>price_usd</th>
      <th>rank</th>
      <th>symbol</th>
      <th>total_supply</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>4.181322e+10</td>
      <td>18251325</td>
      <td>bitcoin</td>
      <td>1583304815</td>
      <td>160824314652</td>
      <td>2.100000e+07</td>
      <td>Bitcoin</td>
      <td>-0.16</td>
      <td>-0.10</td>
      <td>-4.24</td>
      <td>1.000000</td>
      <td>8811.651464</td>
      <td>1</td>
      <td>BTC</td>
      <td>18251325</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.985934e+10</td>
      <td>109951871</td>
      <td>ethereum</td>
      <td>1583304804</td>
      <td>24847675563</td>
      <td>NaN</td>
      <td>Ethereum</td>
      <td>-0.30</td>
      <td>-1.21</td>
      <td>-5.77</td>
      <td>0.025651</td>
      <td>225.986836</td>
      <td>2</td>
      <td>ETH</td>
      <td>109951871</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2.487522e+09</td>
      <td>43779512655</td>
      <td>xrp</td>
      <td>1583304783</td>
      <td>10345770302</td>
      <td>1.000000e+11</td>
      <td>XRP</td>
      <td>0.24</td>
      <td>0.05</td>
      <td>-2.86</td>
      <td>0.000027</td>
      <td>0.236315</td>
      <td>3</td>
      <td>XRP</td>
      <td>99991072785</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2.904550e+10</td>
      <td>18311688</td>
      <td>bitcoin-cash</td>
      <td>1583304787</td>
      <td>6011312055</td>
      <td>2.100000e+07</td>
      <td>Bitcoin Cash</td>
      <td>-0.31</td>
      <td>-1.20</td>
      <td>-1.55</td>
      <td>0.037262</td>
      <td>328.277340</td>
      <td>4</td>
      <td>BCH</td>
      <td>18311688</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4.985315e+10</td>
      <td>4642367414</td>
      <td>tether</td>
      <td>1583304802</td>
      <td>4655585989</td>
      <td>NaN</td>
      <td>Tether</td>
      <td>0.33</td>
      <td>0.12</td>
      <td>0.15</td>
      <td>0.000114</td>
      <td>1.002847</td>
      <td>5</td>
      <td>USDT</td>
      <td>4776930644</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2.571168e+09</td>
      <td>18309077</td>
      <td>bitcoin-sv</td>
      <td>1583304790</td>
      <td>4515203826</td>
      <td>2.100000e+07</td>
      <td>Bitcoin SV</td>
      <td>-0.33</td>
      <td>-0.82</td>
      <td>4.37</td>
      <td>0.027992</td>
      <td>246.610127</td>
      <td>6</td>
      <td>BSV</td>
      <td>18309077</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5.372052e+09</td>
      <td>64215087</td>
      <td>litecoin</td>
      <td>1583304784</td>
      <td>3909287032</td>
      <td>8.400000e+07</td>
      <td>Litecoin</td>
      <td>-0.62</td>
      <td>0.15</td>
      <td>-10.70</td>
      <td>0.006910</td>
      <td>60.878015</td>
      <td>7</td>
      <td>LTC</td>
      <td>64215087</td>
    </tr>
    <tr>
      <th>7</th>
      <td>4.469829e+09</td>
      <td>920633224</td>
      <td>eos</td>
      <td>1583304787</td>
      <td>3356364529</td>
      <td>NaN</td>
      <td>EOS</td>
      <td>-0.41</td>
      <td>-0.47</td>
      <td>-7.09</td>
      <td>0.000414</td>
      <td>3.645713</td>
      <td>8</td>
      <td>EOS</td>
      <td>1017333236</td>
    </tr>
    <tr>
      <th>8</th>
      <td>3.793092e+08</td>
      <td>155536713</td>
      <td>binance-coin</td>
      <td>1583304785</td>
      <td>3128054117</td>
      <td>1.875367e+08</td>
      <td>Binance Coin</td>
      <td>-0.03</td>
      <td>1.70</td>
      <td>3.50</td>
      <td>0.002283</td>
      <td>20.111355</td>
      <td>9</td>
      <td>BNB</td>
      <td>187536713</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1.596776e+08</td>
      <td>702599556</td>
      <td>tezos</td>
      <td>1583304785</td>
      <td>2021424645</td>
      <td>NaN</td>
      <td>Tezos</td>
      <td>-2.21</td>
      <td>5.98</td>
      <td>8.49</td>
      <td>0.000327</td>
      <td>2.877065</td>
      <td>10</td>
      <td>XTZ</td>
      <td>702599556</td>
    </tr>
  </tbody>
</table>
</div>




```python
%%nose

import inspect
import pandas as pd

def test_current_is_a_data_frame():
    assert type(current) == pd.core.frame.DataFrame, \
    'The variable current should contain the DataFrame produced by read_json()'
    
def test_pandas_imported():
    assert inspect.ismodule(pd), 'Do not delete the "from pandas import pd" import'

def test_plt_imported():
    assert inspect.ismodule(plt), 'Do not delete the "import matplotlib.pyplot as plt "import'
```






    3/3 tests passed




## 2. Full dataset, filtering, and reproducibility
<p>The previous API call returns only the first 100 coins, and we want to explore as many coins as possible. Moreover, we can't produce reproducible analysis with live online data. To solve these problems, we will load a CSV we conveniently saved on the 6th of December of 2017 using the API call <code>https://api.coinmarketcap.com/v1/ticker/?limit=0</code> named <code>datasets/coinmarketcap_06122017.csv</code>. </p>


```python
# Reading datasets/coinmarketcap_06122017.csv into pandas
dec6 = pd.read_csv('datasets/coinmarketcap_06122017.csv')

# Selecting the 'id' and the 'market_cap_usd' columns
market_cap_raw = dec6[['id','market_cap_usd']]

# Counting the number of values
market_cap_raw.count()
```




    id                1326
    market_cap_usd    1031
    dtype: int64




```python
%%nose

def test_dec6_is_dataframe():
    assert type(dec6) == pd.core.frame.DataFrame, \
    'The variable dec6 should contain the DataFrame produced by read_csv()'

def test_market_cap_raw():
    assert list(market_cap_raw.columns) == ['id', 'market_cap_usd'], \
    'The variable market_cap_raw should contain the "id" and "market_cap_usd" columns exclusively'
```






    2/2 tests passed




## 3. Discard the cryptocurrencies without a market capitalization
<p>Why do the <code>count()</code> for <code>id</code> and <code>market_cap_usd</code> differ above? It is because some cryptocurrencies listed in coinmarketcap.com have no known market capitalization, this is represented by <code>NaN</code> in the data, and <code>NaN</code>s are not counted by <code>count()</code>. These cryptocurrencies are of little interest to us in this analysis, so they are safe to remove.</p>


```python
# Filtering out rows without a market capitalization
cap = market_cap_raw.query('market_cap_usd > 0')
#cap = market_cap_raw[market_cap_raw['market_cap_usd']>0]

# Counting the number of values again
cap.count()
```




    id                1031
    market_cap_usd    1031
    dtype: int64




```python
%%nose

def test_cap_filtered():
    assert cap.id.count() == cap.market_cap_usd.count(), 'id and market_cap_usd should have the same count'
    
def test_cap_small():
    assert cap.id.count() == 1031, 'The resulting amount of cryptos should be 1031'
```






    2/2 tests passed




## 4. How big is Bitcoin compared with the rest of the cryptocurrencies?
<p>At the time of writing, Bitcoin is under serious competition from other projects, but it is still dominant in market capitalization. Let's plot the market capitalization for the top 10 coins as a barplot to better visualize this.</p>


```python
#Declaring these now for later use in the plots
TOP_CAP_TITLE = 'Top 10 market capitalization'
TOP_CAP_YLABEL = '% of total cap'

# Selecting the first 10 rows and setting the index
cap10 = cap.head(10).set_index(cap.id[:10])

# Calculating market_cap_perc
cap10 = cap10.assign(market_cap_perc = lambda x: (x.market_cap_usd / cap.market_cap_usd.sum()) * 100)

# Plotting the barplot with the title defined above 
ax = cap10.plot.bar( x='id',y='market_cap_perc',title=TOP_CAP_TITLE)
#ax = cap10.plot.bar( x='id',y='market_cap_perc',title='Top 10 market capitalization')

# Annotating the y axis with the label defined above
ax.set_ylabel(TOP_CAP_YLABEL)
#ax.set_ylabel('% of total cap')

```




    Text(0,0.5,'% of total cap')




![svg](output_10_1.svg)



```python
%%nose

def test_len_cap10():
    assert len(cap10) == 10, 'cap10 needs to contain 10 rows'

def test_index():
    assert cap10.index.name == 'id', 'The index should be the "id" column'

def test_perc_correct():
    assert round(cap10.market_cap_perc.iloc[0], 2) == 56.92, 'the "market_cap_perc" formula is incorrect'
    
def test_title():
    assert ax.get_title() == TOP_CAP_TITLE, 'The title of the plot should be {}'.format(TOP_CAP_TITLE)

def test_ylabel():
    assert ax.get_ylabel() == TOP_CAP_YLABEL, 'The y-axis should be named {}'.format(TOP_CAP_YLABEL)
```






    5/5 tests passed




## 5. Making the plot easier to read and more informative
<p>While the plot above is informative enough, it can be improved. Bitcoin is too big, and the other coins are hard to distinguish because of this. Instead of the percentage, let's use a log<sup>10</sup> scale of the "raw" capitalization. Plus, let's use color to group similar coins and make the plot more informative<sup>1</sup>. </p>
<p>For the colors rationale: bitcoin-cash and bitcoin-gold are forks of the bitcoin <a href="https://en.wikipedia.org/wiki/Blockchain">blockchain</a><sup>2</sup>. Ethereum and Cardano both offer Turing Complete <a href="https://en.wikipedia.org/wiki/Smart_contract">smart contracts</a>. Iota and Ripple are not minable. Dash, Litecoin, and Monero get their own color.</p>
<p><sup>1</sup> <em>This coloring is a simplification. There are more differences and similarities that are not being represented here.</em></p>
<p><sup>2</sup> <em>The bitcoin forks are actually <strong>very</strong> different, but it is out of scope to talk about them here. Please see the warning above and do your own research.</em></p>


```python
# Colors for the bar plot
COLORS = ['orange', 'green', 'orange', 'cyan', 'cyan', 'blue', 'silver', 'orange', 'red', 'green']

# Plotting market_cap_usd as before but adding the colors and scaling the y-axis  
ax = cap10.plot.bar( x='id',y='market_cap_usd',title=TOP_CAP_TITLE, color =COLORS, log=True)

# Annotating the y axis with 'USD'
ax.set_ylabel("USD")

# Final touch! Removing the xlabel as it is not very informative
ax.set_xlabel('')
```




    Text(0.5,0,'')




![svg](output_13_1.svg)



```python
%%nose

def test_title():
    assert ax.get_title() == TOP_CAP_TITLE, 'The title of the plot should be {}'.format(TOP_CAP_TITLE)

def test_ylabel():
    assert ax.get_ylabel() == 'USD', 'The y-axis should be named {}'.format(TOP_CAP_YLABEL)
    
def test_xlabel():
    assert not ax.get_xlabel(), 'The X label should contain an empty string, currently it contains "{}"'.format(ax.get_xlabel())
    
def test_log_scale():
    assert ax.get_yaxis().get_scale() == 'log', \
    'The y-axis is not on a log10 scale. Do not transform the data yourself, use the pandas/matplotlib interface'
    
#def test_colors():
#    assert round(ax.patches[1].get_facecolor()[1], 3) == 0.502, 'The colors of the bars are not correct'
```






    4/4 tests passed




## 6. What is going on?! Volatility in cryptocurrencies
<p>The cryptocurrencies market has been spectacularly volatile since the first exchange opened. This notebook didn't start with a big, bold warning for nothing. Let's explore this volatility a bit more! We will begin by selecting and plotting the 24 hours and 7 days percentage change, which we already have available.</p>


```python
# Selecting the id, percent_change_24h and percent_change_7d columns
volatility = dec6[['id', 'percent_change_24h','percent_change_7d']]

# Setting the index to 'id' and dropping all NaN rows
volatility = volatility.set_index('id').dropna()

# Sorting the DataFrame by percent_change_24h in ascending order
volatility = volatility.sort_values('percent_change_24h', ascending=True)

# Checking the first few rows
print(volatility.head())
```

                   percent_change_24h  percent_change_7d
    id                                                  
    flappycoin                 -95.85             -96.61
    credence-coin              -94.22             -95.31
    coupecoin                  -93.93             -61.24
    tyrocoin                   -79.02             -87.43
    petrodollar                -76.55             542.96



```python
%%nose

def test_vol():
    assert list(volatility.columns) == ['percent_change_24h', 'percent_change_7d'], '"volatility" not loaded correctly'
    
def test_vol_index():
    assert list(volatility.index[:3]) == ['flappycoin', 'credence-coin', 'coupecoin'], \
    '"volatility" index is not set to "id", or data sorted incorrectly'
```






    2/2 tests passed




## 7. Well, we can already see that things are *a bit* crazy
<p>It seems you can lose a lot of money quickly on cryptocurrencies. Let's plot the top 10 biggest gainers and top 10 losers in market capitalization.</p>


```python
#Defining a function with 2 parameters, the series to plot and the title
def top10_subplot(volatility_series, title):
    # Making the subplot and the figure for two side by side plots
    fig, axes = plt.subplots(nrows=1, ncols=2, figsize=(10, 6))
    
    # Plotting with pandas the barchart for the top 10 losers
    ax = (volatility_series[:10].plot.bar(color='darkred', ax=axes[0]))
    
    # Setting the figure's main title to the text passed as parameter
    fig.suptitle(title)
    
    # Setting the ylabel to '% change'
    ax.set_ylabel('% change')
    
    # Same as above, but for the top 10 winners
    ax = (volatility_series[-10:].plot.bar(color='darkblue', ax=axes[1]))
    
    # Returning this for good practice, might use later
    return fig, ax

DTITLE = "24 hours top losers and winners"

# Calling the function above with the 24 hours period series and title DTITLE  
fig, ax = top10_subplot(volatility.percent_change_24h,DTITLE)
```


![svg](output_19_0.svg)



```python
%%nose

DTITLE = "24 hours top losers and winners"

def test_title():
    assert fig.get_children()[-1].get_text() == DTITLE, 'The title of the plot should be {}'.format(DTITLE)

def test_subplots():
    assert len(fig.get_axes()) == 2, 'The plot should have 2 subplots'
    
def test_ylabel():
    fig.get_axes()[0].get_ylabel() == '% change', 'y axis label should be set to % change'

def test_comet_coin():
    assert round(fig.get_children()[2].get_children()[3].get_height(), 0) == 252.0, \
    'The data on the winners plot is incorrect'
  
def test_tyrocoin():
    assert abs(round(fig.get_children()[1].get_children()[4].get_height(), 0)) == 77.0, \
    'The data on the losers plot is incorrect'

#def test_colors():
#    r, g, b, a = fig.get_axes()[0].patches[1].get_facecolor()
#    assert round(r, 1) and not round(g, 1) and not round(b, 1), 'The bars on the left plot are not red'
    
#def test_colors2():
#    r, g, b, a = fig.get_axes()[1].patches[1].get_facecolor()
#    assert not round(r, 1) and not round(g, 1) and round(b, 1), 'The bars on the left plot are not blue'
    

```






    5/5 tests passed




## 8. Ok, those are... interesting. Let's check the weekly Series too.
<p>800% daily increase?! Why are we doing this tutorial and not buying random coins?<sup>1</sup></p>
<p>After calming down, let's reuse the function defined above to see what is going weekly instead of daily.</p>
<p><em><sup>1</sup> Please take a moment to understand the implications of the red plots on how much value some cryptocurrencies lose in such short periods of time</em></p>


```python
# Sorting in ascending order
volatility7d = volatility.sort_values('percent_change_7d', ascending=True)

WTITLE = "Weekly top losers and winners"

# Calling the top10_subplot function
fig, ax = top10_subplot(volatility7d.percent_change_7d, WTITLE)
```


![svg](output_22_0.svg)



```python
%%nose

WTITLE = "Weekly top losers and winners"

def test_title():
    assert fig.get_children()[-1].get_text() == WTITLE, 'The title of the plot should be {}'.format(WTITLE)

def test_subplots():
    assert len(fig.get_axes()) == 2, 'The plot should have 2 subplots'
    
def test_ylabel():
    fig.get_axes()[0].get_ylabel() == '% change', "y axis label should be set to '% change'"
   
#def test_colors():
#    r, g, b, a = fig.get_axes()[0].patches[1].get_facecolor()
#    assert round(r, 1) and not round(g, 1) and not round(b, 1), 'The bars on the left plot are not red'
#    
#def test_colors2():
#    r, g, b, a = fig.get_axes()[1].patches[1].get_facecolor()
#    assert not round(r, 1) and not round(g, 1) and round(b, 1), 'The bars on the left plot are not blue'
    
def test_comet_coin():
    assert abs(round(fig.get_children()[2].get_children()[3].get_height(), 0)) == 543.0, \
    'The data on the gainers plot is incorrect'
  
def test_tyrocoin():
    assert abs(round(fig.get_children()[1].get_children()[4].get_height(), 0)) == 87.0, \
    'The data on the losers plot is incorrect'
```






    5/5 tests passed




## 9. How small is small?
<p>The names of the cryptocurrencies above are quite unknown, and there is a considerable fluctuation between the 1 and 7 days percentage changes. As with stocks, and many other financial products, the smaller the capitalization, the bigger the risk and reward. Smaller cryptocurrencies are less stable projects in general, and therefore even riskier investments than the bigger ones<sup>1</sup>. Let's classify our dataset based on Investopedia's capitalization <a href="https://www.investopedia.com/video/play/large-cap/">definitions</a> for company stocks. </p>
<p><sup>1</sup> <em>Cryptocurrencies are a new asset class, so they are not directly comparable to stocks. Furthermore, there are no limits set in stone for what a "small" or "large" stock is. Finally, some investors argue that bitcoin is similar to gold, this would make them more comparable to a <a href="https://www.investopedia.com/terms/c/commodity.asp">commodity</a> instead.</em></p>


```python
# Selecting everything bigger than 10 billion 
largecaps = cap.query('market_cap_usd>10000000000')

# Printing out largecaps
print(largecaps.head())
```

                 id  market_cap_usd
    0       bitcoin    2.130493e+11
    1      ethereum    4.352945e+10
    2  bitcoin-cash    2.529585e+10
    3          iota    1.475225e+10



```python
%%nose

def test_large():
    assert not largecaps.market_cap_usd.count() < 4, 'You filtered too much'
    
def test_small():
    assert not largecaps.market_cap_usd.count() > 4, "You didn't filter enough"
    
def test_order():
    assert largecaps.iloc[1].id == "ethereum", "The dataset is not in the right order, no need to manipulate it here"
```






    3/3 tests passed




## 10. Most coins are tiny
<p>Note that many coins are not comparable to large companies in market cap, so let's divert from the original Investopedia definition by merging categories.</p>
<p><em>This is all for now. Thanks for completing this project!</em></p>


```python
# Making a nice function for counting different marketcaps from the
# "cap" DataFrame. Returns an int.
# INSTRUCTORS NOTE: Since you made it to the end, consider it a gift :D
def capcount(query_string):
    return cap.query(query_string).count().id

# Labels for the plot
LABELS = ["biggish", "micro", "nano"]

# Using capcount count the biggish cryptos
biggish = capcount('market_cap_usd>300000000')

# Same as above for micro ...
micro = capcount('market_cap_usd>50000000 & market_cap_usd<300000000')

# ... and for nano
nano =  capcount('market_cap_usd<50000000')

# Making a list with the 3 counts
values = [biggish,micro, nano]
#print(values)
# Plotting them with matplotlib 
plt.bar(range(len(values)), values, tick_label =LABELS)
```




    <Container object of 3 artists>




![svg](output_28_1.svg)



```python
%%nose

def test_biggish():
    assert biggish == 39, 'biggish is not correct'
    
def test_micro():
    assert micro == 96, 'micro is not correct'

def test_nano():
    assert nano == 896, 'nano is not correct'

def test_lenvalues():
    assert len(values) == 3, "values list is not correct"
```






    4/4 tests passed



