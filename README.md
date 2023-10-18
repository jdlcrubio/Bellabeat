<h1> Bellabeat Case Study</h1>

<h2> Introduction</h2>
As the final challenge of the Google Data Analytics Certificate, I was asked to complete a case study. There was two datasets I could choose from to carry out my analysis. One of the datasets contained data from 30 FitBit users, which is the dataset which I chose. The dataset contained different types of data like sleep, heart rate, and different measures of activity. I had to put myself in the shoes of a data analyst that worked for Bellabeat. Bellabeat is company that offers devices that track actvitiy, sleep, stress, and even menstrual cycle. My task was to analyze the data to identify trends and behaviors. I then had to use these trends and behaviors to drive market strategies for one of the Bellabeat products.
  
<h2> Data Manipulation and Analysis Using R</h2>

````##loading readr to be able to read a csv file
library(readr)
##loading and viewing our data after it was manipulated in Google Sheets
actslp <- read_csv("~/Downloads/activity_sleep_updated.csv")
View(actslp)
##taking samples of five from each user
##repeated the same steps for all 18 users
df <- actslp %>% filter(Id == "1503960366")
df1 <- df[sample(nrow(df), 5), ]

df2 <- actslp %>% filter(Id == "1927972279")
df3 <- df2[sample(nrow(df2), 5), ]
 
df2 <- actslp %>% filter(Id == "2026352035")
df4 <- df2[sample(nrow(df2), 5), ]

df2 <- actslp %>% filter(Id == "2347167796")
df5 <- df2[sample(nrow(df2), 5), ]
df5

df2 <- actslp %>% filter(Id == "3977333714")
df6 <- df2[sample(nrow(df2), 5), ]

df2 <- actslp %>% filter(Id == "4020332650")
df7 <- df2[sample(nrow(df2), 5), ] 

df2 <- actslp %>% filter(Id == "4319703577")
df8 <- df2[sample(nrow(df2), 5), ]
 
df2 <- actslp %>% filter(Id == "4388161847")
df9 <- df2[sample(nrow(df2), 5), ]

df2 <- actslp %>% filter(Id == "4445114986")
df10 <- df2[sample(nrow(df2), 5), ]

df2 <- actslp %>% filter(Id == "4558609924")
df11 <- df2[sample(nrow(df2), 5), ]

df2 <- actslp %>% filter(Id == "4702921684")
df12 <- df2[sample(nrow(df2), 5), ]

df2 <- actslp %>% filter(Id == "5553957443")
df13 <- df2[sample(nrow(df2), 5), ]

df2 <- actslp %>% filter(Id == "5577150313")
df14 <- df2[sample(nrow(df2), 5), ]

df2 <- actslp %>% filter(Id == "6117666160")
df15 <- df2[sample(nrow(df2), 5), ]

df2 <- actslp %>% filter(Id == "6962181067")
df16 <- df2[sample(nrow(df2), 5), ]

df2 <- actslp %>% filter(Id == "7086361926")
df17 <- df2[sample(nrow(df2), 5), ]

df2 <- actslp %>% filter(Id == "8378563200")
df18 <- df2[sample(nrow(df2), 5), ]

df2 <- actslp %>% filter(Id == "8792009665")
df19 <- df2[sample(nrow(df2), 5), ]
##appending each users' samples into one dataframe
dffff <- rbind(df1, df3, df4, df5, df6, df7, df8, df9, df10 ,df11, df12
               , df13, df14, df15, df16, df17, df18, df19)
##new dataframe containing 5 samples of each user
dffff
##loading tidyverse to carry out our analysis using scatter plots
library(tidyverse)
##created a scatter plot to illustrate LightActiveDistance vs TotalDistance
##positive correlation between light active distance and total distance
##in other words, the more light active distance the more total distance
ggplot(data = dffff) + geom_point(mapping = aes(x = LightActiveDistance, y = TotalDistance)) + 
  labs(title = "LightActiveDistance vs TotalDistance")
##created a scatter plot to illustrate LightActiveDistance vs SedentaryMinutes
##correlation between sedentary and light activite distance
ggplot(data = dffff) + geom_point(mapping = aes(x = LightActiveDistance, y = SedentaryMinutes)) +
  geom_smooth(method = "lm", aes(x = LightActiveDistance, y = SedentaryMinutes)) +
  labs(title = "LightActiveDistance vs SedentaryMinutes")
##finding the average of the TotalMinutesAsleep column
dffff %>% summarize(asleepmean = mean(TotalMinutesAsleep))
##creating a scatter plot to illustrate TotalMinutesAsleep vs TotalTimeInBed
ggplot(data = dffff) + geom_point(mapping = aes(x = TotalMinutesAsleep, y = TotalTimeInBed)) +
  labs(title = "TotalMinutesAsleep vs TotalTimeInBed") + 
  geom_smooth(method = "lm", aes(x = TotalMinutesAsleep, y = TotalTimeInBed)) +
  annotate("rect", xmin = 200, xmax = 600, ymin = 400, ymax = 600, alpha = .6) +
  annotate("text", x = 600, y = 3, label = "mean(TotalMinutesAsleep) = 408")
##creating a scatter plot for LightActiveDistance vs TotalSteps
library(ggplot2)
ggplot(data = dffff) + geom_point(mapping = aes(x = LightActiveDistance, y = TotalSteps)) +
  geom_smooth(method = "lm", aes(x = LightActiveDistance, y = TotalSteps)) +
  labs(title = "LightActiveDistance vs TotalSteps") 
##creating a sactter plot for LightActiveDistance vs Calories
ggplot(data = dffff) + geom_point(mapping = aes(x = TotalSteps, y = Calories)) +
 geom_smooth(method = "lm", aes(x = TotalSteps, y = Calories)) 
##calculating average total steps
dffff %>% summarize(stepsmean = mean(TotalSteps))
##finding the max number of steps taken by an individual in a day
dffff %>% summarize(stepsmax = max(TotalSteps))
7000 * 2
````

<h2> Visualizations in R</h2>

![AsleepvsTotal](https://github.com/jdlcrubio/Bellabeat/assets/147890371/324bb643-bfaa-4c9b-846e-3ec576098ade)

![LightvsSteps](https://github.com/jdlcrubio/Bellabeat/assets/147890371/9c3c93ac-27b1-47ab-b8dc-74dcab77b55e)

![LightvsSeden](https://github.com/jdlcrubio/Bellabeat/assets/147890371/f536cc44-5b56-406e-adcb-b4abf4ad0720)





