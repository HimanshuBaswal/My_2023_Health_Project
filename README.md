
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
|Date (Steps)	| Date 	| Date | Dimension |
|Total Steps	|Whole Number	|Whole Number	|Measure |
|Distance (KM)	|Whole Number	|Whole Number |Measure |
|Duration (Mins)	|Whole Number	|Whole Number	|Measure|
|Duration (HH:MM:SS)	|DD-MM-YYYY HH:MM:SS	|DD-MM-YYYY HH:MM:SS	|Dimension|
|Calories	|Whole Number	|Whole Number	|Measure|
|Fat Burned	|Whole Number	|Whole Number	|Measure|
|Date (Sleep)	|Date 	|Date 	|Dimension|
|Light Sleep (Minutes)	|Whole Number	|Whole Number	|Measure|
|Deep Sleep (Minutes)	|Whole Number	|Whole Number	|Measure|
|Total Sleep (duration)	|Whole Number	|Whole Number	|Measure|
|Total Sleep (Time)	|DD-MM-YYYY HH:MM:SS	|DD-MM-YYYY HH:MM:SS	|Dimension|
|Sleep Score	|Whole Number|	Whole Number|	Measure|
|Date (HeartRate)	|Date 	|Date 	|Dimension|
|Average |Whole Number	|Whole Number	|Measure|
|Maximum |Whole Number	|Whole Number	|Measure|
|Minimum |Whole Number	|Whole Number	|Measure|
|Resting Heart Rate	|Whole Number	|Whole Number	|Measure|
|Date	|Date 	|Date 	|Dimension|
|Start_Time	|Text	|Text	|Dimension|
|Workout_Duration (mins)	|Text	|Whole Number	|Measure|
|Avg Heart Rate		|Text	|Whole Number	|Measure|
|Max Heart Rate		|Text	|Whole Number	|Measure|
|Calories		|Text	|Whole Number	|Measure|
|Relaxed_Duration (Mins)	|Text	|Whole Number	|Measure|
|Light_Duration (Mins)	|Text	|Whole Number	|Measure|
|Intensive_Duration (Mins)	|Text	|Whole Number	|Measure|
|Aerobic_Duration (Mins)	|Text	|Whole Number	|Measure|
|Anaerobic_Duration (Mins)	|Text	|Whole Number	|Measure|
|VO2 Max_Duration (Mins)	|Text	|Whole Number	|Measure|

This is what your fields in tableau will look like:

![3](https://github.com/HimanshuBaswal/My_Health_Project/assets/74957804/7def421d-afee-43e4-b30f-9f4589209cfc)
![2](https://github.com/HimanshuBaswal/My_Health_Project/assets/74957804/6107b550-ae0e-48e6-8681-978f7f45dbbc)

### _Key Metrics:_
- **Overall Health Score**: Comprising metrics like Intensity Balance Ratio, Workout Efficiency, and Wellness Hours.
	- High Intensity Balance Ratio - Ratio of time spent in Zone 2 and above heart rate zones during workout. Zones like Intensive, Aerobic, Anaerobic, VO2 MAX Zone. ![1](https://github.com/HimanshuBaswal/My_Health_Project/assets/74957804/996be3e4-114b-4c69-a037-2723a9c8327f)
 	- Workout Efficiency Ratio - Calories burnt per minute i.e., [Calories/Workout Duration (mins)]. ![2](https://github.com/HimanshuBaswal/My_Health_Project/assets/74957804/65fca793-21e5-4684-9655-858e36beb3fd)
	- Wellness Hours - Total time spent in wellness activities like Sleeping, Working out, Walking. ![3](https://github.com/HimanshuBaswal/My_Health_Project/assets/74957804/dd6f3353-728d-4c55-8148-381387506325)
 	- Overall Health Score - This is like the northstar metric for this project. It is basically a weight score formula that utilizes Step Score, Sleep Score, Heart Rate Score, and Workout Score. ![5](https://github.com/HimanshuBaswal/My_Health_Project/assets/74957804/87a0c95b-7c35-4250-bf17-ec704454ba97)
  	- Avg Day Text - A Text based calculated field to show what an average day looks like. ![10](https://github.com/HimanshuBaswal/My_Health_Project/assets/74957804/7f3779ef-acd4-45c0-8a28-900a36a59f06)
  	- Month Name - Deriving month name from Date. ![9](https://github.com/HimanshuBaswal/My_Health_Project/assets/74957804/76d0f66b-4c6a-4990-ba6c-d36266f0d7df)
  	- Weekday - Group of days counted as weekdays and others are basically weekend.
  	- 1steps average - A FIXED month view of the Total Steps with ROUNDED value.
  	- 2hours average - A FIXED month view of the Total Sleep time with ROUNDED value.
  	- 3calories average - A FIXED month view of the Total Calories Burned with ROUNDED value.
  	- Total Calories Burned - Summation of Calories burnt from Walking and from Workout. ![4](https://github.com/HimanshuBaswal/My_Health_Project/assets/74957804/a8e372d1-4735-419a-a8c5-a86e17dd9921)
	
- **Heart Rate Metrics**: Evaluating heart rate trends and resting heart rate levels.
	- Heart Rate Score - This score is based on the resting heart rate. ![Heart Rate Score](https://github.com/HimanshuBaswal/My_Health_Project/assets/74957804/0c3e8345-645a-4516-87f0-19887c5314e0)

- **Sleep Quality Metrics**: Including Weekend vs. Weekday sleep patterns and Sleep Score analysis.
	- Sleep Score - An Inbuild sleep score from the MI band 3 App.
  	- Total Hours Slept - Cumulative time spent sleeping (deep sleep + light sleep). It gives us overall sleeping time in Hours.  ![1](https://github.com/HimanshuBaswal/My_Health_Project/assets/74957804/506ea591-eba0-4ac2-a8c1-79af4668c03f)

- **Step Tracking Metrics**: Incorporating Streak and Step Score for monitoring progress.
	- Hours Walked - Duration of walking in hours. ![1](https://github.com/HimanshuBaswal/My_Health_Project/assets/74957804/debcc79c-014d-4238-bfbe-ec412ffff1f4)
  	- Step Score - A Metric devised by normalizing the daily step count with normalization function. (X - Xmin)/(Xmax - Xmin)![2](https://github.com/HimanshuBaswal/My_Health_Project/assets/74957804/50e359ef-8dfe-4fd0-b15f-197271baa372)
  	- Streak - Potential new visual 
	
- **Workout Performance Metrics**: Covering
  	- Workout Score - A Score derived from utilizing normalized workout score in percentage. ![4](https://github.com/HimanshuBaswal/My_Health_Project/assets/74957804/4b797e18-b78e-4519-a6c3-47d3e78d0f8b)
  	- Workout Norm - Normalized formula utilizing heart rate zone levels in minutes and assigning them with weighted score. ![3](https://github.com/HimanshuBaswal/My_Health_Project/assets/74957804/ce4f0ada-879e-4209-8d4a-d79af0356dd4)
	- High Intensity Balance Ratio - Ratio of time spent in high heart rate zone in workout.![1](https://github.com/HimanshuBaswal/My_Health_Project/assets/74957804/db6ac68a-e5eb-4207-ab46-dc9188ab3fe0)
 	- *Workout Metric Parameter* - This parameter will serve as a dynamic axis selection parameter in the visual, where I see how different parameters affect my workout score.![5](https://github.com/HimanshuBaswal/My_Health_Project/assets/74957804/7005f16e-7b0a-4bd5-8ae6-6091fc7f9d91)
  	- Workout Metric - This calculated field utilizes the *Workout Metric Parameter* to select between different fields.![6](https://github.com/HimanshuBaswal/My_Health_Project/assets/74957804/9a6129dd-7dd7-41e0-9edd-fc527097f1fa)


### _Approach:_
- **Overall Health Score Calculation**: Aggregating key metrics to derive an overall health score.
	- KPI's View
   		- High Intensity Balance Ratio - Decimal Number - The best way to show this would be like a KPI, it can be seen on Week, Month, and Quarter level.
     		- Workout Efficiency Ratio - Decimal Number - Number of calories burnt per min in workout duration. KPI view will be good.
       		- Wellness Hours - Time (Hours - Duration) - This is available for eachday whether there is workout data or not. KPI view is the right choice.
         	- Heart Rate Score - A Score - This is a Rating for the Resting Heart Rate. KPI view is the desired one, as there isn't much it heart rate.
         	- Overall Health Score - A Northstar Metric to check the Health Score it can be seen on Week, Month, and Quarter level. Prime KPI view .
	- Month Action Filter - Action Based Filtering system on the Month Field from the Date Column. Squared selection of each month for the user to view.
   	- Calendar View - This is a Custom Calendar view created to show the OHS or other metrics from the KPI View area.
   	- What does an Average day look like? - This is informing the viewer what an average day is like for me.
  
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

## Insights and Takeaways: (Post Completion)
### _Dashboard Highlights:_
- **Overall Health Score Trends**: Tracking improvements or declines in overall health metrics.
- **Steps and Sleep Patterns**: Identifying correlations between step count and sleep quality.
- **Workout Intensity Analysis**: Assessing the impact of workout duration and intensity on overall health.

## Conclusion:
Consideration of Scatter plot visualization showcasing Workout Duration vs. Parameters (Score, calories, Heart Rate levels) for deeper insights. Also, analyze variations in health metrics between weekends and weekdays.


[![N|Tableau](https://cdn.iconscout.com/icon/free/png-256/free-tableau-5376638-4489898.png?f=webp)](https://www.tableau.com/) [![N|Miro](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTxw8FakALOwikyJ6z2eIoYp3Cf7EPKpGRT6L4Pv15oaQ&s)](https://miro.com/index/)
