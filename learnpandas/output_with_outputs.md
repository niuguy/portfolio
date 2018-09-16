### Locate the file
There are two ways to locate the csv file, "absolute path"
or "relative path"
e.g.
Absolute path:
"`/work/project/data/great.csv`"(Mac) or
"`C:\work\project\data\great.csv`"(Windows)
Relative path:
"`data/greate.csv`"(Mac) or "`data\great.csv`"(Windows)
### Read with
pandas.read_csv()
The result is a dataframe Object

```{.python .input  n=5}
import pandas as pd
import numpy as np 
df = pd.read_csv('data/great.csv')
df
```

```{.json .output n=5}
[
 {
  "data": {
   "text/html": "<div>\n<style scoped>\n    .dataframe tbody tr th:only-of-type {\n        vertical-align: middle;\n    }\n\n    .dataframe tbody tr th {\n        vertical-align: top;\n    }\n\n    .dataframe thead th {\n        text-align: right;\n    }\n</style>\n<table border=\"1\" class=\"dataframe\">\n  <thead>\n    <tr style=\"text-align: right;\">\n      <th></th>\n      <th>company</th>\n      <th>locate</th>\n      <th>employees</th>\n      <th>avenue</th>\n    </tr>\n  </thead>\n  <tbody>\n    <tr>\n      <th>0</th>\n      <td>orange</td>\n      <td>New York</td>\n      <td>10000</td>\n      <td>4000.0</td>\n    </tr>\n    <tr>\n      <th>1</th>\n      <td>banana</td>\n      <td>London</td>\n      <td>2000</td>\n      <td>1000.0</td>\n    </tr>\n    <tr>\n      <th>2</th>\n      <td>pinch</td>\n      <td>Paris</td>\n      <td>4000</td>\n      <td>5000.0</td>\n    </tr>\n    <tr>\n      <th>3</th>\n      <td>pear</td>\n      <td>Berlin</td>\n      <td>3000</td>\n      <td>NaN</td>\n    </tr>\n  </tbody>\n</table>\n</div>",
   "text/plain": "  company     locate   employees   avenue\n0  orange   New York       10000   4000.0\n1  banana     London        2000   1000.0\n2   pinch      Paris        4000   5000.0\n3    pear     Berlin        3000      NaN"
  },
  "execution_count": 5,
  "metadata": {},
  "output_type": "execute_result"
 }
]
```

### If the data has no header

```{.python .input  n=6}
df = pd.read_csv('data/great.csv', header= None)
df
```

```{.json .output n=6}
[
 {
  "data": {
   "text/html": "<div>\n<style scoped>\n    .dataframe tbody tr th:only-of-type {\n        vertical-align: middle;\n    }\n\n    .dataframe tbody tr th {\n        vertical-align: top;\n    }\n\n    .dataframe thead th {\n        text-align: right;\n    }\n</style>\n<table border=\"1\" class=\"dataframe\">\n  <thead>\n    <tr style=\"text-align: right;\">\n      <th></th>\n      <th>0</th>\n      <th>1</th>\n      <th>2</th>\n      <th>3</th>\n    </tr>\n  </thead>\n  <tbody>\n    <tr>\n      <th>0</th>\n      <td>company</td>\n      <td>locate</td>\n      <td>employees</td>\n      <td>avenue</td>\n    </tr>\n    <tr>\n      <th>1</th>\n      <td>orange</td>\n      <td>New York</td>\n      <td>10000</td>\n      <td>4000</td>\n    </tr>\n    <tr>\n      <th>2</th>\n      <td>banana</td>\n      <td>London</td>\n      <td>2000</td>\n      <td>1000</td>\n    </tr>\n    <tr>\n      <th>3</th>\n      <td>pinch</td>\n      <td>Paris</td>\n      <td>4000</td>\n      <td>5000</td>\n    </tr>\n    <tr>\n      <th>4</th>\n      <td>pear</td>\n      <td>Berlin</td>\n      <td>3000</td>\n      <td>NaN</td>\n    </tr>\n  </tbody>\n</table>\n</div>",
   "text/plain": "         0          1           2        3\n0  company     locate   employees   avenue\n1   orange   New York       10000     4000\n2   banana     London        2000     1000\n3    pinch      Paris        4000     5000\n4     pear     Berlin        3000      NaN"
  },
  "execution_count": 6,
  "metadata": {},
  "output_type": "execute_result"
 }
]
```

###  Filter rows

```{.python .input  n=8}
df = pd.read_csv('data/great.csv', skiprows=[3,4])
df
```

```{.json .output n=8}
[
 {
  "data": {
   "text/html": "<div>\n<style scoped>\n    .dataframe tbody tr th:only-of-type {\n        vertical-align: middle;\n    }\n\n    .dataframe tbody tr th {\n        vertical-align: top;\n    }\n\n    .dataframe thead th {\n        text-align: right;\n    }\n</style>\n<table border=\"1\" class=\"dataframe\">\n  <thead>\n    <tr style=\"text-align: right;\">\n      <th></th>\n      <th>company</th>\n      <th>locate</th>\n      <th>employees</th>\n      <th>avenue</th>\n    </tr>\n  </thead>\n  <tbody>\n    <tr>\n      <th>0</th>\n      <td>orange</td>\n      <td>New York</td>\n      <td>10000</td>\n      <td>4000</td>\n    </tr>\n    <tr>\n      <th>1</th>\n      <td>banana</td>\n      <td>London</td>\n      <td>2000</td>\n      <td>1000</td>\n    </tr>\n  </tbody>\n</table>\n</div>",
   "text/plain": "  company     locate   employees   avenue\n0  orange   New York       10000     4000\n1  banana     London        2000     1000"
  },
  "execution_count": 8,
  "metadata": {},
  "output_type": "execute_result"
 }
]
```

lambda is also welcomed

```{.python .input  n=11}
df = pd.read_csv('data/great.csv', skiprows=lambda x:x/2==1)
df
```

```{.json .output n=11}
[
 {
  "data": {
   "text/html": "<div>\n<style scoped>\n    .dataframe tbody tr th:only-of-type {\n        vertical-align: middle;\n    }\n\n    .dataframe tbody tr th {\n        vertical-align: top;\n    }\n\n    .dataframe thead th {\n        text-align: right;\n    }\n</style>\n<table border=\"1\" class=\"dataframe\">\n  <thead>\n    <tr style=\"text-align: right;\">\n      <th></th>\n      <th>company</th>\n      <th>locate</th>\n      <th>employees</th>\n      <th>avenue</th>\n    </tr>\n  </thead>\n  <tbody>\n    <tr>\n      <th>0</th>\n      <td>orange</td>\n      <td>New York</td>\n      <td>10000</td>\n      <td>4000.0</td>\n    </tr>\n    <tr>\n      <th>1</th>\n      <td>pear</td>\n      <td>Berlin</td>\n      <td>3000</td>\n      <td>NaN</td>\n    </tr>\n  </tbody>\n</table>\n</div>",
   "text/plain": "  company     locate   employees   avenue\n0  orange   New York       10000   4000.0\n1    pear     Berlin        3000      NaN"
  },
  "execution_count": 11,
  "metadata": {},
  "output_type": "execute_result"
 }
]
```

### Filter columns(or keep wanted)

```{.python .input  n=20}
df = pd.read_csv('data/great.csv', usecols=['company'])
df
```

```{.json .output n=20}
[
 {
  "data": {
   "text/html": "<div>\n<style scoped>\n    .dataframe tbody tr th:only-of-type {\n        vertical-align: middle;\n    }\n\n    .dataframe tbody tr th {\n        vertical-align: top;\n    }\n\n    .dataframe thead th {\n        text-align: right;\n    }\n</style>\n<table border=\"1\" class=\"dataframe\">\n  <thead>\n    <tr style=\"text-align: right;\">\n      <th></th>\n      <th>company</th>\n    </tr>\n  </thead>\n  <tbody>\n    <tr>\n      <th>0</th>\n      <td>orange</td>\n    </tr>\n    <tr>\n      <th>1</th>\n      <td>banana</td>\n    </tr>\n    <tr>\n      <th>2</th>\n      <td>pinch</td>\n    </tr>\n    <tr>\n      <th>3</th>\n      <td>pear</td>\n    </tr>\n  </tbody>\n</table>\n</div>",
   "text/plain": "  company\n0  orange\n1  banana\n2   pinch\n3    pear"
  },
  "execution_count": 20,
  "metadata": {},
  "output_type": "execute_result"
 }
]
```

There are a bunch of other options, refer https://pandas.pydata.org/pandas-
docs/stable/generated/pandas.read_csv.html
