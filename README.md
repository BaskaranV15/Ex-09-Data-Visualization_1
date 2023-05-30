# Ex-09-Data-Visualization-

## AIM
To Perform Data Visualization on a complex dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.
# CODE
```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np
df=sns.load_dataset("tips")
df

plt.figure(figsize=(12,8))
plt.title('data with outliers')
df.boxplot()
plt.show()

plt.figure(figsize=(8,8))
cols=['size','tip','total_bill']
Q1=df[cols].quantile(0.25)
Q3=df[cols].quantile(0.75)
IQR=Q3-Q1
df = df[~((df[cols] < (Q1 - 1.5 * IQR)) |(df[cols] > (Q3 + 1.5 * IQR))).any(axis=1)]
plt.title("After removing outliers")
df.boxplot()
plt.show()

sns.lineplot(x=df['day'],y=df['total_bill'])
sns.lineplot(x=df['day'],y=df['total_bill'],hue=df['sex'])
sns.barplot(x=df['smoker'],y=df['tip'],hue=df['sex'])
df['tip_percentage'] = (df['tip'] / df['total_bill']) * 100

sns.scatterplot(data=df, x='size', y='tip_percentage', size='tip', alpha=0.7)
plt.xlabel('Dining Party Size')
plt.ylabel('Tip Percentage')
plt.title('Tip Percentage by Dining Party Size')
plt.show()

sns.lineplot(x=df['sex'],y=df['tip'],hue=df['time'])

sns.barplot(x=df['sex'],y=df['tip'],data=df)

sns.scatterplot(x='day',y='total_bill',data=df)

sns.barplot(x=df['time'],y=df['total_bill'],hue=df['time'])

average_bill_by_size = df.groupby('size')['total_bill'].mean().reset_index()
max_average_bill = average_bill_by_size[average_bill_by_size['total_bill'] == average_bill_by_size['total_bill'].max()]
print(max_average_bill)

sns.barplot(x=df['size'],y=df['total_bill'])
sns.barplot(x=df['size'],y=df['total_bill'],hue=df['sex'])
sns.barplot(data=df, x='day', y='tip')
average_bill_by_size = df.groupby('size')['total_bill'].mean()
max_average_bill = average_bill_by_size
max_average_bill

average_bill=df.loc[:,['size','total_bill']]
average_bill=df.groupby(by=['size']).mean().sort_values(by=['total_bill'])
sns.barplot(x=average_bill.index,y='total_bill',data=average_bill)
plt.show()

sns.violinplot(data=df, x='day', y='tip',linewide=2,width=0.6,palette='Set3')

sns.violinplot(x="day", y="tip", hue="sex", data=df, linewidth=2, width=0.6,palette="Set3")
sns.barplot(x='time',y='tip',data=df,hue='sex')

sns.kdeplot(data=df,x='total_bill',hue='sex',multiple='stack',linewidth=5,palette='Dark2',alpha=0.5)

sns.barplot(x='day', y='total_bill', hue='sex', data=df, palette='Set1')
# Set labels and title
plt.xlabel('Day of the Week')
plt.ylabel('Total Bill')
plt.title('Total Bill by Day and Gender')
# Show the plot
plt.show()

sns.kdeplot(x=df['total_bill'],y=df['tip'],hue=df['smoker'],multiple='stack',linewidth=5,palette='Dark2',alpha=0.5)

sns.kdeplot(x=df['total_bill'],y=df['tip'])

sns.pointplot(x=df['day'],y=df['tip'],hue=df['sex'])

avg_total_bill = df.groupby('time')['total_bill'].sum()
avg_tip = df.groupby('time')['tip'].sum()
# Create a grouped bar chart
p1 = plt.bar(avg_total_bill.index, avg_total_bill, label='Total Bill', width=0.4)
p2 = plt.bar(avg_tip.index, avg_tip, bottom = avg_total_bill, label='Tip', width=0.4)
plt.xlabel('Time of Day')
plt.ylabel('Amount')
plt.title('Average Total Bill and Tip by Time of Day')
plt.legend()
plt.show()

avg_total_bill
avg_tip
```
# OUPUT
![Screenshot 2023-05-30 155330](https://github.com/BaskaranV15/Ex-09-Data-Visualization_1/assets/118703522/572e1778-c6d3-4680-84a6-63ebccd685ea)
![Screenshot 2023-05-30 155420](https://github.com/BaskaranV15/Ex-09-Data-Visualization_1/assets/118703522/d19121d1-933f-4f11-95b2-4affcdade6f8)
![Screenshot 2023-05-30 155443](https://github.com/BaskaranV15/Ex-09-Data-Visualization_1/assets/118703522/82e13544-e82a-45ca-9aef-801e94d0c1c1)
![Screenshot 2023-05-30 155449](https://github.com/BaskaranV15/Ex-09-Data-Visualization_1/assets/118703522/daddcd49-9188-4972-b638-fac5aaa3a939)
![Screenshot 2023-05-30 155458](https://github.com/BaskaranV15/Ex-09-Data-Visualization_1/assets/118703522/68231ccd-c77e-43b8-a7bd-7eb29e82e377)
![Screenshot 2023-05-30 155508](https://github.com/BaskaranV15/Ex-09-Data-Visualization_1/assets/118703522/180a085d-e251-405d-8538-6388651147ec)
![Screenshot 2023-05-30 155533](https://github.com/BaskaranV15/Ex-09-Data-Visualization_1/assets/118703522/3f3075b1-3d3f-47a0-ab89-bae3a56cd219)
![Screenshot 2023-05-30 155544](https://github.com/BaskaranV15/Ex-09-Data-Visualization_1/assets/118703522/98da4d24-a443-41e6-9708-ca0356dcdc47)
![Screenshot 2023-05-30 155555](https://github.com/BaskaranV15/Ex-09-Data-Visualizatio![Screenshot 2023-05-30 155606](https://github.com/BaskaranV15/Ex-09-Data-Visualization_1/assets/118703522/7071a021-b374-49f6-bd36-be0c4c360a49)
n_1/assets/11![Screenshot 2023-05-30 155612](https://github.com/BaskaranV15/Ex-09-Data-Visualization_1/assets/118703522/da43c62b-ae4f-45b9-a210-6302a7d66f13)
8703522/2cc7e389-c9ce-4a07-9e2f-1e402c3ec73a)
![Screenshot 2023-05-30 155623](https://github.com/BaskaranV15/Ex-09-Data-Visualization_1/assets/118703522/a857db55-da9f-4bea-b18b-1e7057b37c74)
![Screenshot 2023-05-30 155629](https://github.com/BaskaranV15/Ex-09-Data-Visualization_1![Screenshot 2023-05-30 155638](https://github.com/BaskaranV15/Ex-09-Data-Visualization_1/assets/118703522/426d3fd9-94c3-4950-b323-901b395d88c9)
/assets/118703522/6e2522cd-d032-4cb3-afa8-6507a7ccca8f)
![Screenshot 2023-05-30 155645](https://github.com/BaskaranV15/Ex-09-Data-Visualization_1/assets/118703522/737a8d08-ec47-4a79-b02f-f56df84e4f38)
![Screenshot 2023-05-30 155656](https://github.com/BaskaranV15/Ex-09-Data-Visualization_1/assets/118703522/bca0a4f9-c789-42ee-bd95-3ced08b882d0)
![Screenshot 2023-05-30 155709](https://github.com/BaskaranV15/Ex-09-Data-Visualization_1/assets/118703522/a5e55b78-c271-4963-990f-4df7c504b6b5)
![Screenshot 2023-05-30 155715](https://github.com/BaskaranV15/Ex-09-Data-Visualization_1/assets/118703522/32c78273-48ee-44a0-9651-0d6fa0172006)
![Screenshot 2023-05-30 155737](https://github.com/BaskaranV15/Ex-09-Data-Visualization_1/assets/118703522/ef9d385b-8e80-4848-b21c-3d2666c7523e)
![Screenshot 2023-05-30 155743](https://github.com/BaskaranV15/Ex-09-Data-Visualization_1/assets/118703522/9b0d9aea-2083-4028-82b6-32505fe52bcd)
![Screenshot 2023-05-30 155754](https://github.com/BaskaranV15/Ex-09-Data-Visualization_1/assets/118703522/79785ca4-3f76-4999-b5a8-8d0e16b84704)
![Screenshot 2023-05-30 155802](https://github.com/BaskaranV15/Ex-09-Data-Visualization_1/assets/118703522/859bfb94-8996-4486-96c6-c8ac254d5867)
![Screenshot 2023-05-30 155808](https://github.com/BaskaranV15/Ex-09-Data-Visualization_1/assets/118703522/0dd0ee9e-629a-4b51-a74a-d83fdc09523d)
![Screenshot 2023-05-30 155820](https://github.com/BaskaranV15/Ex-09-Data-Visualization_1/assets/118703522/e014d9dc-d77e-4e8a-81f3-f6630b4a36b1)
![Screenshot 2023-05-30 155828](https://github.com/BaskaranV15/Ex-09-Data-Visualization_1/assets/118703522/fff5b169-b74e-4598-91f2-f8e4417a8d0a)
# result 
Using visual elements like charts, graphs, and maps, data visualization is done.
