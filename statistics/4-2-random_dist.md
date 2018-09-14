[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)  

>> #Exercise 4-2:  

	random_numbers = np.random.random(1000)     
	random_numbers_pmf = thinkstats2.Pmf(random_numbers)     
	random_numbers_pmf    
	random_numbers_cdf = thinkstats2.Cdf(random_numbers)   
	random_numbers_cdf   

Plot pmf:    	

	thinkplot.Pmf(random_numbers_pmf)   	

![Ex_4_2_random_plot_1](add link)   	

Plot cdf:   	
	
	thinkplot.Cdf(random_numbers_cdf)   	

![Ex_4_2_random_plot_cdf](add link) 


The cdf image shows straight line - yes the distribution is uniform.



