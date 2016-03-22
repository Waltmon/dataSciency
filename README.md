# summerSloth

(need to update)

Produces some fake data, representing projects done over a year (250 business days), and then does a simple analysis of it.

To produce the data, simulateData() goes through each business day, and first determines how many projects came in that day according to a probability (pdf_projInit) which is sligtly Gaussian to represent more coming in the summer time.  Then, for that day, it loops through each initiated project and determines how long that project will take to complete by choosing a random number, distributed in a semi-Gaussian (by adding 4 random numbers) around 15 days.  If "summer sloth" is allowed by the bool includeSummerSloth, it adds a kind of smear to the random number weighting, which is itself weighted in time to occur around summer time (with a Gaussian).  This effectively increases the time a project will take in the summer time, because people want to be outside instead. This is the effect which the analysis is supposed to reveal.  Revenue is determined as just a constant $1000 plus $100 x days taken.  When the 3 values for each project are determined, the project is loaded with loadProj() into a vector of the class Proj, belonging to the year Year, which is the data structure. 

outputAnalysis() loops through the vector of specified Year and bins the average time taken for projects within each time bin (of 10 days), and also determines the standard error in each bin.  I didn't write a plotter, I just have it output the analyzed data into a text file.  But I included a plot showing w/ and w/o "summer sloth" allowed, showing the effect which was determined by the analysis.

![Binned project completions w/ and w/o "summer sloth"](v3.png)
