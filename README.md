
# RFM Class

### Using the aggregation made from fake transactions we will generate a typical RFM (Recency, Frequency, Monetary) score

#### There are several ways to create the score

- Quantile based discretization (Using pandas qcut)
- Kmeans clustering
- Manual bin discretization based on the distribution of the features

In this example (like one I used in one of my RFM projects) I use the 3 methods together and I take the mean to smooth the effect of each one. This can be useful when you have very skewed data or weird distributions.
In real data also a subset of your data can be a good choice, but as always, the business needs, the reason for the project, and the final goal.
In one of my previous project, I removed people that didn't take action for 6 months using a time period for RFM of 3 months.

### The Class will have in input

- The aggregation file
- format file

### The scores are creating using

- R = days since the last transaction at the end of each month
- F = Number of transactions in the time period
- M = Money spent in the time period (Revenue would be a better parameter)

### The Class will do in order

- Read the data
- Select the features necessary from the data frame aggregate and change name with raw_parameter
- Create score using pandas qcut function
- Create a score using manual bin function
- Create score using kmeans clustering function
- Merge all the score and generate the average scores
- Generate the segments

# Extra Plots

Visualize the segments is important for post analysis. Tableau (or similar) would be the best tool but if not possible these are 3 options.
