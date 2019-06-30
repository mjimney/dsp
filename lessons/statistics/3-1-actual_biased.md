[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

Actual Mean = 1.024205155043831
Biased Mean = 2.403679100664282


Code
resp = nsfg.ReadFemResp()

actual_dist = {x:y for x,y in resp['numkdhh'].value_counts().items()}
total_n_a = sum(actual_dist.values())
actual_dist_norm = {x:y/total_n_a for x, y in actual_dist.items()}
actual_mean = sum([x * y for x, y in actual_dist_norm.items()])
actual_mean

bias_dist = {x:x*y for x,y in resp['numkdhh'].value_counts().items()}
total_n_b = sum(bias_dist.values())
bias_dist_norm = {x:y/total_n_b for x, y in bias_dist.items()}
bias_mean = sum([x * y for x, y in bias_dist_norm.items()])
bias_mean

import pandas as pd
df = pd.DataFrame({'Actual':actual_dist,'Biased':bias_dist})
df.plot.bar()

