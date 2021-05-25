# Bar-Chart-Race

`Bar chart races` have been around for a while and they took social media by storm. It began with Matt Navarra’s tweet, which was viewed 10 million times. 
Bar chart race is a useful way to display time series in a bar chart format via animation and it helps you visualize the change in trends over time, these type of charts are very popular on social media as they provide a holistic data story/insight in a concise and easy to understand chart. 

There are various tools to create this Animated Chart but I wanted to try this in `Python`. 

### Demo 

![Covid-19-Cases-in-India](https://github.com/asthasharma98/Bar-Chart-Race/blob/main/Readme-Resources/covid-19_cases_in_india.gif)


***How to create a bar chart race animation with bar-chart-race library in Python ?***

### Installation

 Use the command given below to install bar_chart_race.
 
 ```
 pip install bar_chart_race
 ```
 **OR**
 
 ```
 conda install -c conda-forge bar_chart_race
 ```
 
### Structure of Data Frame 

For creating the Bar chart race we need to Re-arrange the data frame into a specific format where -
- Every row represents a single period of time
- Each column holds the value for a particular category
- The index contains the time component (optional)

The data below is an example of properly formatted data. It shows total Number of confirmed cases from COVID-19 for several States by date in India.

![Dataframe](https://github.com/asthasharma98/Bar-Chart-Race/blob/main/Readme-Resources/Dataframe.PNG)


### Main Function - bar_chart_race()

Below is the main code to create a chart using the `bar_chart_race()`. All parameters are shown with their default value except for `filename` and `title` and `cmap`. 

```
import bar_chart_race as bcr
df = covid_df_by_date
bcr.bar_chart_race(
    df=df,
    filename='covid-19-confirmed-cases-india.mp4',
    orientation='h',
    sort='desc',
    n_bars=10,
    fixed_order=False,
    fixed_max=True,
    steps_per_period=10,
    interpolate_period=False,
    label_bars=True,
    bar_size=.95,
    period_label={'x': .99, 'y': .25, 'ha': 'right', 'va': 'center'},
    period_fmt='%B %d, %Y',
    period_summary_func=lambda v, r: {'x': .99, 'y': .18,
                                      's': f'Total Confirmed Cases: {v.nlargest(6).sum():,.0f}',
                                      'ha': 'right', 'size': 8, 'family': 'Courier New'},
    period_length=500,
    figsize=(5, 3),
    dpi=144,
    cmap='set2',
    title='COVID-19 Rise of Confirmed Cases in India',
    title_size='10',
    bar_label_size=7,
    tick_label_size=7,
    shared_fontdict={'family' : 'Helvetica', 'color' : '.1'},
    scale='linear',
    writer=None,
    fig=None,
    bar_kwargs={'alpha': .7},
    filter_column_colors=False)  

```

*To get the Animation as HTML set the `Filename` Parameter as `None`. If you are running a Jupyter Notebook, it will automatically be embedded into it.*

```
bcr.bar_chart_race(df=df, filename=None)
```

Note : If you also want to try out this Animated bar chart race but don't want to code or want to try out using some different tools, you can try out with [Flourish Studio](https://flourish.studio/).



