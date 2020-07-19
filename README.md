# boxplot-code
1. mathmatical code for boxplot 2. graphical representation of boxplot

Boxplot is a method for graphically depicting numerical data based on a five-number summary (minimum, first quartile (Q1), median, third quartile (Q3), and maximum). 
Boxplot is widely used because it can tell about outliers and what their values are. The median value of the boxplot represents the median value of a certain feature. 
The first quartile represents the middle number between the smallest number (not the minimum number) and the median of a certain feature, the third quartile represents the middle number between the largest number (not the maximum number) and the median of a certain feature.
The range between the first quartile and third quartile is called the Interquartile range (IQR). The maximum value represents as (Q3 $ + $ 1.5 $ * $ IQR) and the Minimum value represents as (Q1 $ – $ 1.5 $ * $ IQR). 
Any number outside all these ranges is called outlier.

Here in boxplot.ipynb file,

boxplot function takes a list then returns the maximum and minimum numbers of the boxplot distribution of the list.
in boxplot funtion my code works as follows:
1. sort the given list
    sort_score_zero = sorted(dist_list)
2. find the index value of the "median"
    med1 = np.argwhere(sort_score_zero == np.percentile(sort_score_zero,50,interpolation='nearest'))
    med1 = med1[0][0]
    #print(med1)
3. then divide the list into two list
    firsthalf = sort_score_zero[0:med1+1]
    lasthalf = sort_score_zero[med1+1:]
    firsthalf = np.array(firsthalf)
    lasthalf = np.array(lasthalf)
4. find the "Q1"
    q1_index = np.argwhere(firsthalf == np.percentile(firsthalf,50,interpolation='nearest'))
    #print(q1_index)
    q1_index = q1_index[0][0]
    q1 = firsthalf[q1_index]
5. find the "Q3"
    q3_index = np.argwhere(lasthalf == np.percentile(lasthalf,50,interpolation='nearest'))
    q3_index = q3_index[0][0]
    q3 = lasthalf[q3_index]
6. find the "IQR", "maximum", "minimum"
    IQR = q3 - q1
    MaxT = q3 + 1.5 * IQR
    MinT = q1 - 1.5 * IQR
    
7. for boxplot diagram
    sns.boxplot(y=[25,29,3,32,85,33,27,28],palette = 'winter') #here sns is imported name of seaborn
