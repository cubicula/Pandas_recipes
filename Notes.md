##
Basic understanding ... dataframe indices needn't be unique

```
df = pd.DataFrame(data = {'A':list('abcd'), 'B':list('abcd')}, index=[0,1,2,1])
df
```
```
A	B
0	a	a
1	b	b
2	c	c
1	d	d
```
Then `df.loc[1]` returns two rows!

```
	A	B
1	b	b
1	d	d
```

