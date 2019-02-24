### Where the users likely live and work at?

This dataset CDR.csv has call records for 10 users tracked over the course of 3 years. 
In all plots, the X-Coordinate should be **Longitude**, and the Y coordinate should be 
**Latitude**. We don't yet know exactly where the user is located just based off 
the cell phone tower position data; but considering the below are for calls that arrived 
in the twilight of weekends, it's likely that wherever they are bunched up is probably 
near where the caller's residence.

### Function pd.to_datetime()

Pandas by default represents the dates with  datetime64.
We use **pd.to_datetime** function to convert **pandas DataFrame** data imported as string format
to __datetime__ format. By the lambda function **lambda x: x.hour**
we pull out the field __hour__ from the __datetime__ format.

### Find all records per each phone

records_per_user = []
for i in range(np.size(users)):
    records_for_phone_i = df[df['In'] == df_In_unique[i]] # get all records for phone users[i]
    records_per_user.append(records_for_phone_i)

for i in range(np.size(users)):
    print( i,  ', phone: ', users[i],  ' len of recorsd ',   records_per_user[i].shape[0] )
    
We get the following results per each phone number:

0 , phone:  4638472273  len of recorsd  3648
1 , phone:  1559410755  len of recorsd  11633
2 , phone:  4931532174  len of recorsd  2896
3 , phone:  2419930464  len of recorsd  2497
4 , phone:  1884182865  len of recorsd  2865
5 , phone:  3688089071  len of recorsd  1610
6 , phone:  4555003213  len of recorsd  2410
7 , phone:  2068627935  len of recorsd  5835
8 , phone:  2894365987  len of recorsd  12053
9 , phone:  8549533077  len of recorsd  7741 

### Weekend calls, phone = 4638472273

To get weekend calls we use the following conditions

**user0_weekend = user0[(user0['DOW'] == 'Sat') | (user0['DOW'] == 'Sun')]**

### Only Satarday from 13:00 to 16:00, phone = 4638472273

**user0_Sat_1to4AM = user0[(user0['DOW'] == 'Sat') & (user0['time_hour'] > 13) & (user0['time_hour'] < 16)]**

### Weekday night calls,  phone = 4638472273

The conditions are as follows: No Satarday, No Sunday, 0 < TimeHour < 6. 

**user0_bef6AM_aft22PM = user0[(user0['DOW'] != 'Sat') & (user0['DOW'] != 'Sun') & (user0['time_hour'] > 0) & (user0['time_hour'] < 6)]**

### Only Satarday from 13:00 to 16:00, all phones

* Phone:  4638472273 all rows of coord from 13:00 to 16:00 =  133
* Phone:  1559410755 all rows of coord from 13:00 to 16:00 =  396
* Phone:  4931532174 all rows of coord from 13:00 to 16:00 =  96
* Phone:  2419930464 all rows of coord from 13:00 to 16:00 =  75
* Phone:  1884182865 all rows of coord from 13:00 to 16:00 =  98
* Phone:  3688089071 all rows of coord from 13:00 to 16:00 =  58
* Phone:  4555003213 all rows of coord from 13:00 to 16:00 =  93
* Phone:  2068627935 all rows of coord from 13:00 to 16:00 =  200
* Phone:  2894365987 all rows of coord from 13:00 to 16:00 =  413
* Phone:  8549533077 all rows of coord from 13:00 to 16:00 =  317

