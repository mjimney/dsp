[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

The CDF line is very close to being a diaginal line so the distribution is roughly uniform.  The pmf is an issue because all values have roughly the same probability due to the high level of decimals, but you cannot tell how evenly distributed the values are.

Code

from collections import defaultdict
import pandas as pd

rand_nums = np.random.random(1000)
rand_nums = np.sort(rand_nums)


pmf = defaultdict(int)

for num in rand_nums:
    pmf[num] += 1

n = sum(pmf.values())
pmf = {x:y/n for x,y in pmf.items()}

pmf_df = pd.DataFrame({'values':pmf})
pmf_df.plot.line()



cdf = pmf.copy()
for x in cdf:
    cdf[x] = EvalCdf(rand_nums,x)
cdf_df = pd.DataFrame({'values':cdf})
cdf_df.plot.line()


