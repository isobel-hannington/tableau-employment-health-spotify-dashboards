# 📊 Tableau dashboards: GB jobs, global health and Spotify

**Three interactive dashboards on Tableau Public, each answering one question from a different dataset.**

From Week 2 of my bootcamp. GB Employment asks which industries and cities gained jobs between 2011 and 2014. Global Health Insights shows a health organisation how life expectancy and BMI vary by continent and country. For Spotify, an open brief, I asked what separates popular tracks from unpopular ones.

## 🔎 At a glance

| | |
|---|---|
| **Tools** | Tableau Desktop Public Edition and Tableau Public |
| **Charts** | Bar charts, a line chart, a pie chart, scatter plots, a map, treemaps and headline figures |
| **Datasets** | EMSI job change data for 16 city areas in Great Britain (2011 and 2014); Gapminder health data (158 countries, 1990 to 2008); Spotify audio features (176,774 unique tracks), all supplied by Leep Talent |
| **Bootcamp week** | Week 2, Days 1 and 2 (September 2026), Level 3 Data Technician Skills Bootcamp, Leep Talent |
| **Type** | Individual work on training datasets |
| **Live dashboards** | [GB Employment Data](https://public.tableau.com/app/profile/isobel.hannington/viz/GBEmploymentData_17900040228790/GBEmploymentData) · [Global Health Insights](https://public.tableau.com/app/profile/isobel.hannington/viz/GlobalHealthInsights_17900762145110/GlobalHealthInsights) · [What makes a song popular on Spotify?](https://public.tableau.com/app/profile/isobel.hannington/viz/Week2SpotifyData/WhatmakesasongpopularonSpotify) |

## 💡 Skills demonstrated

**✔️ Calculated fields**
- Popularity tiers and the share of hits with `COUNTD` (Spotify)
- Each city's growth as total change divided by 2011 jobs (GB Employment)

**✔️ Interactive dashboards**
- Dropdown filters (Global Health, Spotify), plus Top N and range filters
- Filter actions, so clicking a city or an industry filters the rest of the dashboard (GB Employment)

**✔️ Choosing the right chart**
- Bar charts to compare, a line chart for change over time, a pie chart for a two-way split, scatter plots for relationships, a map for places and treemaps for parts of a whole

**✔️ Preparing the data**
- A percentage-of-total table calculation
- A group to merge two spellings of one genre (Spotify)

**✔️ Telling the story**
- Turning an open brief into one clear question, with headline figures first and chart titles that ask the question each chart answers (Spotify)
- Writing findings for a non-technical reader (the NHS note below)

## 📗 Dashboards built

| Dashboard | What I built |
|---|---|
| GB Employment | Bar charts of job change and job totals by industry, a map of the 16 city areas and a treemap of sub-industries, all linked by filter actions |
| Global Health Insights | The brief's four charts: life expectancy by continent in 2008, the trend for the five countries with the highest average life expectancy, population by gender, and life expectancy against BMI by country. I added BMI by continent as my own choice. |
| Spotify | Three headline figures, then popularity by genre, the audio features of hits against low-popularity tracks, a treemap of moods and a scatter plot of each genre by energy and valence, with a genre dropdown |

```
Popularity Tier:
IF [popularity] >= 60 THEN "Hit"
ELSEIF [popularity] >= 30 THEN "Mid"
ELSE "Low"
END

% Hits:
COUNTD(IF [Popularity Tier] = "Hit" THEN [track_id] END) / COUNTD([track_id])
```

## 📈 Results

### 🏢 GB Employment

![GB Employment dashboard](images/gb-employment-dashboard.png)

- Across the 16 city areas, jobs rose by 443,276 (3.2%) between 2011 and 2014. The file covers these areas only, not the whole of Great Britain.
- Professional, scientific and technical activities added the most jobs (134,655), then administrative and support services (120,169) and real estate (65,387).
- London grew fastest (+8.7%), followed by Brighton (+4.4%) and Nottingham-Derby (+3.1%). Four areas lost jobs: Glasgow (-2.2%), Cardiff-Newport (-0.8%), Leeds-Bradford (-0.7%) and Newcastle-Sunderland (-0.3%).

### 🌍 Global Health Insights

![Global Health Insights dashboard](images/global-health-dashboard.png)

- In 2008, average life expectancy ranged from 77.42 years in Europe to 58.73 in Africa. Each country counts equally; the averages aren't weighted by population.
- Average BMI was highest in Oceania (28.76) and lowest in Africa (23.46).
- Australia's life expectancy rose from 77.0 in 1990 to 81.6 in 2008.
- For the NHS: track average BMI in the UK alongside life expectancy, compare it with the rest of Europe, and look at BMI against cholesterol.

### 🎵 What makes a song popular on Spotify?

![Spotify dashboard](images/spotify-dashboard.png) (https://public.tableau.com/app/profile/isobel.hannington/viz/Week2SpotifyData/WhatmakesasongpopularonSpotify) 

- 9.19% of tracks are hits (popularity 60+), and the average popularity score is 41.1.
- Hits are far less acoustic (0.23 against 0.56 for low-popularity tracks) and rarely instrumental (0.04 against 0.20), so polished, vocal-led production is the clearest difference.
- Pop, Rap and Rock are the most popular genres, and A Capella, Movie and Opera the least. Energy alone doesn't explain popularity: Ska is among the most energetic, upbeat genres yet ranks in the bottom six.

## 🎓 Key learning outcomes

- **Sum or average?** BMI has to be averaged. Summing it added 38 rows per country and pushed the axis to about 1,100.
- **Don't average percentages.** Averaging sub-industry growth rates let tiny sub-industries dominate (one in London went from 6 jobs to 535) and made Glasgow look as if it was growing when it lost jobs. Total change over total 2011 jobs gives the true rate.
- **Check what a filter hides.** A Top 10 filter on job growth leaves large employers that shrank, such as manufacturing, off the job-total charts, so their titles now say so.
- **Clean categories before grouping.** "Children's Music" was spelt with both a straight and a curly apostrophe, which would have split it across two bars.

## 🛠️ Tools and technologies

- **Tableau Desktop Public Edition:** building the three dashboards
- **Tableau Public:** publishing them online, at the links above

## 📁 Repository contents

| File | What it contains |
|---|---|
| `GB_Employment_Data.twbx` | The GB Employment dashboard as a packaged Tableau workbook |
| `Global_Health_Insights.twbx` | The Global Health Insights dashboard as a packaged Tableau workbook |
| `Spotify_Data.twbx` | The Spotify dashboard as a packaged Tableau workbook, with its data inside |
| `EMSI_JobChange_UK.xlsx` | The UK employment dataset behind the GB Employment dashboard |
| `GapminderHealth_Dataset.xlsx` | The Gapminder health dataset behind the Global Health Insights dashboard |
| `Data_Technician_Workbook_Week_2.docx` | The Leep Talent Week 2 workbook with my written answers (Days 1 and 2 cover this project) |
| [`images/`](images/) | Screenshots of the three dashboards |

Each `.twbx` file opens in Tableau Desktop or the free Tableau Public app.
