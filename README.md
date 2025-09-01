# Decision-Tree-Whether-Forecast-ML
A simple Machine Learning project using Decision Tree algorithm to predict whether to play ball based on weather conditions.  Dataset includes Outlook, Temperature, Humidity, Wind, and PlayBall decisions.
# Weather Decision Tree

This project uses a small weather dataset to decide whether to play ball or not, based on:
- Outlook
- Temperature
- Humidity
- Wind

## Files
- `weather.csv` → Dataset in table format
- `decision_tree.py` → Python code to train and test Decision Tree
- Day,Outlook,Temperature,Humidity,Wind,PlayBall
1,Sunny,Hot,High,Weak,No
2,Sunny,Hot,High,Strong,No
3,Overcast,Hot,High,Weak,Yes
4,Rain,Mild,High,Weak,Yes
5,Rain,Cool,Normal,Weak,Yes
6,Rain,Cool,Normal,Strong,No
7,Overcast,Cool,Normal,Strong,Yes
8,Sunny,Mild,High,Weak,No
9,Sunny,Cool,Normal,Weak,Yes
10,Rain,Mild,Normal,Weak,Yes
11,Sunny,Mild,Normal,Strong,Yes
12,Overcast,Mild,High,Strong,Yes
13,Overcast,Hot,Normal,Weak,Yes
14,Rain,Mild,High,Strong,No
  import pandas as pd
from sklearn.tree import DecisionTreeClassifier, plot_tree
import matplotlib.pyplot as plt

# Load dataset
data= pd.read_csv(io.StringIO(data))
print(data.head( ))

# Features and target
data.columns= ['Dog', 'outlook', 'Temperature', 'Humidity', 'wind', 'playball']
data.head( )
data['outlook'].unique ( )
output = {'sunny':0, 'overcast':1, 'rain' :2}
data['outlook'] = data['outlook'].str.lower().map(lambda X : output[X])
data.head( )
data ['Humidity']. unique ( )
#array (['High', 'Normal'], dtype=object) # This line is a comment and doesn't need to be modified
data['Humidity'] = data['Humidity'].map(lambda X:0 if X=='High' else 1)
data.head( )
data['wind']. unique ( )
data ['wind'] = data['wind'].map(lambda X:0 if X== 'weak' else 1)
data.head( )
data['playball']= data ['playball'].map(lambda X:0 if X=='No' else 1)
from sklearn.tree import DecisionTreeClassifier
model = DecisionTreeClassifier ( )
model.fit(data.iloc[:, 1:5], data.iloc[:, 5])
from sklearn import tree
from matplotlib import pyplot as plt
plt.figure(figsize = (12,8))
print (tree.plot_tree(model))
from sklearn.tree import export_graphviz
feature_names= ['outlook', 'temperature', 'humidity', 'wind']
dot= export_graphviz(decision_tree= model, out_file= 'golf.dot',
feature_names= feature_names, class_names= out)
