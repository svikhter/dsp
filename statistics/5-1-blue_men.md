[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

>> 
Chek values of mu (mean) and standard deviation (sigma)
'''
  mu
  sigma
''

We already know that mean = 178 and standard deviation = 7.7 (in cm)

  
    import scipy.stats
    normal_distribution_var = scipy.stats.norm(loc = mu, scale = sigma)
    
    #here we checked normal distribution:
    #loc is mean, scale is standard deviation
    
    normal_distribution_var
    
    #the result is returned in "standard random variable", which can confirm its mean and standard deviation
    
    normal_distribution_var.mean()
    #It is: 178
    normal_distribution_var.std()
    #It is: 7.7

    #Notes. This variable can also calculate its cdf, taking one positional argument
    #Here we checked cdf of a position (mean minus one standard deviation)
    #This returned a % of people that are at the point "one std deviation below the mean"
    #The result was: 16% (rounded)

    normal_distribution_var.cdf(mu-sigma)
    #Result: 0.15865525

  Remember the question was about people between 5'10'' and 6'11 tall. 
  Let's convert this into centimeters.
  
    #One inch is = 2.54 cm
    #Here is how I convert it:
    
    cm_5_10 =(5*12+10)*2.54
    cm_6_01 = (6*12+1)*2.54
    
    print(cm_5_10)
    # It is 177.8
    
    print(cm_6_01)
    # It is 185.42


    #The function will take the value in cm.
    
    
    cdf_5_10 = dist.cdf(cm_5_10)    # 5'10" =177.8
    cdf_6_01 = dist.cdf(cm_6_01)  #6'01'' = 185.42

    print (cdf_5_10, cdf_6_01, cdf_6_01 - cdf_5_10)
    #The result shows low, high, high minus low

The output:
(0.48963902786483265, 0.83173371081078573, 0.34209468294595308)
