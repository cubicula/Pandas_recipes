##
Basic understanding ... dataframe indices needn't be unique

```
df = pd.DataFrame(data = {'A':['a'+i for i in list('1234')], 'B':['b'+i for i in list('1234')]}, index=[0,1,2,1])
```
```
A	B
0	a1	b1
1	a2	b2
2	a3	b3
1	a4	b4
```
Then `df.loc[1]` returns two rows!

```
A	B
1	a2	b2
1	a4	b4
```



