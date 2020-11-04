# Covid19-India-Data-Analysis
import pandas as pd #It Is useful For Readind, Making Data Frame, Manipulating, Managing And Much More
import numpy as np #Much Faster To Play With Numbers, So This Library Is Also Useful
import matplotlib.pyplot as plt #For Data Visualisation, these library is helpful
df=pd.read_csv('e:/covid_19_india.csv') #Using Panda To Read CSV type File (CSV: Comma Seperated Values)

df.drop(['Time','ConfirmedIndianNational','ConfirmedForeignNational','Sno'],axis=1,inplace=True) 
"""A DataFrame object has two axes: “axis 0” and “axis 1”. “axis 0” represents rows and “axis 1” represents columns.
Now it's clear that Series and DataFrame share the same direction for “axis 0” – it goes along rows direction."""
#axis=1 means droping that column which contains Time,ConfirmedIndianNational,ConfirmedForeignNational
#inplace=True means changing in original Data Frame, not Making any copy.

df.rename(columns={'State/UnionTerritory':'State'},inplace=True) 
#Renaming The Columns So That It Is Easy To Remember

df=df.iloc[::-1] #Reversing Rows, So That At the beginning i will get the latest Record

df = df.groupby('State')[['Confirmed','Cured','Deaths']].first()
"""Only Contains One State Only one time so that the overall confirmed,deaths and cured Cases 
at the latest is known, aslo written[['Confirmed','Cured','Deaths']] to get this columns.
The state will now act like an index"""

print(df.head(42))

#plt.plot("x axis,y axis,color='',label='') to make graph 
#plt.title("") To give title to the graph
#plt.xlabel("") To give title to the x axis, similarly y.label for y axis
#plt.legend() To show what does specific lines means
#plt.show() Act as an print
plt.plot(np.arange(0,len(df)),df['Confirmed'],color='blue',label='Confirmed Cases')
plt.plot(np.arange(0,len(df)),df['Cured'],color='green',label='Cured Cases')
plt.plot(np.arange(0,len(df)),df['Deaths'],color='red',label='Deaths')
plt.title("State Wise Comparison")
plt.xlabel("State")
plt.ylabel("Cases")
plt.legend()
plt.show()
#This Graph Contains Numeric terms in X axis

plt.plot(np.arange(0,len(df)),df['Deaths'],color='red',label='Deaths')
plt.title("State Wise Comparison")
plt.xlabel("State")
plt.ylabel("Cases")
plt.legend()
plt.show()
#Only Deaths Analysis

plt.plot(np.arange(0,len(df)),df['Cured'],color='green',label='Cured Cases')
plt.title("State Wise Comparison")
plt.xlabel("State")
plt.ylabel("Cases")
plt.legend()
plt.show()
#Only Cured Cases Analysis

plt.plot(np.arange(0,len(df)),df['Confirmed'],color='blue',label='Confirmed Cases')
plt.title("State Wise Comparison")
plt.xlabel("State")
plt.ylabel("Cases")
plt.legend()
plt.show()

#plt.plot("x axis,y axis,color='',label='') to make graph 
#plt.title("") To give title to the graph
#plt.xlabel("") To give title to the x axis, similarly y.label for y axis
#plt.legend() To show what does specific lines means
#plt.show() Act as an print
plt.plot(df.index,df['Confirmed'],color='blue',label='Confirmed Cases')
plt.plot(df.index,df['Cured'],color='green',label='Cured Cases')
plt.plot(df.index,df['Deaths'],color='red',label='Deaths')
plt.title("State Wise Comparison")
plt.xlabel("State")
plt.ylabel("Cases")
plt.legend()
plt.show()
#This Graph Contains Name Of The State In X axis
#Only Confirmed Cases Analysis
