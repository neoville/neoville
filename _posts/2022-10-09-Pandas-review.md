    준비: Pandas import


```python
# 판다스, 넘파이 불러오기
import pandas as pd
import numpy as np
```

    객체 생성(Object creation): 여러 값들로 이루어진 list로부터 Series 만들기


```python
s = pd.Series([1, 3, 5, np.nan, 6, 8])

s
```




    0    1.0
    1    3.0
    2    5.0
    3    NaN
    4    6.0
    5    8.0
    dtype: float64



DataFrame 생성: _range() 함수를 이용하여 Numpy array로부터 


```python
dates = pd.date_range("20130101", periods=6)

dates
```




    DatetimeIndex(['2013-01-01', '2013-01-02', '2013-01-03', '2013-01-04',
                   '2013-01-05', '2013-01-06'],
                  dtype='datetime64[ns]', freq='D')




```python
df = pd.DataFrame(np.random.randn(6, 4), index=dates, columns=list("ABCD"))

df
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-01</th>
      <td>-0.690236</td>
      <td>-0.503255</td>
      <td>-0.161739</td>
      <td>0.272396</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>0.320978</td>
      <td>-0.111253</td>
      <td>-0.199378</td>
      <td>0.640265</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>1.156401</td>
      <td>1.336300</td>
      <td>1.664201</td>
      <td>-0.764236</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>0.105883</td>
      <td>0.136233</td>
      <td>-0.325962</td>
      <td>-1.234223</td>
    </tr>
    <tr>
      <th>2013-01-05</th>
      <td>-0.939378</td>
      <td>-0.435466</td>
      <td>-1.873725</td>
      <td>-1.012697</td>
    </tr>
    <tr>
      <th>2013-01-06</th>
      <td>-0.155596</td>
      <td>-0.740179</td>
      <td>-1.542558</td>
      <td>-0.594198</td>
    </tr>
  </tbody>
</table>
</div>



Dataframe 생성: 여러 가지 방법. 특히 Series와 유사한 구조를 지닌 Dictionary로부터 


```python
df2 = pd.DataFrame(
    {
        "A": 1.0,
        "B": pd.Timestamp("20130102"),
        "C": pd.Series(1, index=list(range(4)), dtype="float32"),
        "D": np.array([3] * 4, dtype="int32"),
        "E": pd.Categorical(["test", "train", "test", "train"]),
        "F": "foo",
    }
)


df2
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
      <th>F</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>2013-01-02</td>
      <td>1.0</td>
      <td>3</td>
      <td>test</td>
      <td>foo</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.0</td>
      <td>2013-01-02</td>
      <td>1.0</td>
      <td>3</td>
      <td>train</td>
      <td>foo</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1.0</td>
      <td>2013-01-02</td>
      <td>1.0</td>
      <td>3</td>
      <td>test</td>
      <td>foo</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1.0</td>
      <td>2013-01-02</td>
      <td>1.0</td>
      <td>3</td>
      <td>train</td>
      <td>foo</td>
    </tr>
  </tbody>
</table>
</div>




```python
A~F의 Data type은 서로 다르다.
```


```python
df2.dtypes
```




    A           float64
    B    datetime64[ns]
    C           float32
    D             int32
    E          category
    F            object
    dtype: object



<데이터 보기>
DataFrame.head()은 위쪽 행, DataFrame.tail()은 아래쪽 행


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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-01</th>
      <td>-0.690236</td>
      <td>-0.503255</td>
      <td>-0.161739</td>
      <td>0.272396</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>0.320978</td>
      <td>-0.111253</td>
      <td>-0.199378</td>
      <td>0.640265</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>1.156401</td>
      <td>1.336300</td>
      <td>1.664201</td>
      <td>-0.764236</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>0.105883</td>
      <td>0.136233</td>
      <td>-0.325962</td>
      <td>-1.234223</td>
    </tr>
    <tr>
      <th>2013-01-05</th>
      <td>-0.939378</td>
      <td>-0.435466</td>
      <td>-1.873725</td>
      <td>-1.012697</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.tail(3)
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-04</th>
      <td>0.105883</td>
      <td>0.136233</td>
      <td>-0.325962</td>
      <td>-1.234223</td>
    </tr>
    <tr>
      <th>2013-01-05</th>
      <td>-0.939378</td>
      <td>-0.435466</td>
      <td>-1.873725</td>
      <td>-1.012697</td>
    </tr>
    <tr>
      <th>2013-01-06</th>
      <td>-0.155596</td>
      <td>-0.740179</td>
      <td>-1.542558</td>
      <td>-0.594198</td>
    </tr>
  </tbody>
</table>
</div>



출력: DataFrame.index 또는 Dataframe.columns


```python
df.index
```




    DatetimeIndex(['2013-01-01', '2013-01-02', '2013-01-03', '2013-01-04',
                   '2013-01-05', '2013-01-06'],
                  dtype='datetime64[ns]', freq='D')




```python
df.columns
```




    Index(['A', 'B', 'C', 'D'], dtype='object')



Pandas와 Numpy의 차이: 넘파이는 array 전체에 1개의 데이터 종류만 허용, Pandas는 상관없음.
                       Dataframe.to_numpy()를 사용


```python
df.to_numpy()
```




    array([[-0.690236  , -0.5032546 , -0.16173892,  0.27239629],
           [ 0.32097798, -0.11125301, -0.19937847,  0.64026545],
           [ 1.15640072,  1.33629964,  1.66420099, -0.76423595],
           [ 0.1058826 ,  0.13623347, -0.32596181, -1.23422344],
           [-0.93937805, -0.43546641, -1.87372451, -1.01269738],
           [-0.15559613, -0.74017929, -1.54255787, -0.59419799]])



df2는 여러 데이터 종류로 이뤄진 DataFrame이다. 아래처럼 실행해 보면...


```python
df2.to_numpy()
```




    array([[1.0, Timestamp('2013-01-02 00:00:00'), 1.0, 3, 'test', 'foo'],
           [1.0, Timestamp('2013-01-02 00:00:00'), 1.0, 3, 'train', 'foo'],
           [1.0, Timestamp('2013-01-02 00:00:00'), 1.0, 3, 'test', 'foo'],
           [1.0, Timestamp('2013-01-02 00:00:00'), 1.0, 3, 'train', 'foo']],
          dtype=object)



Dataframe.to_numpy() 함수의 출력 결과에 index나 column label은 포함되지 않는다.

describe() 함수는 데이터를 간략하게 요약하여 보여줌


```python
df.describe()
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>6.000000</td>
      <td>6.000000</td>
      <td>6.000000</td>
      <td>6.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>-0.033658</td>
      <td>-0.052937</td>
      <td>-0.406527</td>
      <td>-0.448782</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.752033</td>
      <td>0.747072</td>
      <td>1.252236</td>
      <td>0.743196</td>
    </tr>
    <tr>
      <th>min</th>
      <td>-0.939378</td>
      <td>-0.740179</td>
      <td>-1.873725</td>
      <td>-1.234223</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>-0.556576</td>
      <td>-0.486308</td>
      <td>-1.238409</td>
      <td>-0.950582</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>-0.024857</td>
      <td>-0.273360</td>
      <td>-0.262670</td>
      <td>-0.679217</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>0.267204</td>
      <td>0.074362</td>
      <td>-0.171149</td>
      <td>0.055748</td>
    </tr>
    <tr>
      <th>max</th>
      <td>1.156401</td>
      <td>1.336300</td>
      <td>1.664201</td>
      <td>0.640265</td>
    </tr>
  </tbody>
</table>
</div>



데이터 변환


```python
df.T
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
      <th>2013-01-01</th>
      <th>2013-01-02</th>
      <th>2013-01-03</th>
      <th>2013-01-04</th>
      <th>2013-01-05</th>
      <th>2013-01-06</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A</th>
      <td>-0.690236</td>
      <td>0.320978</td>
      <td>1.156401</td>
      <td>0.105883</td>
      <td>-0.939378</td>
      <td>-0.155596</td>
    </tr>
    <tr>
      <th>B</th>
      <td>-0.503255</td>
      <td>-0.111253</td>
      <td>1.336300</td>
      <td>0.136233</td>
      <td>-0.435466</td>
      <td>-0.740179</td>
    </tr>
    <tr>
      <th>C</th>
      <td>-0.161739</td>
      <td>-0.199378</td>
      <td>1.664201</td>
      <td>-0.325962</td>
      <td>-1.873725</td>
      <td>-1.542558</td>
    </tr>
    <tr>
      <th>D</th>
      <td>0.272396</td>
      <td>0.640265</td>
      <td>-0.764236</td>
      <td>-1.234223</td>
      <td>-1.012697</td>
      <td>-0.594198</td>
    </tr>
  </tbody>
</table>
</div>



DataFrame.sort_index() sorts by an axis: 축에 의한 정렬


```python
df.sort_index(axis=1, ascending=False)
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
      <th>D</th>
      <th>C</th>
      <th>B</th>
      <th>A</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-01</th>
      <td>0.272396</td>
      <td>-0.161739</td>
      <td>-0.503255</td>
      <td>-0.690236</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>0.640265</td>
      <td>-0.199378</td>
      <td>-0.111253</td>
      <td>0.320978</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>-0.764236</td>
      <td>1.664201</td>
      <td>1.336300</td>
      <td>1.156401</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>-1.234223</td>
      <td>-0.325962</td>
      <td>0.136233</td>
      <td>0.105883</td>
    </tr>
    <tr>
      <th>2013-01-05</th>
      <td>-1.012697</td>
      <td>-1.873725</td>
      <td>-0.435466</td>
      <td>-0.939378</td>
    </tr>
    <tr>
      <th>2013-01-06</th>
      <td>-0.594198</td>
      <td>-1.542558</td>
      <td>-0.740179</td>
      <td>-0.155596</td>
    </tr>
  </tbody>
</table>
</div>




```python
<Selection> 선택
DataFrame.at(), DataFrame.iat(), DataFrame.loc() and DataFrame.iloc()

1개의 열을 선택하면 Series가 생성된다. df["A"]와 df.A는 같은 기능
```


```python
df["A"]
```




    2013-01-01   -0.690236
    2013-01-02    0.320978
    2013-01-03    1.156401
    2013-01-04    0.105883
    2013-01-05   -0.939378
    2013-01-06   -0.155596
    Freq: D, Name: A, dtype: float64



[] (__getitem__) 형식으로 선택하면 행을 분할(slicing)한다.


```python
df[0:3]
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-01</th>
      <td>-0.690236</td>
      <td>-0.503255</td>
      <td>-0.161739</td>
      <td>0.272396</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>0.320978</td>
      <td>-0.111253</td>
      <td>-0.199378</td>
      <td>0.640265</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>1.156401</td>
      <td>1.336300</td>
      <td>1.664201</td>
      <td>-0.764236</td>
    </tr>
  </tbody>
</table>
</div>




```python
df["20130102":"20130104"]
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-02</th>
      <td>0.320978</td>
      <td>-0.111253</td>
      <td>-0.199378</td>
      <td>0.640265</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>1.156401</td>
      <td>1.336300</td>
      <td>1.664201</td>
      <td>-0.764236</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>0.105883</td>
      <td>0.136233</td>
      <td>-0.325962</td>
      <td>-1.234223</td>
    </tr>
  </tbody>
</table>
</div>




```python
<Label로 선택하기>
df.loc[]와 df.iloc[]는 오직 행만, 열만, 혹은 둘 다 선택할 수 있음
df.at[]과 df.iat[]은 행과 열에서 단일값(single value)을 선택할 수 있음
```


```python
df.loc[dates[0]]
```




    A   -0.690236
    B   -0.503255
    C   -0.161739
    D    0.272396
    Name: 2013-01-01 00:00:00, dtype: float64



Lable로 다축(multi-axis)도 선택 가능


```python
df.loc[:, ["A", "B"]]
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
      <th>A</th>
      <th>B</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-01</th>
      <td>-0.690236</td>
      <td>-0.503255</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>0.320978</td>
      <td>-0.111253</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>1.156401</td>
      <td>1.336300</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>0.105883</td>
      <td>0.136233</td>
    </tr>
    <tr>
      <th>2013-01-05</th>
      <td>-0.939378</td>
      <td>-0.435466</td>
    </tr>
    <tr>
      <th>2013-01-06</th>
      <td>-0.155596</td>
      <td>-0.740179</td>
    </tr>
  </tbody>
</table>
</div>



Label 슬라이싱해서 보기(이름으로 잘랐기 때문에 양쪽 끝단에 해당하는 행이나 열까지 보임


```python
df.loc["20130102":"20130104", ["A", "B"]]
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
      <th>A</th>
      <th>B</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-02</th>
      <td>0.320978</td>
      <td>-0.111253</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>1.156401</td>
      <td>1.336300</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>0.105883</td>
      <td>0.136233</td>
    </tr>
  </tbody>
</table>
</div>



반환된 객체의 차원(dimension)이 줄어들 수도 있음(당연히)


```python
df.loc["20130102", ["A", "B"]]
```




    A    0.320978
    B   -0.111253
    Name: 2013-01-02 00:00:00, dtype: float64



Scalar 값을 얻기 위해서 아래와 같이 실행


```python
df.loc[dates[0], "A"]
```




    -0.6902360032880608




```python
# 아래와 같이 해도 동일한 결과를 얻는다.

df.at[dates[0], "A"]
```

스칼라 = 단일 값, 벡터화 = 통쨰로

예를 들어 merong이라는 칼럼의 값을 2배로 만들고 싶다면?
for 반복문을 사용하면 아래와 같은 코드가 나온다.

for row in range(len(df)):
    df.loc[row, 'merong'] = df.loc[row, 'merong'] * 2
    row = row + 1
    
이 방법은 비효율의 극치. 데이터프레임의 처음부터 끝까지 훑어야 한다 --> 느리다
바람직한 방법은 아래와 같음

df['merong'] = df['merong'] * 2

merong 칼럼(pandas에는 시리즈) 전체에 바로 계산을 때리는 것.
이렇게 한 방에 계산을 처리하는 방식을 벡터 연산, 혹은 벡터화 연산이라고 한다.


<위치로 선택하기> 
 DataFrame.iloc() 또는 DataFrame.at().


```python
# 3번 행

df.iloc[3]
```




    A    0.105883
    B    0.136233
    C   -0.325962
    D   -1.234223
    Name: 2013-01-04 00:00:00, dtype: float64




```python
# 슬라이싱
df.iloc[3:5, 0:2]
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
      <th>A</th>
      <th>B</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-04</th>
      <td>0.105883</td>
      <td>0.136233</td>
    </tr>
    <tr>
      <th>2013-01-05</th>
      <td>-0.939378</td>
      <td>-0.435466</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 위치를 가리키는 정수 리스트로 선택
df.iloc[[1, 2, 4], [0, 2]]
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
      <th>A</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-02</th>
      <td>0.320978</td>
      <td>-0.199378</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>1.156401</td>
      <td>1.664201</td>
    </tr>
    <tr>
      <th>2013-01-05</th>
      <td>-0.939378</td>
      <td>-1.873725</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 열은 놔두고 행만 슬라이싱하기
df.iloc[1:3, :]
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-02</th>
      <td>0.320978</td>
      <td>-0.111253</td>
      <td>-0.199378</td>
      <td>0.640265</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>1.156401</td>
      <td>1.336300</td>
      <td>1.664201</td>
      <td>-0.764236</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 행은 놔두고 열만 슬라이싱하기
df.iloc[:, 1:3]
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
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-01</th>
      <td>-0.503255</td>
      <td>-0.161739</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>-0.111253</td>
      <td>-0.199378</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>1.336300</td>
      <td>1.664201</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>0.136233</td>
      <td>-0.325962</td>
    </tr>
    <tr>
      <th>2013-01-05</th>
      <td>-0.435466</td>
      <td>-1.873725</td>
    </tr>
    <tr>
      <th>2013-01-06</th>
      <td>-0.740179</td>
      <td>-1.542558</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 특정 단일값(스칼라) 얻기
df.iloc[1, 1]
```




    -0.11125300640243944




```python
# 아래와처럼 해도 동일한 결과, but 빠른 접근 가능
df.iat[1, 1]
```

<Boolean 인덱싱> - 단일 칼럼의 값들로 데이터 선택하기


```python
# 칼럼 A의 값이 0보다 큰 애들만
df[df["A"] > 0]
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-02</th>
      <td>0.320978</td>
      <td>-0.111253</td>
      <td>-0.199378</td>
      <td>0.640265</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>1.156401</td>
      <td>1.336300</td>
      <td>1.664201</td>
      <td>-0.764236</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>0.105883</td>
      <td>0.136233</td>
      <td>-0.325962</td>
      <td>-1.234223</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 데이터프레임 전체에서 조건에 맞는 값들만 선택하기
df[df > 0]
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-01-01</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.272396</td>
    </tr>
    <tr>
      <th>2013-01-02</th>
      <td>0.320978</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.640265</td>
    </tr>
    <tr>
      <th>2013-01-03</th>
      <td>1.156401</td>
      <td>1.336300</td>
      <td>1.664201</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2013-01-04</th>
      <td>0.105883</td>
      <td>0.136233</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2013-01-05</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2013-01-06</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



<과제> 여기까지 내용으로 활용하여 연습문제를 3개씩 만들어 올 것. 
       문제와 풀이과정 및 해답 전부를 깃허브 또는 깃허브 블로그에 포스팅

