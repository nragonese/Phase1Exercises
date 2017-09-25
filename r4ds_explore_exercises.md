Exercise 3.2.4
1) nothing
2) 234 rows, 11 columns
3) f = front-wheel drive, r = rear wheel drive, 4 = 4wd
5) It's just a list of available car options

Exercise 3.2.4
1)	It should go outside aes()
2)	Categorical: manufacturer, model, trans, drv, fl, class
3)	It doesn’t run, there aren’t enough shapes for all in-between points
4)	It’s unique to both variables
5)	Controls the boarder thickness
6)	Nothing

Exercises 3.5.1
1)	It gives a separate graph for each value
2)	That combination of drive and cylinder didn’t exist in the data set
3)	Facets by either row or column
4)	Advantage is you can see everything at once, disadvantage is it makes comparison amongst the facet variables difficult
5)	Nrow shows the facets in N number of rows. Ncol, n number of columns. Facet grid determines it based on the unique combinations of the 2 variables
6)	So that you can see more of the graphs at once without scrolling

Exercises 3.6.1
1)	Line, boxplot, bar, point
2)	N/A
3)	Removes the legends on the side
4)	Shows the shadow of how far out the data points get
5)	No, just defines the mapping individually vs in the heading
6)	
ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + 
      geom_point() + 
     geom_smooth(se = FALSE)
ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + 
    geom_point() + 
    geom_smooth(se = FALSE, mapping = aes(group = drv))

ggplot(data = mpg, mapping = aes(x = displ, y = hwy, color = drv)) + 
    geom_point() + 
    geom_smooth(se = FALSE, mapping = aes(color = drv))

ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + 
    geom_point(mapping = aes(color = drv)) + 
    geom_smooth(se = FALSE )
ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + 
    geom_point(mapping = aes(color = drv)) + 
    geom_smooth(se = FALSE, mapping = aes(linetype = drv))
ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + 
geom_point(mapping = aes(color = drv, stroke = 2))

Exercises 3.7.1
1) Scatterplot with a mean, ggplot(data = diamonds) + 
stat_summary( mapping = aes(x = cut, y = depth)
2)bar makes the height equal the number of cases, col makes the heights represent values
3) blank, abline, hline, vline, text, point, jitter, segment, line, bar
4) mean, X and Y values

Exercises 3.8.1
1)	You can’t see all the data points, use jitter
2)	Height and width to adjust horizontal and vertical jitter
3)	Jitter shows each point as one, count increases the size with more points
4)	ggplot(data = mpg, mapping = aes(x = cty, y = hwy)) +  geom_boxplot()

Exercises 3.9.1
1) 
bar <- ggplot(data = diamonds) + 
  geom_bar(
    mapping = aes(x = cut, fill = cut), 
    show.legend = FALSE,
    width = 1
  ) + 
  theme(aspect.ratio = 1) +
  labs(x = NULL, y = NULL)

bar + coord_flip()
bar + coord_polar()

2) used for custom labels
3) map has actual proportions, quick map is approx. and better for smaller data
4) highway increases at a faster rate than city, with can be seen more easily with the 1:1 ratio of coord_fixed(). Geom_abline() gives out a summary of the plot

Exercises 4.4
1)	typo with the i
2)	ggplot(dota = mpg) +   geom_point(mapping = aes(x = displ, y = hwy)),
Exercise 5.2.4
1)
	1) 8,482
	2) 9,313
	3)139,504
	4)86,326
	5) 29
	6) 239
	7) 9,34
2) can be used to simplify boundaries for departure times 
3) 8,255 canceled flights
4) it assumes value is an integer

Exercises 5.3.1
1)	INA <- filter(flights,is.na(dep_time)) + arrange(INA,sched_dep_time)
2)	arrange(flights,desc(dep_delay)), arrange(flights,dep_delay)
3)	arrange(flights,hour,minute)
4)	long: PSE, SJU, BQN short: LGA,CLT

Exercises 5.4.1
2)  it will show up multiple times
3)filter for all on time flights
4)selects NAs by default

Exercises 5.5.2
1)	
hourmin <- transmute(flights,
+           dep_time,
+           hour = dep_time %/% 100,
+           minute = dep_time %% 100
+ )
transmute(hourmin,minpastmid = (hour*60)+minute)

2)	Dep – arrival doesn’t factor in 60 min per hour instead of 100
3)	Departure delay is in min dep time/ sched dep time is in HR:MM
4)	Not sure
5)	[1]  2  4  6  5  7  9  8 10 12 11
a.	First it adds the matrix with both, then only the 2nd matrixes number

Exercises 5.6.7

Exercises 7.3.4

Exercises 7.4.1
1)	Histogram they’re not included, bar chart they’re marked as 0s.
2)	Allows the functions to run by removing nulls
