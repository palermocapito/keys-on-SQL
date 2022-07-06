# optimizationinventory
code under python
import pandas as pd
import numpy as np 
import matplotlib.pyplot as plt
import seaborn as sns
import scipy.stats as stats
d=[28,19,18,13,19,16,19,18,13,16,16,11,18,15,13,15,13,11,13,10,12]
def double_exp_smooth(d, extra_periods=1, alpha=0.4, beta=0.4):
    cols=len(d)
    d=np.append(d,[np.nan]*extra_periods)
    f,a,b=np.full((3,cols+extra_periods),np.nan)
    a=np.full((3,cols+extra_periods),np.nan)#
    b=np.full((3,cols+extra_periods),np.nan)#
    a[0]=d[0]
    b[0]=d[1]-d[0]
    f= np.full(21,0)
    for t in range(1,cols):
        gh[t-1]+b[t-1]
        a[t]=alpha*d[t]+(1-alpha)*(a[t-1]+b[t-1])
        b[t]=beta*(a[t]-a[t-1])+(1-beta)*b[t-1]
    for t in range(cols,cols+extra_periods):
        f[t]=a[t-1]+b[t-1]
        a[t]=gh[t]
        b[t]=b[t-1]
df=pd.DataFrame.from_dict({"Demand":d,"Forecast":f,"Level":a,"Trend":b,"Error":d-f})
return df
