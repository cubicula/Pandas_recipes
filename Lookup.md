# Lookups

### Passing multiple columns to _apply_

```
cisco_web_filter_copy['a plus b'] = \
    cisco_web_filter_copy.apply(lambda x:f_add( x['Hostname'], x['Product ID'] ) , axis=1)
```

```
def f_add(a, b):    
    return( a+b )
```

### Calculating _multiple_ columns based on a single column with _apply_

```
cisco_web_filter_copy[['Device Type', 'DeviceCatalogIndex', 'DeviceCatalogModelName', 'Standard HW']] = \
cisco_web_filter_copy['Product ID'].apply(lambda x:lookup_model(x, df_devcat))`
```

where the lookup function is something like this:

```
def lookup_model(s, df_devcat):
    
    # lookup in device catalog, lower case, strip white space
    match  = df_devcat[ df_devcat['Device Model'] == s ]
    
    if match.empty:
        ind = "No model match in catalog"
        name = np.nan
        standard_HW = np.nan
        device_type = np.nan
    elif len(match)>1:
        ind = "Multiple matches in catalog"
        name = match['Device Model'].values[0] 
        standard_HW = match['Standard HW'].values[0]
        device_type = match['Device Type'].values[0]
        
    return pd.Series([device_type, ind, name, standard_HW])
    
```
