# Lookups

Calculating _multiple_ columns based on a single column with _apply_

`cisco_web_filter_copy[['Device Type', 'DeviceCatalogIndex', 'DeviceCatalogModelName', 'Standard HW']] = cisco_web_filter_copy['Product ID'].apply(lambda x:lookup_model(x, df_devcat))`
