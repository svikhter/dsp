[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased) 

*In this example we explore "class size paradox"*   
    First, I created the data frame:  
    
    resp = nsfg.ReadFemResp() 

In this case dataframe resp was created using predefined function ReadFemResp (function definition can be found in nsfg module)  

View data:    

    resp 
   

View column list: 

    resp.columns  

Column list: 

    list(resp)  

The result was column list as a list of strings

View data in the column:

    resp['numkdhh']

Create histogram:

    hist_num_kids = thinkstats2.Hist(resp.numkdhh, label='num_of_kids_in_hh')
    thinkplot.Hist(hist_num_kids)
    thinkplot.Config(xlabel='Number of kids', ylabel='Count')

![hist_num_kids](/include link here)  

    num_of_kids_pmf = thinkstats2.Pmf(resp.numkdhh, label='num_kids')
    num_of_kids_pmf

Result:
Pmf({0: 0.466178202276593, 1: 0.21405207379301322, 2: 0.19625801386889966, 3: 0.08713855815779145, 4: 0.025644380478869556, 5: 0.01072877142483318}) 

Pmf, the probability mass function, shows probabilities of 0 to 5 children, it's normalized -  adds up to 100% 

Now, move to the biased pmf:  
(as if we asked children): 

I created my own version of the function:  
For each num_of_kids, we multiply the probability by num of kids responding 

        def BiasedPmf(pmf, label):  
            new_pmf = pmf.Copy(label=label) 
            for x, p in pmf.Items(): 
                new_pmf.Mult(x, x) 
            new_pmf.Normalize() 
            return new_pmf


Run the function, pass two arguments: pmf = num_of_kids_pmf and  label = 'numkdhh'.

    KidsBiasedPmf = BiasedPmf(num_of_kids_pmf, 'numkdhh') 

Read values:

    KidsBiasedPmf 

Here is what I see:
Pmf({0: 0.0, 1: 0.4009803921568627, 2: 0.3676470588235294, 3: 0.16323529411764706, 4: 0.04803921568627451, 5: 0.020098039215686272}) . 

Now plot it:  

    biased_pmf = BiasedPmf(num_of_kids_pmf, label='numkdhh')
    thinkplot.PrePlot(2)
    thinkplot.Pmfs([num_of_kids_pmf, biased_pmf])
    thinkplot.Config(xlabel='Num of children', ylabel='PMF')

![ex_3_1_num_f_kids_vs_biased](add link)

Plot biased separately to view:  

    biased_pmf = BiasedPmf(num_of_kids_pmf, label='numkdhh')
    thinkplot.PrePlot(1)
    thinkplot.Pmfs([biased_pmf])
    thinkplot.Config(xlabel='Num of children', ylabel='PMF')

![ex_3_1_biased_pmf](add linkl)

Compute their means:  

    print('mean', num_of_kids_pmf.Mean())
    print(' biased mean', biased_pmf.Mean())
    
Here is what I see:

mean 1.024205155043831
 biased mean 1.9186274509803922



