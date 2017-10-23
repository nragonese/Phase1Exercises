### 16.2.4 Exercises

1) you get a failed to parse error message.

2) it allows you to pick a timezone. the default is your current timezone, which may not correspond to the data you're working with.

3)
  d1 - mdy(d1)
  d2 - ymd(d2)
  d3 - dmy(d3)
  d4 - mdy(d4)
  d5 - mdy(d5)
  
### 16.3.4 Exercises

1)
flights_dt %>%
  mutate(time = hour(dep_time)*60 +minute(dep_time),
         month = as.factor(month(dep_time))) %>%
  ggplot(aes(x = time, group = month, color = month)) +
  geom_freqpoly(binwidth = 100)

2)
flights_dt %>% 
  mutate(dep_time2 = sched_dep_time + dep_delay*60) %>%
  filter(dep_time2 != dep_time) %>%
  select(dep_time2, dep_time, sched_dep_time, dep_delay)
 
3) 
flights_dt %>%
  mutate(air_time2 = arr_time - dep_time, delta = air_time - air_time2) %>%
  filter(air_time2 != air_time) %>%
  select(origin,dest,air_time2,dep_time,arr_time,air_time, delta)
  
4)
flights_dt %>%
  mutate(sched_dep_hour = hour(sched_dep_time)) %>%
  group_by(sched_dep_hour) %>%
  summarise(dep_delay = mean(dep_delay)) %>%
  ggplot(aes(y = dep_delay, x = sched_dep_hour)) +
  geom_smooth()
  
5)
  
flights_dt %>%
  mutate(day = wday(sched_dep_time, label = TRUE)) %>%
  group_by(day) %>%
  summarise(dep_delay = mean(dep_delay)) %>%
  ggplot(aes(y = dep_delay, x = day)) +
  geom_point()
  
  Saturday has the lowest average departure delay.
  
6)
ggplot(diamonds, aes(x = carat)) + 
  geom_density()
  
Both have an abnormal distribution towards whole numbers, liekly due to human preference in scheduling/ diamond creation.

7)
flights_dt %>%
  mutate(early = dep_delay < 0,
         minute = minute(sched_dep_time) %% 10) %>%
  group_by(minute) %>%
  summarise(early = mean(early)) %>%
  ggplot(aes(x = minute, y = early)) +
  geom_point()


