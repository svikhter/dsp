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
                 
  ![image Added_Image_Ex_7_1_mother_age_baby_weight.png](/img/Added_Image_Ex_7_1_mother_age_baby_weight.png)               

