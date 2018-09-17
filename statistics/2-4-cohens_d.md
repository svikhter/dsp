[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)


I created my own version of the function, with descriptive names of the variables.  


    def Coheneffectsize_SV(group1, group2):    
      diff_in_mean = group1.mean() - group2.mean()   
      size1, size2 = len(group1), len(group2)   
      variance1, variance2 = group1.var(), group2.var() 
      pooled_variance = (size1 * variance1 + size2 * variance2)/ (size1 + size2)  
      pooled_standard_deviation = np.sqrt(pooled_variance)  
      Cohen_d = diff_in_mean / pooled_standard_deviation  
      return Cohen_d
 
  
  
  
  
Then, I created dafa frames and series and used the above function:

    live_babies  = mydf[mydf['prgoutcome'] == 1]  
    first_babies = live_babies[live_babies['birthord'] == 1]  
    other_babies = live_babies[live_babies['birthord'] != 1]  

    mygroup1 = first_babies.totalwgt_lb  
    #(or could use this instead: forst_babies['totalwgt_lb'] )
    mygroup2 = other_babies.totalwgt_lb 

    d = Coheneffectsize_SV(mygroup1, mygroup2) 
  
The result:  
-0.088672927072602 

I compared it to pregnancy length:  

    d_preg_len = Coheneffectsize_SV(first_babies.prglngth, other_babies.prglngth)  
   
  Result:    
0.028879044654449883  

I checked mean, var and std:

    print ('first_babies.mean ' , first_babies.totalwgt_lb.mean())  
    print ('first_babies.var ' , first_babies.totalwgt_lb.var()) 
    print ('first_babies.std ' , first_babies.totalwgt_lb.std()) 
  
    print ('other_babies.mean ', other_babies.totalwgt_lb.mean())   
    print ('other_babies.var ' , other_babies.totalwgt_lb.var())   
    print ('other_babies.std ' , other_babies.totalwgt_lb.std())   

    first_babies.mean  7.201094430437772  
    first_babies.var  2.0180273009157768  
    first_babies.std  1.4205728777207374  
    other_babies.mean  7.325855614973262  
    other_babies.var  1.9437810258964572  
    other_babies.std  1.3941954762143138 

I also tried to plot the weights, but  I think there were too many different values, I probably should have grouped them:

    Hist_weight_firsts_1 = thinkstats2.Hist(first_babies.totalwgt_lb)  
    Hist_weight_other_2 =  thinkstats2.Hist(other_babies.totalwgt_lb)  
    thinkplot.PrePlot(2) 
    thinkplot.Hist(Hist_weight_firsts, align = 'left', width = 0.45)  
    thinkplot.Hist(Hist_weight_other, align = 'right', width = 0.45)  

![hist image](/img/Added_Image_Stats_2_4.png)

Cohen's D compares difference between groups to variability within groups.  
(diff between means) /  (pooled standard deviation)  
  
   
  Result is a negative value: -0.08 . 
  I researched what this means: I got "negative effect size", and in this case effect is decreasing the mean.  
   
