[Think Stats Chapter 7 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2008.html#toc70) (weight vs. age)

>> 

    import first 
    import nsfg  

    df_nfsg = nsfg.ReadFemResp()  

    live, firsts, others = first.MakeFrames()  
    live = live.dropna(subset=['agepreg', 'totalwgt_lb'])  
    
    mothers_ages = live.agepreg  
    baby_weights = live.totalwgt_lb  
    
    thinkplot.Scatter(mothers_ages, baby_weights)  
    thinkplot.Config(xlabel='Age',  
                 ylabel='Weight (lb)',  
                 axis=[10, 70, 0.1, 15],  
                 legend=False) . 
                 
  Here is the scatter plot of mother's age Vs baby weight:              
                 
  ![image Added_Image_Ex_7_1_mother_age_baby_weight.png](/img/Added_Image_Ex_7_1_mother_age_baby_weight.png)      
  
    #np.digitize returns the indices of the bins to which each value in input array belongs.
    
    bins = np.arange(10, 75, 5) #(start, stop, step)
    #result: array([10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60, 65, 70])
    
    indices = np.digitize(live.agepreg, bins)
    mothers_ages_groups = live.groupby(indices)
    
    #check number of records in each group:
    
    for i, age_group in mothers_ages_groups:
    print(i, len(age_group)) 
    
1 58
2 1852
3 2962
4 2336
5 1393
6 401
7 36

    age_group_means = []
    for i, age_group in mothers_ages_groups:
        age_group_means.append(age_group.agepreg.mean())

    print (age_group_means)  
    
 [14.217586206896554, 18.111484881209783, 22.389182984470924, 27.3206292808229, 32.03910983488937, 36.806284289276746, 41.058055555555555]
 
    #alternative way, without "append":
    age_group_means_2 = [age_group.agepreg.mean() for i, age_group in mothers_ages_groups]
    print ( age_group_means_2 )
    
 [14.217586206896554, 18.111484881209783, 22.389182984470924, 27.3206292808229, 32.03910983488937, 36.806284289276746, 41.058055555555555]
 
    #now find CDF of baby weights:
    #using Cdf in thinkstats2:
    
    baby_weights_cdfs=[]
    for i, age_group in mothers_ages_groups:
        
        baby_weights_cdfs.append(thinkstats2.Cdf(age_group.totalwgt_lb))
        
        #will now plot:
        
        for percent in [80, 60, 40, 20]: #[75, 50, 25]:
            weight = []
            for n in baby_weights_cdfs:
                
                weight.append(n.Percentile(percent))
                
            thinkplot.Plot(age_group_means, weight) 
            
            
  ![image_included_Added_Image_Ex_7_1_percentile.png](/img/Added_Image_Ex_7_1_percentile.png)          
    
    
