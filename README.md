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
````
    employee = employee[employee.duplicated(subset='employee_id', keep=False) == False | (employee.primary_flag == "Y")]
    return employee[['employee_id', 'department_id']]
````
````
    result = products.melt(id_vars=['product_id'], value_vars=['store1', 'store2', 'store3'], var_name='store', value_name='price')
    result = result[result['price'].notnull()]
    return result[['product_id', 'store', 'price']]
````
````
    employees["bonus"] = ((employees["employee_id"] % 2 == 1) & (~employees["name"].str.startswith("M"))) * employees["salary"]
    return employees[["employee_id", "bonus"]].sort_values("employee_id")
````
````
    logins_2020 = logins[logins['time_stamp'].dt.year == 2020]
    result = logins_2020.groupby('user_id')['time_stamp'].max().reset_index()
    result.rename(columns={'time_stamp': 'last_stamp'}, inplace=True)
    return result[['user_id', 'last_stamp']]
````
````
salary_categories = pd.cut(accounts['income'], 
                               [float('-inf'), 19_999, 50_000, float('inf')], 
                               labels=['Low Salary', 'Average Salary', 'High Salary'])
    counts = salary_categories.value_counts()
    all_categories = ['Low Salary', 'Average Salary', 'High Salary']
    counts = counts.reindex(all_categories)
    return pd.DataFrame({'category': counts.index, 'accounts_count': counts.values})
````
````
df = signups[["user_id"]].merge(confirmations[["user_id", "action"]], on="user_id", how="left")
    df["action"] = (df["action"] == "confirmed").astype(int)
    result = df.groupby("user_id", as_index=False)["action"].mean().round(2).rename(columns={"action": "confirmation_rate"})
    return result
````
# Work woth dataset
````
df = pd.read_csv('/kaggle/input/student-information-dataset/students.csv')

df.head()
````
````
df.info()
````
````
df.isnull().sum()
````
````
df.columns.to_list()
````
````
df.duplicated().sum()
````
````
df.describe(include = 'all').T
````
````
df['StudentID'] = df['StudentID'].astype(int)

df['Email'] = df['Email'].astype(str)

df['GraduationYear'] = df['GraduationYear'].astype(int)

df['Age'] = df['Age'].astype(int)

df['GPA'] = df['GPA'].astype(float)

df['Department'] = df['Department'].astype('category')
````
````
age = df[(df['Age'] < 18) | (df['Age'] > 25)]
print(age)
````
````
print(df['Department'].value_counts())
````
````
sns.histplot(df['Age'], kde=True)
plt.title("Distribution of Age")
plt.show()
````
````
sns.histplot(df['GPA'], kde=True)
plt.title("Distribution of GPA")
plt.show()
````
````
corr_matrix = df[['Age', 'GPA']].corr()
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm')
plt.title("Correlation Matrix: Age and GPA")
plt.show()
````
````
sns.boxplot(x='Department', y='GPA', data=df)
plt.title("GPA by Department")
plt.xticks(rotation=45)
plt.show()
````
````
sns.scatterplot(x='Age', y='GPA', data=df)
plt.title("Age vs GPA")
plt.show()
````
