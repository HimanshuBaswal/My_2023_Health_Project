
# My Health Project

## The Mission:
> To leverage health data collected over 6 months, starting January 2023 till late June 2023, and create an interactive dashboard/story for personal health insights.

## About the Project:
#### _Data Source:_
The project utilizes personal health data logged daily, covering steps, sleep patterns, heart rate, and workout sessions, tracked through the MI 3 band. The data spans from January 1, 2024, to June 27, 2024, capturing various aspects of health and well-being.

#### _Workbook Structure:_
| Sheet Name | Fields |
| ------ | ------ |
| Steps Data | Records Total Steps, Distance (KM), Duration, Calories, and Fat Burned.
| Sleep Data | Includes Light Sleep, Deep Sleep, Total Sleep Duration, and Sleep Score.
| Heart Rate Data | Contains Average, Maximum, Minimum, and Resting Heart Rate.
| Workout Data | Logs Workout Duration, Heart Rate Metrics, and Calories Burned.

#### _Tools Utilized:_
| Tool | Usage |
| ------ | ------ |
| Tableau | Employed for visualizing data and creating interactive dashboards |
| Miro | Used for dashboard layout planning, information architecture, metric selection, documentation & Notes. |
| Excel | Utilized for data management and preliminary analysis | 

#### _Link:_
[Link to the Tableau Data Viz](https://public.tableau.com/views/My2023HealthLogsStory/OHS?:language=en-US&:sid=&:display_count=n&:origin=viz_share_link)

## About the Dashboards :
The project comprises of four main dashboards:
- **Sleep Insights**: Focuses on sleep patterns and quality metrics.
	- The Sleep Tracking data focuses mainly on my sleeping behaviour. I utilized descriptive statistics to answer simple questions like *What is everyday average sleep like?, What does my sleep on weekends and weekends look like?, How does my sleep vary over the days?* and more such questions all with the use of graphs and visualization.

- **Steps Insights**: Displays daily step count and related statistics.
	- The Steps Tracking data focuses on analytics of my movement. I ask questions like *How much do I walk everyday?, What does that look like in hours?, When was my step score the best throughout the week?*, all of these through simply charts and KPI's.

- **Workout Analysis**: Highlights workout sessions, intensity levels, and calorie expenditure.
	- The Workout Data is a look at my workout stats. Fields like Workout duration, Heart Rate levels are used here. I ask questions like *What is avg workout duration?, What are my weekday and weekend workouts like?, How do my metrics change on weekend compared to weekday?*

- **Overall Health Score**: Provides an aggregated view of health metrics and trends.
	- This dashboard would be the main design which explains the Why? What? and How? of the dashboard. *A KPI view of all the created metrics, filter by month view, Calendar view, What does my average day look like.* This page would serve as a link to all others.

## Methodology:
### _Data Preparation:_

The Health Logs are recorded in an excel workout in a table format for each kind of log. Heart Rate, Sleep, Steps, and Workout are four different kind of health logs and they are entered in 4 different sheets. Each Sheet has a primary column that is basically the Date (DD-MM-YYYY) format. 

The final data is a **INNER JOIN** of Heart Rate, Sleep, Steps, and Workout data on the **Date** field. 
![1](https://github.com/HimanshuBaswal/My_Health_Project/assets/74957804/2103351e-be78-4ae0-8267-67fcff39a96b)

A look at all the Fields in the data:
| Field Name | Current Type | New Type | Classify |
| ------ | ------ | ------ | ------ |
|Date (Steps)	| Date 	|- | Dimension |
|Total Steps	|Whole Number	|- |Measure |
|Distance (KM)	|Whole Number	|- |Measure |
|Duration (Mins)	|Whole Number	|- |Measure|
|Duration (HH:MM:SS)	|DD-MM-YYYY HH:MM:SS	|- |Dimension|
|Calories	|Whole Number	|- |Measure|
|Fat Burned	|Whole Number	|- |Measure|
|Date (Sleep)	|Date 	|- |Dimension|
|Light Sleep (Minutes)	|Whole Number	|- |Measure|
|Deep Sleep (Minutes)	|Whole Number	|- |Measure|
|Total Sleep (duration)	|Whole Number	|- |Measure|
|Total Sleep (Time)	|DD-MM-YYYY HH:MM:SS	|- |Dimension|
|Sleep Score	|Whole Number|- |Measure|
|Date (HeartRate)	|Date 	|- |Dimension|
|Average |Whole Number	|-	|Measure|
|Maximum |Whole Number	|-	|Measure|
|Minimum |Whole Number	|-	|Measure|
|Resting Heart Rate	|Whole Number	|-	|Measure|
|Date	|Date 	|- 	|Dimension|
|Start_Time	|Text	|-	|Dimension|
|Workout_Duration (mins)	|Text	|**Whole Number**|Measure|
|Avg Heart Rate		|Text	|**Whole Number**|Measure|
|Max Heart Rate		|Text	|**Whole Number**|Measure|
|Calories		|Text	|**Whole Number**|Measure|
|Relaxed_Duration (Mins)	|Text	|**Whole Number**|Measure|
|Light_Duration (Mins)	|Text	|**Whole Number**|Measure|
|Intensive_Duration (Mins)	|Text	|**Whole Number**|Measure|
|Aerobic_Duration (Mins)	|Text	|**Whole Number**|Measure|
|Anaerobic_Duration (Mins)	|Text	|**Whole Number**|Measure|
|VO2 Max_Duration (Mins)	|Text	|**Whole Number**|Measure|

This is what your fields in tableau will look like:

![2](https://github.com/HimanshuBaswal/My_Health_Project/assets/74957804/6107b550-ae0e-48e6-8681-978f7f45dbbc) 
![3](https://github.com/HimanshuBaswal/My_Health_Project/assets/74957804/7def421d-afee-43e4-b30f-9f4589209cfc)

### _Key Metrics:_
- **Overall Health Score**: Comprising metrics like Intensity Balance Ratio, Workout Efficiency, and Wellness Hours.
	- High Intensity Balance Ratio - Ratio of time spent in Zone 2 and above heart rate zones during workout. Zones like Intensive, Aerobic, Anaerobic, VO2 MAX Zone.
      	```sh
     	High Intensity Balance Ratio = ([Intensive Duration (Mins)] + [Aerobic Duration (Mins)] + [Anaerobic Duration (Mins)] + [VO2 Max Duration (Mins)])/[Workout Duration (mins)]
     	```
 
	- Workout Efficiency Ratio - Calories burnt per minute i.e., [Calories/Workout Duration (mins)].
     	```sh
     	Workout Efficiency Ratio = ([Calories(Workout)]/[Workout Duration (mins)])
     	```
 
	- Wellness Hours - Total time spent in wellness activities like Sleeping, Working out, Walking.
     	```sh
     	Wellness Hours = [Total Sleep (duration)] + [Duration (Mins)] + [Workout Duration (mins)])/60
     	```
      
	- Overall Health Score - This is like the northstar metric for this project. It is basically a weight score formula that utilizes Step Score, Sleep Score, Heart Rate Score, and Workout Score.
     	```sh
     	Overall Health Score = ((ZN([Step Score)*0.2) + (ZN([Sleep Score)*0.35) + (ZN([Heart Rate Score)*0.15) + (ZN([Workout Score)*0.3))/1
     	```     
   
	- Month Name - Deriving month name from Date.
     	```sh
     	Month = DATENAME('Month',[Date])
     	```
   
   	- Weekday - Group of days counted as weekdays and others are basically weekend.
     	```sh
     	Weekday = DATENAME('weekday',[Date])
     	```
   
   	- 1steps average - A FIXED month view of the Total Steps with ROUNDED value.
        ```sh
     	1steps average = ROUND({ FIXED DATETRUNC("month", [Date]): AVG([Total Steps]) },0)
     	```
   
	- 2hours average - A FIXED month view of the Total Sleep time with ROUNDED value.
     	```sh
     	2hours average = ROUND({ FIXED DATETRUNC("month", [Date]): AVG([Total Sleep (duration)]) },0)
     	```   
   
   	- 3calories average - A FIXED month view of the Total Calories Burned with ROUNDED value.
     	```sh
     	3calories average = ROUND({ FIXED DATETRUNC("month", [Date]): AVG([Calories]) },0)
     	```
     
	- Total Calories Burned - Summation of Calories burnt from Walking and from Workout.
     	```sh
     	Total Calories Burned = ZN([Calories])+ZN([Calories(Workout)])
     	```   

  	- Avg Day Text - A Text based calculated field to show what an average day looks like.
     	```sh
     	Avg Day Text = "On average in " + STR([Month Name]) + " I walked " + STR([1Steps Average]) + " steps, slept " + STR([2Hours Average]) + " hours, and burnt " + STR([3Calories Average]) + " calories per day"
     	```      
	
- **Heart Rate Metrics**: Evaluating heart rate trends and resting heart rate levels.
	- Heart Rate Score - This score is based on the resting heart rate.
     	```sh
     	Heart Rate Score = IF [Resting Heart Rate] >= 49 AND [Resting Heart Rate] <= 55 THEN 100
			   	ELSEIF [Resting Heart Rate] >= 56 AND [Resting Heart Rate] <= 61 THEN 90
			  	ELSEIF [Resting Heart Rate] >= 62 AND [Resting Heart Rate] <= 65 THEN 80
			  	ELSEIF [Resting Heart Rate] >= 66 AND [Resting Heart Rate] <= 69 THEN 70
				ELSEIF [Resting Heart Rate] >= 70 AND [Resting Heart Rate] <= 73 THEN 60
			   	ELSEIF [Resting Heart Rate] >= 74 AND [Resting Heart Rate] <= 81 THEN 50
			 	ELSEIF [Resting Heart Rate] >= 82 THEN 40
			        END
     	```
      ![Resting-Heart-Rate-RHR-chart-1-946x1024](https://github.com/HimanshuBaswal/My_Health_Project/assets/74957804/5475717b-c9d5-48da-9c49-d1a11481904e)


- **Sleep Quality Metrics**: Including Weekend vs. Weekday sleep patterns and Sleep Score analysis.
	- Sleep Score - An Inbuild sleep score from the MI band 3 App.

  	- Total Hours Slept - Cumulative time spent sleeping (deep sleep + light sleep). It gives us overall sleeping time in Hours.
     	```sh
     	Total Hours Slept = [Total Sleep (duration)]/60
     	```

- **Step Tracking Metrics**: Incorporating Streak and Step Score for monitoring progress.
	- Hours Walked - Duration of walking in hours.
     	```sh
     	Hours Walked = [Duration (Mins)]/60
     	```
    
  	- Step Score - A Metric devised by normalizing the daily step count with normalization function. (X - Xmin)/(Xmax - Xmin)
     	```sh
     	Step Score = (([Total Steps] - 2997)/(20475-2997))
     	```
   
  	- Streak - Potential new visual 
	
- **Workout Performance Metrics**: Covering
  	- Workout Score - A Score derived from utilizing normalized workout score in percentage.
     	```sh
     	Workout Score = ([Workout Norm]/2447.76)*100
     	```
  
  	- Workout Norm - Normalized formula utilizing heart rate zone levels in minutes and assigning them with weighted score.
     	```sh
     	Workout Norm = (([Relaxed Duration (Mins)]*5) + ([Light Duration (Mins)]*10) + ([Intensive Duration (Mins)]*15) + ([Aerobic Duration (Mins)]*20) + ([Anaerobic Duration (Mins)]*23) + ([VO2 Max Duration (Mins)]*27))
     	```
   
	- High Intensity Balance Ratio - Ratio of time spent in high heart rate zone in workout.
     	```sh
     	High Intensity Balance Ratio = ([Intensive Duration (Mins)]+[Aerobic Duration (Mins)]+[Anaerobic Duration (Mins)]+[VO2 Max Duration (Mins)])/[Workout Duration (mins)]
     	```
   
 	- *Workout Metric Parameter* - This parameter will serve as a dynamic axis selection parameter in the visual, where I see how different parameters affect my workout score.![5]
     	```sh
     	Name = Workout Metric
        Data type = String
        Current Value = Workout Duration
     	```
   
  	- Workout Metric - This calculated field utilizes the *Workout Metric Parameter* to select between different fields.
     	```sh
     	Workout Metric = CASE [Parameters].[Workout Metric]
  	   		WHEN 'Workout Duration' THEN [Workout Duration (mins)]
  	   		WHEN 'Max Heart Rate' THEN [Max Heart Rate]
  	   		WHEN 'Avg Heart Rate' THEN [Avg Heart Rate]
  	   		WHEN 'Calories (Workout)' THEN [Calories (Workout)]
  	   		WHEN 'Intensity Balance Ratio' THEN [High Intensity Balance Ratio]
  	   		WHEN 'Workout Efficiency Ratio' THEN [Workout Efficiency Ratio]
  	   		END
     	```

### _Approach:_
- **Overall Health Score Calculation**: Aggregating key metrics to derive an overall health score.
	- KPI's View
   		- High Intensity Balance Ratio - Decimal Number - The best way to show this would be like a KPI, it can be seen on Month level.
     		- Workout Efficiency Ratio - Decimal Number - Number of calories burnt per min in workout duration. KPI view will be good.
       		- Wellness Hours - Time (Hours - Duration) - This is available for eachday whether there is workout data or not. KPI view is the right choice. Unit as hours.
         	- Heart Rate Score - A Score - This is a Rating for the Resting Heart Rate. KPI view is the desired one.
         	- Overall Health Score - A Northstar Metric to check the Health Score, it can be filtered on Month detail.
	- Month Action Filter - Action Based Filtering system on the Month Field from the Date Column. Squared selection of each month for the user to view.
   	- Calendar View - This is a Custom Calendar view created to show the OHS or other metrics from the KPI View area in an heat map. Circle based on size of the OHS value to be shown with valued colours.
   	- What does an Average day look like? - This is informing the viewer what an average day is like for me in terms of steps, hours, and calories. (A statement will be the standard way to show it.)

- **Sleep Insights**: Analyzing sleep duration, quality, and patterns.
	- How much do I sleep on average everyday? - Card of number of minutes and hours I sleep everyday.
   	- How much of that is light sleep? - Card view of light sleep in hours
   	- How much of that is deep sleep? - Card view of deep sleep in hours
  	- What is my Best Sleep score? - Card view of best sleep score
  	- What is my Worst Sleep score? - Card view of worst sleep score 
  	- Weekends vs Weekday? -  Total Sleep, Deep Sleep, Light Sleep on Weekends vs Weekdays 
   	- How does my sleep score vary over different days of the week? - Sleep score over the weekdays in a line chart.
   	- Is there a correlation between the duration of deep sleep and the sleep score? - 2 Scatter plot for correlation between deep sleep and sleep score.
   	- How does the average duration of total sleep change over the course of a month? - Line Chart view of total sleep over course of a month. Month Filter!
  	- Month Action Filter - Action Based Filtering system on the Month Field from the Date Column. Squared selection of each month for the user to view.

- **Steps Tracker**: Monitoring daily step count and streaks.
	- How much do I walk on average everyday? - Card view of my average daily steps.
  	- How many kilometer's is that? - Card view of kilometer's walked everyday.
  	- How much time do I spent walking? - Card view of minutes spent walking a day.
  	- What does that time look like in hours? - Card view of hours spent walking a day.
  	- What amount of calories do I burn everyday? - Card view of the number of calories burned from walking in a day.
  	- What is my highest steps? - Card view of my highest steps in a day.
  	- What is my lowest steps? - Card view of my lowest steps in a day.
  	- How long was my biggest streak of hitting 12K steps? - Card view of Streak.
  	- On average, what day of the week was my step score the best? - Line Chart view of step score over course of a week.
  	- Month Action Filter - Action Based Filtering system on the Month Field from the Date Column. Squared selection of each month for the user to view.

- **Workout Analysis**: Assessing workout intensity, duration, and calorie burn.
  	- How many Calories did I burn on average everyday? - Card view of the number of Kcals burned.
  	- What is average workout duration? - Card view of the average workout duration in minutes.
  	- What is my Average and Maximum Heart Rate like? - Card view of my average and maximum heart rate during workout.
  	- What is my Best Workoutscore? - Card view of best workout score.
  	- What is my Worst Workoutscore? - Card view of worst workout score.
  	- What are my weekday and weekend workout like? - Bar Chart comparing the weekday and weekend workout based.
  	- How does my workout score change based on different parameters - Scatter plot of Workout Score vs other workout parameter.
  	- Month Action Filter - Action Based Filtering system on the Month Field from the Date Column. Squared selection of each month for the user to view.

## Insights:

### MAIN DASHBOARD
- **Overall Health Score (OHS)**
	-   **January Peak**: The average Overall Health Score (OHS) peaked at 62.2 in January. This is reflected in the calendar view, where the majority of days are represented by dark blue squares, indicating higher scores.
	-   **March Decline**: OHS saw a significant drop in March, averaging 46.5. This is corroborated by a more varied color representation in the calendar view, showing less consistency in high scores.
	-   **May Peak Day**: The highest OHS was recorded on May 21st, with a score of 83.5.

- **Workout Efficiency**
	-   **Lowest in January**: Workout efficiency was at its lowest in January, with an efficiency score of 5.4.
	-   **Highest in June**: The highest workout efficiency was observed in June, with a score of 6.2.

- **Heart Rate Score**
	-   **March Low**: The heart rate score was at its lowest in March, with a score of 66.9.
	-   **June High**: The highest heart rate score was recorded in June, reaching 80.4.

- **Intensity Balance Ratio (IB Ratio)**
	-   **February Minimum**: The IB Ratio reached its lowest point in February, with a value of 36.
	-   **April Maximum**: The highest IB Ratio was recorded in April, at 50.

- **Wellness Hours**
	-   **February Peak**: The maximum wellness hours were recorded in February, with a total of 13.5 hours.
	-   **March Low**: The lowest wellness hours were in March, totaling 10.4 hours.

- **Calendar View**
	-   **January Consistency**: January shows the most consistent OHS, with dark blue squares indicating stable, high scores throughout the month.
	-   **March Variability**: March demonstrates the least consistency, with an average OHS in the 40s and several outliers, indicating fluctuating health scores.

### STEPS DASHBOARD
**Steps**
1.  **Lowest Step Count**: The lowest step count recorded was in June, with only 2,997 steps.
2.  **Highest Step Count**: The highest step count was achieved in February, with a total of 20,475 steps.
3.  **Consistent Achievement in January**: In January, the target step count of 12,000 steps was met every day for all 31 days.
4.  **January Averages**:
	-   **Highest Average Step Count**: January saw the highest average step count, reaching 16,133 steps per day.
	-   **Highest Average Distance Walked**: The average distance walked in January was 10.97 kilometers per day.
	-   **Average Walking Time**: On average, 187.5 minutes were spent walking each day in January, equivalent to approximately 3.13 hours.
	-   **Calories Burnt**: An average of 414.1 calories was burnt daily while walking in January.
6.  **Step Count Variability**: January had an average difference of 3,739 steps between the highest and lowest daily counts, indicating a more consistent average step count compared to other months.
7.  **Consistent Step Score**: The step score in January consistently ranged between 74 and 78.

### SLEEP DASHBOARD
**Sleep Overall**
1.  **Average Daily Sleep**: Consistent average of 7.2 hours per day over the 6 months.
2.  **Deep Sleep**:
	-   **Low Deep Sleep in Q1**: January (0.83 hours), February (1.66 hours), and March (1.73 hours), leading to a Q1 average of 1.4 hours.
	-   **Higher Deep Sleep in Q2**: Average of 2.05 hours.
4.  **Light Sleep**: Consistently around 5.2 hours per day over the 6 months.
5.  **Sleep Score**:
	-   **Best**: 98 in June.
	-   **Worst**: 40 in January.
7.  **Total Sleep**:
	-   **Consistent Average**: 7.2 hours across the months.
	-   **Lowest**: 3.9 hours on January 8th.
	-   **Highest**: 10.9 hours on March 18th.

**Sleep Score Analysis**
1.  **Weekdays vs. Weekends**:
	-   **January, May, June**: Weekday sleep scores were at least 4 points higher than weekend scores.
	-   **February, March, April**: Weekday and weekend scores were almost similar, with weekdays slightly higher.

2.  **Average Sleep Score by Day of the Week**:
	-   **January**: Worst sleep scores for all days.
	-   **April**: Best sleep scores for all days.
	-   **Thursday**: Best day overall.
	-   **Sunday**: Worst day overall.

**Deep Sleep Analysis**
1.  **Weekdays vs. Weekends**:
	-   **Higher on Weekends**: February, March, April, June.
	-   **Higher on Weekdays**: January, May.

2.  **Deep Sleep by Day of the Week**:
	-   **Saturday**: Highest overall deep sleep.
	-   **Sunday**: Fluctuates the most - low in January, February, May, and June; high in March and April.
	-   **Monday**: Consistently low.

**Light Sleep Analysis**
1.  **Weekdays vs. Weekends**:
	-   **Higher on Weekends**: February, March, April, May, June.
	-   **Equal on Weekdays and Weekends**: January.

2.  **Light Sleep by Day of the Week**:
	-   **Sunday and Saturday**: Highest sleep scores.
	-   **January**: Highest overall average light sleep (395 mins).
	-   **April**: Least light sleep overall average (312 mins).
	-   **Monday**: Least light sleep overall average (304 mins).
	-   **Saturday**: Highest light sleep (382 mins), followed by Sunday (360 mins) - only days with 6+ hours of light sleep on average.

**Total Sleep Analysis**
1.  **Weekdays vs. Weekends**:
	-   **Higher on Weekends**: February, March, April, May, June.
	-   **Equal on Weekdays and Weekends**: January.

2.  **Total Sleep by Day of the Week**:
	-   **Highest Average Total Sleep Time**: January, April, June.
	-   **Lowest Average Total Sleep Time**: May, March.
	-   **Saturday in March**: Highest total sleep time (10.3 hours on average).
	-   **Monday in March**: Lowest total sleep time (5.6 hours on average).
	-   **Saturday**: Highest total sleep time overall (10.3 hours on average).
	-   **Monday**: Lowest total sleep time overall (5.4 hours on average).

**Workout Analysis**

1.  **Average Calories Burned:**
	-   **February**: On average, I burned 671 calories.
	-   **June**: Average calorie burn was 597 calories.

2.  **Average Heart Rate:**
	-   **June**: Peaked at an average of 121 bpm.

3.  **Maximum Heart Rate:**
	-   **May**: Peaked at an average of 181 bpm.

4.  **Average Workout Duration:**
	-   **January**: Average workout duration was 114 minutes.

5.  **Best Workout Score:**
	-   **May** **21st**: Achieved a score of 99.98.

6.  **Worst Workout Score:**
	-   **June** **19th**: Score dropped to 30.16.

**Workout Score vs Parameters:**

1.  **Workout Duration vs. Weekday/Weekend:**
	-   Weekends: Higher workout duration compared to weekdays.

2.  **Workout Duration vs. Workout Score:**
	-   Correlation: Positive correlation between workout duration and average workout score.

3.  **Max Heart Rate vs. Weekday/Weekend:**
	-   Observation: Similar maximum heart rate on weekends and weekdays.

4.  **Max Heart Rate vs. Workout Score:**
	-   Correlation: No significant correlation between workout score and maximum heart rate.

5.  **Average Heart Rate vs. Weekday/Weekend:**
	-   Weekdays: Slightly higher average heart rate compared to weekends.

6.  **Average Heart Rate vs. Workout Score:**
	-   Correlation: No significant correlation between workout score and average heart rate.

7.  **Calories Burned (Workout) vs. Weekday/Weekend:**
	-   Weekends: Burned 20% more calories compared to weekdays.

8.  **Calories Burned (Workout) vs. Workout Score:**
	-   Correlation: Positive correlation between calories burned and workout score.

9.  **High Intensity Balance (HIB) Ratio vs. Weekday/Weekend:**
	-   Weekdays: Spent 46% of workout duration in high-intensity compared to 39% on weekends.

10. **HIB Ratio vs. Workout Score:**
    	-   Correlation: Higher HIB ratio is associated with a better workout score.

11.  **Workout Efficiency vs. Weekday/Weekend:**
	-   Weekdays: Average workout efficiency of 5.8, slightly higher than weekends (5.44).

12.  **Workout Efficiency vs. Workout Score:**
	-   Correlation: Positive correlation between workout efficiency and workout score.


## Conclusion:
The project successfully harnessed personal health data to provide actionable insights. Regular monitoring and visualization of health metrics fostered a deeper understanding of personal well-being, encouraging healthier habits and informed lifestyle choices. The Insights gained gives me a deep understanding about what works when it comes to health, what kind of sleep is better for health, how to remain consistent with chasing a walking goal, and what kind of heart rate zone is good for optimal fat burning and longevity.

[Link to the Tableau Data Viz](https://public.tableau.com/views/My2023HealthLogsStory/OHS?:language=en-US&:sid=&:display_count=n&:origin=viz_share_link)

[![N|Tableau](https://cdn.iconscout.com/icon/free/png-256/free-tableau-5376638-4489898.png?f=webp)](https://www.tableau.com/) [![N|Miro](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTxw8FakALOwikyJ6z2eIoYp3Cf7EPKpGRT6L4Pv15oaQ&s)](https://miro.com/index/)
