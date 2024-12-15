# HEART-DISEASE-ANALYSIS-
Heart disease analysis is the process of using data to identify and predict heart disease.

1.Create histogram for showing cholesterol with Number of bins 5
2.Create Boxplot for showing trestbps and comment what the dark spot indicate
3.Find and print the percentage of females and males heart disease
4.Create a scatter plot for showing age and ST depression induced by exercise relative to rest

#importing libraries

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df=pd.read_csv("heart.csv")
print(df.head())

print(df.describe(include="all"))
print(df.describe(include="all"))
print(df.columns)
print(df.info())
SEX={0:"female",1:"male"}
df.sex.replace(SEX,inplace=True)
df.head()

#1.Create histogram for showing Cholesterol with Number of bins 5
plt.hist(df.chol,bins=5,rwidth=0.7)
plt.grid(linestyle="--")
plt.xlabel("Cholesterol")
plt.ylabel("Count of people")
plt.xticks([50,100,150,200,250,300,350,400,450,500])
plt.title("Histogram for showing cholesterol with Number of bins 5 using Matplotlib")
plt.show()
sns.distplot(df.chol,hist=True,kde=False,bins=5,color="blue")
plt.xlabel("Cholesterol")
plt.ylabel("Count of people")
plt.title("Histogram for showing Cholesterol with Number of bins 5 using Seaborn")
plt.grid(linestyle="--")
plt.show()



#2.Create Boxplot for showing trestbps and comment what the dark spot indicate

plt.boxplot(df.trestbps)
plt.grid(linestyle="--")

plt.ylabel("Resting blood pressure (in mm Hg)")
plt.title("Boxplot for showing trestbps using Matplotlib")
plt.show()
sns.boxplot(df.trestbps,orient="v")
plt.grid(linestyle="--")
plt.ylabel("Resting blood pressure (in mm Hg)")
plt.title("Boxplot for showing trestbps using Seaborn")
plt.show()

#3.Create bar plot for showing Gender and target.

#draw a bar plot of target by sex
#Change the sex(0,1)=(female,male)


#print percentages of females vs. males Heart Disease
male_with_heart_disease=df[(df.sex=="male") & (df.target==1)].sex.count()
female_with_heart_disease=df[(df.sex=="female") & (df.target==1)].sex.count()
total_male_count=df[(df.sex=="male")].sex.count()
total_female_count=df[(df.sex=="female")].sex.count()

male_with_heart_disease_percentage=male_with_heart_disease/total_male_count*100
female_with_heart_disease_percentage=female_with_heart_disease/total_female_count*100

print("Percentages of females vs. males Heart Disease is:\n","Female:",\
      female_with_heart_disease_percentage,"Male:",male_with_heart_disease_percentage)

sns.scatterplot(x="age",y="oldpeak",data=df)
plt.show()

#4.Create a scatter plot for showing Age and ST depression induced by excercise relative to rest

sns.scatterplot(x="age",y="oldpeak",data=df)
plt.show()


