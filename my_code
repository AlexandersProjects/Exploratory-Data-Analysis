import pandas as pd 
import numpy as np 
import matplotlib.pyplot as plt 
import seaborn as sns


"""
1) Three df:
    df_meal
    df_center
    df_food
    
2) merge them

"""

# df_meal
df_meal = pd.read_csv('C:/Users/Blaschko/OneDrive/Dokumente/Personal/IT/matplotlib_Visualization/Foodsupplier data_04.05.2020/meal_info.csv') 
print("meal: \n",df_meal.head())

#print(df_meal.dtypes)
#print(df_meal.info())

# df_center
df_center = pd.read_csv('C:/Users/Blaschko/OneDrive/Dokumente/Personal/IT/matplotlib_Visualization/Foodsupplier data_04.05.2020/fulfilment_center_info.csv') 
print("center: \n",df_center.head())

# df_food
df_food = pd.read_csv('C:/Users/Blaschko/OneDrive/Dokumente/Personal/IT/matplotlib_Visualization/Foodsupplier data_04.05.2020/train.csv') 
print("food: \n", df_food.head())

# merge

df = pd.merge(df_food,df_center,on='center_id') 
df = pd.merge(df,df_meal,on='meal_id')

print("merge: \n", df.head())

"""
Bar Graph with matplotlib

Bar graphs are best used when we need to compare the quantity of categorical values within the same category.
"""
print("This is the index: \n", df.index)
# first making a pivot table
table = pd.pivot_table(data = df, index = "category", values = "num_orders",aggfunc = np.sum)

print("this is the table: \n", table)

# now making the bar graph:

plt.bar(table.index,table["num_orders"])

# Ticks
plt.xticks(rotation = 70)

# x labels
plt.xlabel("Food item")

# y labels
plt.ylabel("Quantity sold")

# title
plt.title("Most popular food")

# save the plot
plt.savefig("C:/Users/Blaschko/OneDrive/Dokumente/Personal/IT/matplotlib_Visualization/images_graphs/bar_chart_001.png",dpi=300,bbox_inches='tight')

# print
print(plt.show())


"""
Divide food item order by the number of unique meals it´s present in
"""

# dictionary for meals per food item
item_count = {}

for i in range(table.index.nunique()):
    item_count[table.index[i]] = table.num_orders[i]/df_meal[df_meal["category"]==table.index[i]].shape[0]



# bar plot
plt.bar([x for x in item_count.keys()],[x for x in item_count.values()],color="orange")

# plt.bar([x for x in item_count.keys()],[x for x in item_count.values()],color='orange')

plt.xticks(rotation = 70)
plt.xlabel("Food item")
plt.ylabel("Number of meals")
plt.title("Meals per food item")

plt.savefig("C:/Users/Blaschko/OneDrive/Dokumente/Personal/IT/matplotlib_Visualization/images_graphs/bar_chart_meals_per_food.png",dpi=300,bbox_inches='tight')
print(plt.show())

"""
Making a Pie chart
"""
"""
# dictionary for cuisine and its total orders

d_cuisine = {}

# total number of order

total = df["num_orders"].sum()

# find ratio of orders per cuisine
for i in range(df["cuisine"].nunique()):
    
    # cuisine 
    c = df ["cuisine"].unique()[i]
    
# number of orders for the cuisine

c_order = df[df["cuisine"]==c]["num_orders"].sum()

d_cuisine[c] = c_order/total


# plotting the pie chart

plt.pie([x*100 for x in d_cuisine.values()], labels = [x for x in d_cuisine.keys()],autopct= "%0.1f", explode=[0,0,0.1,0])

# label the plot

plt.title("Cuisine share %")
plt.savefig("C:/Users/Blaschko/OneDrive/Dokumente/Personal/IT/matplotlib_Visualization/images_graphs/pie_chart_cuisine_share.png",dpi=300,bbox_inches='tight')   

print(plt.show())

"""
# dictionary for cuisine and its total orders
d_cuisine = {}

# total number of order
total = df['num_orders'].sum()

# find ratio of orders per cuisine
for i in range(df['cuisine'].nunique()):

# cuisine
    c = df['cuisine'].unique()[i]

# num of orders for the cuisine
c_order = df[df['cuisine']==c]['num_orders'].sum()
d_cuisine[c] = c_order/total

#pie plot 
explode = (0, 0, 0.1, 0)
sizes =  (27.3, 14.1, 36.9, 21.6) # [x*100 for x in d_cuisine.values()]
pie_labels = ("Thai", "Continental", "Italian", "Indian") # [x for x in d_cuisine.keys()]

plt.pie(sizes, labels = pie_labels, autopct='%1.1f%%',explode = explode)

plt.axis('equal')
plt.tight_layout()


#label the plot 
plt.title('Cuisine share %') 
plt.savefig("C:/Users/Blaschko/OneDrive/Dokumente/Personal/IT/matplotlib_Visualization/images_graphs/pie_chart_cuisine_share.png",dpi=300,bbox_inches='tight') 
print(plt.show())

"""
# pie plot 
explode = (0, 0, 0.1, 0)
sizes = [x*100 for x in d_cuisine.values()]
labels = labels=[x for x in d_cuisine.keys()]

print("Sizes: \n", sizes, "Labels: \n")
plt.pie(sizes ,labels = labels, autopct='%1.1f%%',explode = explode, shadow = True, startangle = 90) 

plt.axis('equal')
plt.tight_layout()
"""



# BOX PLOT

#dictionary for base price per cuisine
c_price = {}
for i in df['cuisine'].unique():
    c_price[i] = df[df['cuisine']==i].base_price

#plotting boxplot 
plt.boxplot([x for x in c_price.values()],labels=[x for x in c_price.keys()]) 

#x and y-axis labels 
plt.xlabel('Cuisine') 
plt.ylabel('Price') 

#plot title 
plt.title('Analysing cuisine price') 

#save and display 
plt.savefig("C:/Users/Blaschko/OneDrive/Dokumente/Personal/IT/matplotlib_Visualization/images_graphs/box_cuisine_price.png",dpi=300,bbox_inches='tight') 
plt.show();

"""
Plotting an easy histogram to inspect the distribution of the data
"""
#plotting histogram 
plt.hist(df['base_price'],rwidth=0.9,alpha=0.3,color='blue',bins=15,edgecolor='red') 

#x and y-axis labels 
plt.xlabel('Base price range') 
plt.ylabel('Distinct order') 

#plot title 
plt.title('Inspecting price effect') 

#save and display the plot 
plt.savefig("C:/Users/Blaschko/OneDrive/Dokumente/Personal/IT/matplotlib_Visualization/images_graphs/inspecting_price effect_15.png",dpi=300,bbox_inches='tight') 
plt.show()

"""
Plotting a histogram with only 10 bins
"""
#plotting histogram 
plt.hist(df['base_price'],rwidth=0.9,alpha=0.3,color='yellow',bins=10,edgecolor='red') 

#x and y-axis labels 
plt.xlabel('Base price range') 
plt.ylabel('Distinct order') 

#plot title 
plt.title('Inspecting price effect') 

#save and display the plot 
plt.savefig("C:/Users/Blaschko/OneDrive/Dokumente/Personal/IT/matplotlib_Visualization/images_graphs/inspecting_price effect_10.png",dpi=300,bbox_inches='tight') 
plt.show()



"""
Plotting a histogram with 20 bins
"""
#plotting histogram 
plt.hist(df['base_price'],rwidth=0.9,alpha=0.3,color='red',bins=20,edgecolor='red') 

#x and y-axis labels 
plt.xlabel('Base price range') 
plt.ylabel('Distinct order') 

#plot title 
plt.title('Inspecting price effect') 

#save and display the plot 
plt.savefig("C:/Users/Blaschko/OneDrive/Dokumente/Personal/IT/matplotlib_Visualization/images_graphs/inspecting_price effect_20.png",dpi=300,bbox_inches='tight') 
plt.show()

"""
making lists for comparing monthly with weekly sales
"""

#new revenue column 
df['revenue'] = df.apply(lambda x: x.checkout_price*x.num_orders,axis=1) 

#print(df["revenue"].head())

#new month column 
df['month'] = df['week'].apply(lambda x: x//4) 

#list to store month-wise revenue 
month=[] 
month_order=[] 

for i in range(max(df['month'])):
    month.append(i) 
    month_order.append(df[df['month']==i].revenue.sum())

# print("Month: \n",month[1],"month order: \n", month_order[1])
    
# List to store weekly revenue

week = []
week_order = []

for i in range(max(df['week'])):
    week.append(i)
    week_order.append(df[df['week']==i].revenue.sum())
    
# print("Week: \n", week[1], "Week order: \n", week_order[1])

"""
Creating subplots and lineplots for comparison
"""

# plt.plot(week, week_order)


#subplots returns a Figure and an Axes object 
fig,ax=plt.subplots(nrows=1,ncols=2,figsize=(20,5)) 

#manipulating the first Axes 
ax[0].plot(week,week_order) 
ax[0].set_xlabel('Week') 
ax[0].set_ylabel('Revenue') 
ax[0].set_title('Weekly income') 

#manipulating the second Axes 
ax[1].plot(month,month_order) 
ax[1].set_xlabel('Month') 
ax[1].set_ylabel('Revenue') 
ax[1].set_title('Monthly income') 

#save and display the plot 
plt.savefig("C:/Users/Blaschko/OneDrive/Dokumente/Personal/IT/matplotlib_Visualization/images_graphs/first_subplot_scatter.png",dpi=300,bbox_inches='tight') 
plt.show()

"""
Analyzing center type with three subplots in one figure
"""
center_type_name = ['TYPE_A','TYPE_B','TYPE_C'] 

# Relationship between op aera and number of orders
op_table = pd.pivot_table(df,index = "op_area", values = "num_orders", aggfunc = np.sum)

# Relation between center type and op area
c_type = {}
for i in center_type_name:
    c_type[i] = df[df["center_type"]==i].op_area
    
# relation between center type and number of orders
center_table= pd.pivot_table(df,index = "center_type", values ="num_orders", aggfunc = np.sum)

# subplots
fig,ax = plt.subplots(nrows = 3,ncols = 1,figsize = (9,13)) 

# Scatter plot
ax[0].scatter(op_table.index,op_table["num_orders"], color ="purple")
ax[0].set_xlabel("Operation Area")
ax[0].set_ylabel("Number of orders")
ax[0].set_title("Does the operation area affect number of orders?")
ax[0].annotate("Optimum operation area of 4 km^2", xy=(4.2,1.1*10**7),xytext=(7,1.1*10**7),arrowprops=dict(facecolor= "black", shrink = 0.05), fontsize = 12)

# Box plot
ax[1].boxplot([x for x in c_type.values()], labels = [x for x in c_type.keys()])
ax[1].set_xlabel("Center type")
ax[1].set_ylabel("Operation area")
ax[1].set_title("Which center type had the optimum operation area?")

# Bar graph
ax[2].bar(center_table.index, center_table["num_orders"], alpha = 0.7, color = "orange", width = 0.5)
ax[2].set_xlabel("Center type")
ax[2].set_ylabel("Number of orders")
ax[2].set_title("Orders per Center type")

# Show figure
plt.tight_layout() 
plt.show()

# Save figure
plt.savefig("C:/Users/Blaschko/OneDrive/Dokumente/Personal/IT/matplotlib_Visualization/images_graphs/three_plots.png",dpi=300,bbox_inches='tight')
