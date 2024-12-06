# HW5
````
def sum_daily_odd_even(transactions: pd.DataFrame) -> pd.DataFrame:
    transactions['odd_sum'] = transactions['amount'] * (transactions['amount'] % 2 != 0)
    transactions['even_sum'] = transactions['amount'] * (transactions['amount'] % 2 == 0)
    result = (transactions.groupby('transaction_date')[['odd_sum', 'even_sum']].sum().reset_index())
    
    return result
````
````
    return teacher.groupby('teacher_id').nunique().reset_index().rename(columns={'subject_id': 'cnt'})[['teacher_id', 'cnt']]
````

