```python
import pandas as pd 
```

문제 1) 데이터를 로드하라. 데이터는 탭(\t)을 기준으로 구분되어 있다.

* 롤 랭킹 데이터 : https://www.kaggle.com/datasnaek/league-of-legends
* DataUrl = ‘https://raw.githubusercontent.com/Datamanim/pandas/main/lol.csv’


```python
DataUrl = 'https://raw.githubusercontent.com/Datamanim/pandas/main/lol.csv'
df = pd.read_csv(DataUrl,sep='\t')
```


```python
type(df)
```




    pandas.core.frame.DataFrame



문제 2) 데이터의 상위 5개 행을 출력하라


```python
Ans = df.head(5)
Ans
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
      <th>gameId</th>
      <th>creationTime</th>
      <th>gameDuration</th>
      <th>seasonId</th>
      <th>winner</th>
      <th>firstBlood</th>
      <th>firstTower</th>
      <th>firstInhibitor</th>
      <th>firstBaron</th>
      <th>firstDragon</th>
      <th>...</th>
      <th>t2_towerKills</th>
      <th>t2_inhibitorKills</th>
      <th>t2_baronKills</th>
      <th>t2_dragonKills</th>
      <th>t2_riftHeraldKills</th>
      <th>t2_ban1</th>
      <th>t2_ban2</th>
      <th>t2_ban3</th>
      <th>t2_ban4</th>
      <th>t2_ban5</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>3326086514</td>
      <td>1504279457970</td>
      <td>1949</td>
      <td>9</td>
      <td>1</td>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>...</td>
      <td>5</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>114</td>
      <td>67</td>
      <td>43</td>
      <td>16</td>
      <td>51</td>
    </tr>
    <tr>
      <th>1</th>
      <td>3229566029</td>
      <td>1497848803862</td>
      <td>1851</td>
      <td>9</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>...</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>11</td>
      <td>67</td>
      <td>238</td>
      <td>51</td>
      <td>420</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3327363504</td>
      <td>1504360103310</td>
      <td>1493</td>
      <td>9</td>
      <td>1</td>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>2</td>
      <td>...</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>157</td>
      <td>238</td>
      <td>121</td>
      <td>57</td>
      <td>28</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3326856598</td>
      <td>1504348503996</td>
      <td>1758</td>
      <td>9</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>164</td>
      <td>18</td>
      <td>141</td>
      <td>40</td>
      <td>51</td>
    </tr>
    <tr>
      <th>4</th>
      <td>3330080762</td>
      <td>1504554410899</td>
      <td>2094</td>
      <td>9</td>
      <td>1</td>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>...</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>86</td>
      <td>11</td>
      <td>201</td>
      <td>122</td>
      <td>18</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 61 columns</p>
</div>



문제 3) 데이터의 행과 열의 갯수를 파악하라


```python
print(df.shape)
print('행:',df.shape[0])
print('열:',df.shape[1])
```

    (51490, 61)
    행: 51490
    열: 61
    

문제 4) 전체 칼럼을 출력


```python
Ans = df.columns
Ans
```




    Index(['gameId', 'creationTime', 'gameDuration', 'seasonId', 'winner',
           'firstBlood', 'firstTower', 'firstInhibitor', 'firstBaron',
           'firstDragon', 'firstRiftHerald', 't1_champ1id', 't1_champ1_sum1',
           't1_champ1_sum2', 't1_champ2id', 't1_champ2_sum1', 't1_champ2_sum2',
           't1_champ3id', 't1_champ3_sum1', 't1_champ3_sum2', 't1_champ4id',
           't1_champ4_sum1', 't1_champ4_sum2', 't1_champ5id', 't1_champ5_sum1',
           't1_champ5_sum2', 't1_towerKills', 't1_inhibitorKills', 't1_baronKills',
           't1_dragonKills', 't1_riftHeraldKills', 't1_ban1', 't1_ban2', 't1_ban3',
           't1_ban4', 't1_ban5', 't2_champ1id', 't2_champ1_sum1', 't2_champ1_sum2',
           't2_champ2id', 't2_champ2_sum1', 't2_champ2_sum2', 't2_champ3id',
           't2_champ3_sum1', 't2_champ3_sum2', 't2_champ4id', 't2_champ4_sum1',
           't2_champ4_sum2', 't2_champ5id', 't2_champ5_sum1', 't2_champ5_sum2',
           't2_towerKills', 't2_inhibitorKills', 't2_baronKills', 't2_dragonKills',
           't2_riftHeraldKills', 't2_ban1', 't2_ban2', 't2_ban3', 't2_ban4',
           't2_ban5'],
          dtype='object')



문제 5) 6번째 칼럼 이름을 출력


```python
Ans = df.columns[5]
Ans
```




    'firstBlood'



문제 6) 6번째 칼럼의 데이터 타입은?


```python
Ans = df.iloc[:,5].dtype
Ans
```




    dtype('int64')



문제 7) 데이터셋의 인덱스 구성은?


```python
Ans = df.index
Ans
```




    RangeIndex(start=0, stop=51490, step=1)



문제 8) 6번째 컬럼의 3번째 값은?


```python
Ans = df.iloc[2,5]
```


```python

```
