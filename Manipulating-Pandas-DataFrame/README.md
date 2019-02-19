### DataFrame and JSON data

Let 'df' be the var of DataFrame type.
Assume, we do two operations:
1) write 'df' to file df.json of the JSON format
and after that
2) read df.json into the var 'df2' of DataFrame.

The only way to get exactly the same data  'df2' = 'df',
is to execute the operations  df.to_json and df2 = pd.read_json
with the parameter orient='split'.
